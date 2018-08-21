---
title: "Kossel XL 构建记 (34) ---- The Printer Calibration"
date: "2014-11-08 20:00:00"
tags: ["3DP", "Kossel", "GCode","G29","G30",Calibration]
draft: false
author: "tt4"
---

#### 简单人肉校正

忘了哪个人的博客里面曾经提到，Delta 系的打印机最重要的是对称，自认为我的这台 Kossel XL, 每个环节都力图精准，对称的问题应该不大。

简单调平可以这样做：

- 用皮尺测量一下 XYZ 三轴的限位器是不是一样高，尽量使得三个限位器在同一高度上。

- 首先看看 Z 轴的最大值是多少：G28 让打印机Home, 记住 LCD 上 Z 的取值, 我的是 258 (mm)，然后 G1 Z200, G1 Z100, G1 50, ... 直到喷头碰到玻璃板，限位器开关触发（可以用 M119 来检测限位器的状态，这里 z_min 应该 Triggered.） 再一次记下 Z 的值（这次是 11 mm）. 说明 Z-Max 应该是 258-11 = 247mm.

- 然后将打印头移到玻璃板上方 1~2 mm 处， 例如用： G1 Z12 或 G1 Z13. 然后前后左右移动打印头，用 G1 X10, X20, X30 ... G1 X-10， X-20,... G1 Y10, Y-10, .... 看看喷头是否会撞到玻璃板。

- 我这里的情况是四个方向都撞到了，说明打印头 X Y 方向不是水平的，而是一个向上凸的曲面。

如果是我这种情况，这个网站：[builda3dprinter][1]

#### 校正办法

- 中间向上凸的时候：增加 DELTA_RADIUS 的值以变平。增加的办法是 M666 R设定值（参考下文中表格）然后 M500 保存，M501 检查新值。根据我的经验，增加的量和边缘的 Z 高度成正比。作者用 DELTA_SMOOTH_ROD_OFFSET 的值也是等效的。
- 中间向下凸的时候：减少 DELTA_RADIUS 的值以变平。

人肉校正的结果是不错的！DELTA_RADIUS 设置为 146mm, Z_HEIGHT 设为 245mm。整体中心与最靠近三柱的 ABC 三点的高度差可以控制在 ± 1mm 之内！【更新：实际上我们可以手动调平到四周三点和中心点的误差不超过 0.3mm】

#### 打印件误差校正

- 可以打印一个 100x2x2 mm 的长方形，用 OpenSCAD 很容易实现（cube([100,2,2]) 即可）。然后打印出来，测量打印件的长度，修正 Diagonal_Rod 的长度：

测量值/100 * 原长度就是杆子的新长度。

#### 自动校正

我用的是 RichCattell 的 Marlin 固件。自动调平号称这个固件的强项。今天我们来谈谈 RichCattell 的自动校正设置。

这里的自动校正可以自动纠正如下设置：

- Delta Radius
- Delta Rod Length
- Software Endstop Offsets
- Z-Height correction
- Tower Position Error Correction (独立于半径和每个柱的径向位置调节)

上述这些变量都可以通过 M666 手动调节。

下面这些命令是这个版本新增的：

- G30: G30 会检测 指定点，或者默认情况下检测圆心以及圆周上点的 Z 高度，


  G30 Probe bed and produce a report of the current state of the printer, e.g.:

  Z-Tower Endstop Offsets -0.0125 X:-3.05 Y:-1.83 Z:-2.69 -0.0000 -0.0000

  Tower Position Adjust -0.0625 A:-0.04 B:0.05 C:-0.01 -0.0375 -0.0250 I:0.25 J:-1.25 K:-0.37 -0.0250
  Delta Radius: 109.5965
  X-Tower Y-Tower Diag Rod: 224.5935

  This option does not change any settings, but is useful when manually calibrating a printer, using the M666 command to change values.

  G30 Xnn Ynn Probe bed at specified X,Y point and show z-height and delta carriage positions, e.g.: Bed Z-Height at X:30.00 Y:30.00 = 0.0000 Carriage Positions: [176.40, 207.77, 209.52]

  G30 A 会开始自动校正所有参数，最好之前用 M502 导入默认值，M500 保存之，然后再 G30 A. 自动校正之后，用 M500 保存。


命令	| 意义		| 结果
--------|---------------|---------------
M666 L	| 列出当前设置	| M666 L
	|		| Current Delta geometry values:
	|		| X (Endstop Adj): -3.05
	|		| Y (Endstop Adj): -1.83
	|		| Z (Endstop Adj): -2.69
	|		| P (Z-Probe Offset): X0.00 Y10.00 Z-5.60
	|		| A (Tower A Position Correction): -0.04
	|		| B (Tower B Position Correction): 0.05
	|		| C (Tower C Position Correction): -0.02
	|		| I (Tower A Radius Correction): 0.25
	|		| J (Tower B Radius Correction): -1.25
	|		| K (Tower C Radius Correction): -0.37
	|		| R (Delta Radius): 109.60
	|		| D (Diagonal Rod Length): 224.59
	|		| H (Z-Height): 255.73
	|		|
M666 R200| 设置 delta radius 至 200mm |
M666 H350.0| 设置 Z-Height 为 350.0mm |
--------------------------------------

要设置那条命令，只需要加参数名：见上表，以及参数值（和参数名连在一起书写）即可。

所有参数值都可以通过 M501 从 EEPROM 中读取；或通过 M500 保存到 EEPROM 中。


```c++
#define Z_PROBE_DEPLOY_START_LOCATION {20, 96, 30, 0}
#define Z_PROBE_DEPLOY_END_LOCATION {5, 96, 30, 0}
#define Z_PROBE_RETRACT_START_LOCATION {49, 84, 20, 0}
#define Z_PROBE_RETRACT_END_LOCATION {49, 84, 1, 0}
```
Set precision for autocalibration G30 function – calibration will complete when this value is reached – all probed point have to be at 0 +/- 0.015mm (for 0.03 setting below)

```c++
#define AUTOCALIBRATION_PRECISION 0.03 // mm
```
Set distance to probe bed at for G30 function

```c++
#define BED_DIAMETER 170 // mm
```

[1]: http://www.builda3dprinter.eu/build-manuals/kossel_mini_build_manual/calibration-2/

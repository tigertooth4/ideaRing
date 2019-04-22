---
title: "Kossel XL 构建记 (31) ---- The G-Code Summary "
date: "2014-10-05 15:52:00"
tags: ["3DP", "Kossel", "GCode"]
draft: false
author: "tt4"
---
Title:
Date: 2014-10-05 15:52:00
Tag: 3dp, Kossel, GCode
Status: public

以下我来简单总结一下我需要用到的 G-Code，本文涉及的内容大部分来自 [RepRap:G-Code][1] 以及
[tontome.wordpress][2]

## 概览


字母 | 意义
-----|-----
Gnnn | 标准 G-Code 指令
Mnnn | Reprap 定义的指令
Tnnn | 通常是挤出头的代码
Xnnn | X 坐标移动，Y,Z 同理
Fnnn | 进料速度，以 mm/min 为单位
Ennn | 控制进入挤出机的线材的长度
Nnnn | 行码


## 延时发出的 G 指令

这些指令是逐条进入固件并执行的。固件中一般都设有一个缓存，用来存放未执行的代码。


命令    |  解释     |   例子
--------|-----------|----------
G0	|快速移动   | G0 X12 : 快速在 X 方向移动 12mm
G1	|可控移动   | G1 X10 Y5 E20 : 从当前点移动到 X=10, Y=5 的点，并挤出 20mm 的料丝; G1 F600 可以设置挤出速度为 600mm/min
G28     |移动至原点 | 向着限位开关的方向移动，知道碰触限位开关时停止；G28 X0 Y70 会忽略 Z 方向的复位，X, Y 的数值不起作用
G29     |细致的Z探测| G29 : 每个检查点的 Z 高度都测量 3 次
G30	|当前位置的 Z 探测| G30 : 只探测当前 X-Y 位置的 Z 高度
G31     |通报Z限位器是否已被触发| G31
G32	|用于 FPU 的Z探测|


## 即时执行的 G 指令

命令	| 解释		| 例子
--------|---------------|----------
G4	| 停顿		| G4 P200 停顿 200ms, 停顿过程中很多量仍可以被控制，如挤出头温度等
G21	| 设置以mm 为单位|
G90	| 设置成绝对位置|
G91	| 设置成相对位置|
G92	| 设置当前点为指定坐标|
M0	| 执行完缓冲区指令后立即停止并关机|
M1	| 执行完缓冲区指令后进入睡眠状态|
M17	| 步进电机加电	|
M18	| 步进电机断电	|
M20	| 列出 SD 卡 根目录的文件|
M21	| 初始化 SD 卡 |
M22	| 推出 SD 卡	|
M23	| 选定 SD 卡上的文件|
M24	| 开始、继续 SD 打印|
M25	| 暂停 SD 打印|
M27 	| 报告 SD 卡状态|

## 设定/读取

命令	| 解释		| 例子
--------|---------------|-----------
M92	| 设置 axis_steps_per_units | M92 X<new steps>
M104	| 设置挤出机温度, 然后立即将控制权转交给host| M104 S190 : 设置挤出机到 190°C
M105	| 读取挤出头和热床温度|
M106	| 风扇开	| M106 S190 : 将风扇转速设定在 0-255 之间
M107	| 风扇关	|
M109	| 设置挤出头温度，并等待升温到此温度|
M114	| 得到当前的位置| X Y Z 和挤出头 E 的位置
M119	| 返回限位开关状态|
M134	| 将 PID 值写入到 EEPROM|
M135	| 设置 PID 采样间隔 | M135 S300 （设置采样间隔为 300ms)
M136	| 打印 PID 设置到 host|
M140	| 设置热床温度，并立即交回控制权|
M190	| 等待热床到设定的温度| M190 S60
M201	| 设定打印最大加速度| M201 X1000 Y1000 Z100 E2000 （设置 X,Y, Z 和 E 的加速度 unit/second^2
M203	| 设定最大 Feedrate (mm/minute) | M203 X6000 Y6000 Z300 E10000
M207 	| 通过测量 Z 轴的最大活动范围来校准 Z 轴 | M207 (当把打印头移动到你认为的 Z=0 处时用这个命令，打印机会自动回位并记录 Z 轴移动的距离作为 Z_MAX)
M208	| 设置 X Y Z 轴的最大行程 | M208 X250 Y210 Z180 （Marlin 中可以通过 M500 命令把设置结果保存到 EEPROM 中）
M240	| 照相|
M301	| 手动设置 PID 的值| M301 P1 I2 D3
M303	| 自动PID调节| 设置加热头：M303 S<temperature> C<cycles> 设置热床： M303 E-1 C<cycles> S<temperature>
M304	| 设置热床 PID 的值| M304 P1 I2 D3
M500	| 保存设置到 EEPROM 中 | M500
M501	| 从 EEPROM 中读取设置| M501
M502	| 重置为出厂设置| M502 （还需要用 M500 保存）
M503	| 获取设置 | M503
M565	| 设置探针和加热头之间的偏移量| M565 X3 Y4.5 Z-2.37
M660	| 设置 delta 的参数| M660 L250 R160 S200  （L = diagonal rod length, R = delta radius, S = segments per second.）
M906	| 设置各步进电机的电流（毫安）| M906 X300 Y500 Z200 E350

## Marlin-RichCattell 的特殊设定
因为我用的是 RichCattell 版本的 Marlin (此版本对于自动标定有了加强)，这里有几个命令需要强调下：

命令	| 解释		| 例子
--------|---------------|------------
G30 	| 可以 G30 X?? Y??，这是标定特定的点，或者 G30 A 代表自动调平| G30 A 之后，探头将会标定圆周上的六个点以及圆心，得出各个 Tower 的限位开关的修正值，以及各个杆长的修正值等等。
G29 	| 传统的 7x7 网格调平，但是我不清楚其中的机理，调平后得到的数值是 Z 轴的高度，这些数值会直接被利用来补偿打印时的误差吗？ | G29 Z+0.3 让 Z 轴抬升 0.3mm










[1]: http://reprap.org/wiki/G-code/zh_cn
[2]: http://tontome.wordpress.com/2014/08/23/g-code-commands-supported-by-marlin/
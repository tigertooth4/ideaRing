---
title: "Kossel XL 构建记 (24) Electronic Box and First Marlin attempt"
date: "2014-09-11 09:20:00"
tags: ["3DP", "Kossel", "DIY","Marlin","Firmware"]
draft: false
author: "tt4"
---


画好的电路盒已经开始打印了，这个是正在打印的前面板：
![][image-1]
为了调整好开孔的位置还是颇为费时的。我打印了三版才搞定 :/

这是组装好的前面板：
![][image-2]
Kossel XL 赫然在目；）

熬夜组装前面板及防滚架：
![][image-3]
顺便等凌晨 1 点的水果新品发布会（结果视频直播状况频发: 首先是全世界都注意到的中国 lady 的同声传译；然后又遇到无数次的视频中断，甚至水果的官网都一度瘫痪了。。。）

跑题了，抱歉！上图中右侧的防滚架没有考虑到 LCD 面板后面的凸起，装不上。于是人工打磨了一下，开了几个槽 ;/ （懒得再画新的了，反正安慰自己在里面看不见。可见我是一个“看脸”的人...）

装好防滚架的前面板：
![][image-4]

----

前天看到这个网站，说明如何修改 Marlin 的参数 [http://www.hkepc.com/forum/viewthread.php?tid=2084008][1]。然后他推荐了一个 Marlin 的衍生版，由 RichCattell 编写。我看了眼，发现更新的比较频繁，有对自动调平的功能有了改进，于是决定采用，地址是：[https://github.com/RichCattell/Marlin/releases/tag/v1.04][2]

----
好了，现在就开始修改 Marlin 的参数了！在 Marlin 的目录中找到 Configuration.h 这个文件。 Marlin 的设置主要在 Configuration.h 和 Configuration_adv.h 中。

其实也没有多少要改的：主要涉及到 Delta 系打印机的几何参数，例如连杆长度等等。但是这些参数对于 Kossel 的打印质量影响很大，所以要仔细测量并更新 Configuration.h 。

```c++
// Center-to-center distance of the holes in the diagonal push rods.
 # define DEFAULT_DELTA_DIAGONAL_ROD 275.0 // mm
```
这是连杆从球头中心到球头中心的距离，卷尺测量了下，近 275 毫米。

```c++
// Horizontal offset from middle of printer to smooth rod center.
 #define DELTA_SMOOTH_ROD_OFFSET 214.8 //=372/sqrt(3) mm
```
这是从挤出头中心点到垂直铝框架中轴的距离。我是量了两个垂直铝框架中轴间的距离，除以√{3} 这样来算的。

```c++
// Horizontal offset of the universal joints on the end effector.
 #define DELTA_EFFECTOR_OFFSET 39  // mm
```
这是 Effector 中心到 effector 的球头连接头中心的距离。

```c++
// Horizontal offset of the universal joints on the carriages.
 #define DELTA_CARRIAGE_OFFSET 38 // mm
```
这是从垂直铝框架中轴，到滑车上的球头中心的距离。


```c++
// Diameter of print bed - this is used to set the distance that autocalibration probes the bed at.
 # define BED_DIAMETER 260 // mm
```
这是热床的直径，我用的近 260 毫米的大床;)


```c++
 // Z-Probe variables
 // Start and end location values are used to deploy/retract the probe (will move from start to end and back again)
 # define Z_PROBE_OFFSET {0, 10, -5.6, 0}  // X, Y, Z, E distance between hotend nozzle and deployed bed leveling probe.
 # define Z_PROBE_DEPLOY_START_LOCATION {20, 96, 30, 0}   // X, Y, Z, E start location for z-probe deployment sequence
 # define Z_PROBE_DEPLOY_END_LOCATION {5, 96, 30, 0}    // X, Y, Z, E end location for z-probe deployment sequence
 # define Z_PROBE_RETRACT_START_LOCATION {49, 84, 20, 0}  // X, Y, Z, E start location for z-probe retract sequence
 # define Z_PROBE_RETRACT_END_LOCATION {49, 84, 1, 0}     // X, Y, Z, E end location for z-probe retract sequence

 # define AUTOLEVEL_GRID 24 // Distance between autolevel Z probing points, should be less than print surface radius/3.
```
这些是有关自调平系统的一些参数，先不管。自调平总是最后关心的问题。

```c++
// Travel limits after homing
 # define X_MAX_POS 130
 # define X_MIN_POS -130
 # define Y_MAX_POS 130
 # define Y_MIN_POS -130
 # define Z_MAX_POS MANUAL_Z_HOME_POS
 # define Z_MIN_POS 0
```

这些是根据热床大小定的。Z\_MAX\_POS 需要测量一下，是从挤出头到热床的距离。


除此之外，还有一个重要参数，就是：

```c++
 # define DEFAULT_AXIS_STEPS_PER_UNIT   {200, 200, 200, 439.5} //{80, 80, 80, 439.5}
```
这是和传动机构相关的（单位运行距离（1mm）下步进电机前进的步数。200,200,200 分别代表 x,y,z 方向的步进量，439.5(用的默认值，还没改)是挤出机步进电机的步数。 我用的是 0.9 步进，GT2 的皮带（即齿间距2mm），以及 16齿的同步轮。带入网上的计算器：[http://prusaprinters.org/calculator/][3]

或者把上述宏定义修改为下面这若干行代码[^1]

```c++:n
 # define STEPS_PER_REVOLUTION_X 3200
 # define STEPS_PER_REVOLUTION_Z 3200
 # define STEPS_PER_REVOLUTION_E 3200
 # define STEPS_PER_REVOLUTION_Y 6400

 # define IDLER_TEETH_X 8
 # define IDLER_TEETH_Y 8

 # define BELT_PITCH_X (.2 \* MM_PER_INCH)
 # define BELT_PITCH_Y (.2 \* MM_PER_INCH)

 # define PITCH_OF_Z_ROD 1.25

 // makergear extruder box
 # define EXTRUDER_GEAR_RATIO 13.0
 # define PINCH_WHEEL_DIAMETER 11.59

 # define AXIS_STEPS_PER_UNIT_X (STEPS_PER_REVOLUTION_X / IDLER_TEETH_X / BELT_PITCH_X)
 # define AXIS_STEPS_PER_UNIT_Y (STEPS_PER_REVOLUTION_Y / IDLER_TEETH_Y / BELT_PITCH_Y)
 # define AXIS_STEPS_PER_UNIT_Z (STEPS_PER_REVOLUTION_Z / PITCH_OF_Z_ROD)
 # define AXIS_STEPS_PER_UNIT_E (STEPS_PER_REVOLUTION_E \* EXTRUDER_GEAR_RATIO / (PINCH_WHEEL_DIAMETER \* PI))
 # define DEFAULT_AXIS_STEPS_PER_UNIT {AXIS_STEPS_PER_UNIT_X, AXIS_STEPS_PER_UNIT_Y, AXIS_STEPS_PER_UNIT_Z, AXIS_STEPS_PER_UNIT_E}
```
其中 STEPS\_PER\_REVOLUTION 是指电机转动一圈的步数（对于 0.9 步进来说是 360/0.9 = 400 步，但是还有 MicroStepping，在
Ramps 主板上可以通过跳线来设置，最高是 16 分度；因此，电机转动一周实际上会有 6400 个分度。这就是这个参数的由来 ）


----
【更新】今天看到这个不错：Hacking Marlin to add extruder load/unload: [http://3dwest.blogspot.hk][5]
以往更换料丝的时候进料、退料都要的拧半天调节旋钮，有了这个进料、退料的命令后一切就应该方便了。按照这个博客所说，只需要修改：ultralcd.cpp 文件：

```c++:n
 static void lcd_prepare_menu()
 {
     START_MENU();
     MENU_ITEM(back, MSG_MAIN, lcd_main_menu);
 #ifdef SDSUPPORT
     //MENU_ITEM(function, MSG_AUTOSTART, lcd_autostart_sd);
 #endif
     MENU_ITEM(gcode, MSG_DISABLE_STEPPERS, PSTR("M84"));
     MENU_ITEM(gcode, MSG_AUTO_HOME, PSTR("G28"));
     MENU_ITEM(gcode, MSG_LOAD_FILAMENT, PSTR("G21 G1 F500 E10"));
     MENU_ITEM(gcode, MSG_FEED_FILAMENT, PSTR("G1 F1000 E1000"));
     MENU_ITEM(gcode, MSG_UNLOAD_FILAMENT, PSTR("G1 F1000 E-1000"));
     //MENU_ITEM(gcode, MSG_SET_ORIGIN, PSTR("G92 X0 Y0 Z0"));
     MENU_ITEM(function, MSG_PREHEAT_PLA, lcd_preheat_pla);
     MENU_ITEM(function, MSG_PREHEAT_ABS, lcd_preheat_abs);
     MENU_ITEM(function, MSG_COOLDOWN, lcd_cooldown);
 #if PS_ON_PIN > -1
     if (powersupply)
     {
         MENU_ITEM(gcode, MSG_SWITCH_PS_OFF, PSTR("M81"));
     }else{
         MENU_ITEM(gcode, MSG_SWITCH_PS_ON, PSTR("M80"));
     }
 #endif
    MENU_ITEM(submenu, MSG_MOVE_AXIS, lcd_move_menu);
    END_MENU();
}
```

唯一需要注意的是按照你的 Bowden 管长度来调整 MENU_ITEM 的响应代码，作者的 Bowden 管是 1米长的，所以
用了 E1000 。



[^1]:	参考：[http://www.matterhackers.com/news/3d-printer-firmware-settings-stepper-motor-configuration][4]

[1]:	http://www.hkepc.com/forum/viewthread.php?tid=2084008
[2]:	https://github.com/RichCattell/Marlin/releases/tag/v1.04
[3]:	http://prusaprinters.org/calculator/
[4]:	http://www.matterhackers.com/news/3d-printer-firmware-settings-stepper-motor-configuration
[5]:    http://3dwest.blogspot.hk

[image-1]:	/3DP/_images/DSC00557.JPG
[image-2]:	/3DP/_images/DSC00558.JPG
[image-3]:	/3DP/_images/DSC00560.JPG
[image-4]:	/3DP/_images/DSC00561.JPG

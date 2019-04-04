---
title: "Marlin2.0 bugfix + Cohesion3D-remix 上使用 TMC2130 驱动"
date: 2019-03-21T23:30:38+08:00
draft: true

---

TMC2130 是一款非常有趣的步进电机驱动，最吸引我的地方是"失速检测" （Stall-detection) 功能，以及由此而来的"无传感器归零" （Homeless-sensing). 对我这个电路外行，也只有在这块驱动芯片发布多年，各种视频、资料都齐备之后，才有机会尝试. 

由于家里有很多块定制的 C3D-remix 主板，再加上最近一两年一直折腾小号的 CoreXY 机器使用的就是这块主板，因此我决定先买几块 2130 驱动，用这块主板试验一下.

# 软件准备

- PlatformIO 要安装 TMC2130Stepper 的库文件(by teemuatlut). 直接搜索并安装即可

- 主板通电设置 TMC2130 工作电压（此步骤先略过）

- 固件设置的更改：

  :::C

  # define X_DRIVER_TYPE TMC2130
---
title: "Kossel XL 构建记 (22) Mount the power brick, iteration equations"
date: "2014-09-02 23:20:00"
tags: ["3DP", "Kossel", "DIY","Frame","Iteration","Equation"]
draft: false
author: "tt4"
---


不知不觉又是5天没更了。时间过得真快，基本上 Kossel 的雏形已经搭建出来了，内部走线也已经布置完毕。接下来的问题就是总装了！基本上这两天都在折腾滑轨，发现其中一个左右摇晃的比较厉害，如果这样的话在打印时会有很大误差的。于是又返工，把轮子间的距离减小，又重新打了一版。以前滑轮中心距离铝型材中轴线的距离是 8.35 mm, 前天改成 8.15 mm 又打了一版。别看就差区区0.2mm，大概是两张 A4 纸的厚度，其影响却不能小觑。打完装上发现，果然不晃了！只是太紧了，影响滑块的运行。于是又打了一版 8.25 mm 的，发现依然太紧。想想算了，紧了会慢慢变松弛的，就先这样吧！

今天空闲的时候又在考虑装电路板的盒子如何设计，目前思考的结果大致如图所示：![][image-1]

想想，可以在最终组装框架之前，在里面加上一些支撑结构，以使整体结构更稳定，我称之为防滚架。然后再考虑外壳用一体成型的工艺（YYing...）;-)

----
顺便说说迭代方程，这是 Y 问我的，大概是求解 f(f(x)) = x² + x 这类方程。没有通用方法，借用知乎中的一句话：这是数学中的黑领域 :-)

有空细说，画图去了！

----
【更新】顺便量了电源模块的 M4 螺丝孔位置，画了四个固定块，把电源固定在铝框架底部。电源模块用的是这种通用的 12V 电源：![][image-2]。其实我更喜欢那种外接式的笔记本电源（称为 Power Brick），外接在打印机上，不占底部的空间。这样我就可以考虑把主板藏在底部了。但是进行了一番调研之后发现，Power Brick 所能提供的电流不够大（最多15A 左右），如果采用加热的热床的话，热床至少需要 5—10A 的电流，再加上各种电机(按每个电机 2A 计算)、加热头，粗略估计 20A 左右的电流比较保险，于是就买了这种 12V 30A 的大电流通用电源。（所以，你就知道一台 3D 打印机的耗电量是多少了，如果有加热的热床的话，粗略估计会有 240瓦的功耗！）顺便提下，自从研究过功耗、电流等等的影响之后，我也开始注意导线的粗细了：）





[image-1]:	/3DP/_images/case.png
[image-2]:	/3DP/_images/DSC00551.JPG

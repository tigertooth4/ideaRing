---
title: "Kossel XL 构建记 (4) Auto-leveling thoughts"
date: "2014-07-26 12:00:00"
tags: ["3DP", "Kossel", "DIY"]
draft: false
author: "tt4"
---


今天基本确定了框架的方案，ming 的方案中螺丝孔似乎大了点，我还是换用了 @Jaydmdigital 的方案，见
[GitHub][1]. 所以下面可做的事情是，用 Jaydmdigital 的 Visual Calc 画出一个效果图。与之相关的事宜请看：
[Google论坛][2] 或者 [Reprap论坛][3]。

我似乎还需要一个皮带张紧机构的设计方案，台湾朋友的博客中有一个现成的：
[http://diy3dprint.blogspot.tw/2014/07/blog-post.html][4] 但是我觉得还是太复杂了，如果能够和滑块结合
在一起就好了。


关于平台的自动校准，用的最多的方法是探针（在加热头旁边加一个可以收缩的探针）当探针碰到打印平台时触发
微动开关，从而探测到探针触及的地方的高度信息，用以修正平台的起伏。这个设计有很多衍生的设计，例如用
Hall-磁效应代替微动开关、用加热头代替探针触碰打印平台，或者，将触碰开关的触发设计改成压感电阻的设计
(FSR)，当探针下降到碰触到打印平台时，平台下的压感电阻电阻上升，形成开关效应。

我个人更倾向于采取机械的方式，因此，我觉得用打印头代替探针的方案比较容易操作。这个方案最早是 David 在
[Google论坛][5] 上公布的，Steve Graber 给出了一个实现，见 [GitHub][6], [YT][7]。

这里是另外一组关于加热头标定的[讨论][8]（以及方案）。


[1]:	https://github.com/Jaydmdigital/Kossel_2020
[2]:	https://groups.google.com/forum/#!topic/deltabot/DSCs4O8fn00
[3]:	http://forums.reprap.org/read.php?178,342575
[4]:	http://diy3dprint.blogspot.tw/2014/07/blog-post.html
[5]:	https://groups.google.com/forum/#!msg/deltabot/lJqDukVk9PA/ofv9ccMdheUJ
[6]:	https://github.com/grabercars/Cerberus_Pup_170_GT2_belt_drive
[7]:	https://www.youtube.com/watch?v=e119OXzkk7s&feature=youtu.be
[8]:	https://groups.google.com/forum/#!searchin/deltabot/probeless/deltabot/_O8cKhLWcuc/ppdQh_bhup8J

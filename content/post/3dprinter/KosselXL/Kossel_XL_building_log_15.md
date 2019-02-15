---
title: "Kossel XL 构建记 (15) Effector plan"
date: "2014-08-14 10:06:00"
tags: ["3DP", "Kossel", "DIY","MIY","Effector", "Design"]
draft: false
author: "tt4"
---


*Effector* 又叫效应器，是一个生物学里面的名词。这里我们所指的 Effector, 就是悬挂挤出头的吊台。因为我
 们要在吊台上添加自动调平的机构，所以吊台的设计就比一般的吊台复杂不少。要在吊台上添加微动开关、机械部
 件、弹簧等等，保证当挤出头触碰玻璃板的瞬间，微动开关可以被触发，为了这个目的，这几天脑子里各种方案在
 打架...

目前设计的方案是参考（copy）*ATOM3DP* 的。整个联动机构都包在一个类似宇宙飞船外形的舱里。从外面是看不
到微动开关的。碍于微动开关的尺寸，所以整个机构不可能做得很小巧，而且在下部还要装 E3D 的散热风扇
(30x10)，所以后部又要留下足够的空间，使得整个装置的空间都很紧张了。

这是我目前的设计图，虽说是 copy，但是还是和 ATOM3DP 有区别的。![][image-1] 主要是目前 E3D 的 groove
非常大，因此我要预留比 ATOM3DP 设计中更大的空间。

这是 Effector 底部的空洞：![][image-2]这是上面的盖子![][image-3]可以叫它马桶盖😓. 中间使用一颗 m3 螺丝
固定的，到时还要在连接处加上垫片以便上面的盖子不移位。

目前还没有预留固定 groove 的孔，主要是不清楚孔该打在哪里。而且以后还要考虑到和微动开关的配合（微动开
关的位置）等，所以今天我先要打出一个小样，以便今后继续研究。

----

【补充】这是前天制作好的连杆；误差应该在 ± 0.2mm，所以我在滑轨上先定好连杆的长度，然后拧上两个固定微
动开关的零件限位，这样再粘连杆头的时候就不会有错了！![][image-4] ![][image-5] ![][image-6]
![][image-7]

[image-1]:	/3DP/_images/Effector.png
[image-2]:	/3DP/_images/Effector-base.png
[image-3]:	/3DP/_images/Effector-lid.png
[image-4]:	/3DP/_images/DSC00496.jpg
[image-5]:	/3DP/_images/DSC00497.jpg
[image-6]:	/3DP/_images/DSC00498.jpg
[image-7]:	/3DP/_images/DSC00500.jpg

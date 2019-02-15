---
title: "Kossel XL 构建记 (18) Effector design "
date: "2014-08-17 23:49:00"
tags: ["3DP", "Kossel", "DIY","MIY"]
draft: false
author: "tt4"
---


看来目前一切正常，我经常感叹：这台打印机真是从零开始制造的。。。一切都要设计。今天早晨开始调试
effector 的设计方案，之前的方案在做微动开关螺丝孔的时候高了大概 2mm, 因此每次盖上马桶盖的时候一定会盖
不严。现在把微动开关沉下去 2mm 后问题解决了！

然后是用来拉紧马桶盖和底部的螺丝，因为螺丝套在圆珠笔芯的弹簧上，所以整个机构得以实现目的。但是今天发
现，螺丝的螺纹使得弹簧收缩张开时都有很大阻力，于是用锉刀把螺丝中部的螺纹磨平就好了（螺丝还是挺容易锉
的:-D）

今天不早了，等明天再上图吧！设计 effector 的过程真是艰辛。而且，我现在对黄色的马桶盖也不甚满意（貌似
太 juvenile 了，也许纯黑色更大气点？）

因为 effector 的底座厚了几毫米，原来默认的 hotend 固定风扇恐怕安不上了，需要重新做一个，在某宝上看到
了这款 25mm 的[风扇][1]（够小巧 o(╯□╰)o ）。还没有下手，因为不知道用 12V 还是 5V 的。所以 Ramps 1.4
板子上的风扇都是怎么连线的呢？最好看这个网页：
[http://start3dprinting.com/2013/04/adding-a-fan-to-ramps-1-4-board/][2] 说的很清楚，要想要一个能够控
制的风扇，要用 D9 (应该是 12V 的)，要想要一个常转的风扇， Ramps 1.4 板子上有个写着 F1 的风扇接口。

写到这里，又想到应该在 effector 上预留几个孔，好固定吹耗材的风扇啊，不过不知为什么目前所知 Delta 系的打印机都没有这个挂在 effector 上用来吹耗材的风扇？

----
【睡前更新】这个网站不错：[http://start3dprinting.com][3]

3D 打印的印刷电路板：[https://www.kickstarter.com/projects/cartesianco/the-ex1-rapid-3d-printing-of-circuit-boards][4]

【跳票的更新】说是要上图的嘛！就让大家看看 effector 的几版打印件，区别主要是螺丝孔的位置啦！（照片可能不容易发现）

最开始学习的网上的 effector 设计：![][image-1]

G1, G2, G3……![][image-2] (请无视那脏兮兮的键盘= =b)

试装配成功（所有的线材都是走外部的）![][image-3]




[1]:	http://item.taobao.com/item.htm?spm=a1z0k.7385961.1997985097.d4918997.LaP0Zs&id=37389879749&_u=h7veq78468c
[2]:	http://start3dprinting.com/2013/04/adding-a-fan-to-ramps-1-4-board/
[3]:	http://start3dprinting.com
[4]:	https://www.kickstarter.com/projects/cartesianco/the-ex1-rapid-3d-printing-of-circuit-boards

[image-1]:	/3DP/_images/DSC00512.jpg
[image-2]:	/3DP/_images/DSC00510.jpg
[image-3]:	/3DP/_images/DSC00509.jpg

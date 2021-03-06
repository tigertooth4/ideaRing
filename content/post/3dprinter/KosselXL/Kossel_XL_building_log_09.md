---
title: "Kossel XL 构建记 (9) Y-shape carriages design, OpenSCAD"
date: "2014-08-02 10:45:00"
tags: ["3DP", "Kossel", "DIY","MIY","Math","Polar"]
draft: false
author: "tt4"
---


OpenSCAD 真是个好东西。当你规划好每个点的位置后，事情真是变得轻而易举。如果你觉得那个地方长了，或者短
了，只要调调参数就能搞定！昨天一直在设计线性滑轨和上面的连杆支架方案，所以没有记录。今天一起补上！

昨天把支架组装好了, 真是要拧很多螺丝啊！拧到手酸！不过效果还是不错的！支架组装起来要比我想象的大！这
是组装过程图：![][image-1]

昨天在咖啡馆调整了 Y-型滑块的设计，感觉不错，最后用的是 (1/2,3.5) 这个系数组合。![][image-2] 然后就到
了打印制作样品阶段了。首先在 Cura 中切片，![][image-3] 然后生成的 GCode 文件放到打印机的 SD 卡中打印
![][image-4]。整个过程比较顺畅，就是 Cura 的切片打印效果比较一般...

OpenSCAD 的一大优点就是它是得调整模型变得非常简单。要想给滑块配备不同大小的滑轮（我淘了两种，一种
16mm直径,一种20mm直径）。以往要是用 123D Design 的话，就要大动干戈地修改模型的比例了。但是，在
OpenSCAD 中就改一两个参数，1分钟就搞定了！

在铝框架上实际实验了一下，发现16mm直径的滑轮存在不圆的问题，在滑轨上运动时有明显的顿挫感。而且确实太
小了，和整个庞大的打印机框架不协调。于是确定了用 20mm 滑轮。

最后一步，就是在滑块上设计支架了。说是最后一步，但其实非常复杂，要在上面设计同步带固定机构，还要留出
合适的角度以备今后安装吊臂的需要。不过，最后熬了会儿还是设计出来了！![][image-5]

这个方案其实还有改进的余地，例如可以将上下两个固定皮带的固定槽部件分开，然后用螺丝固定，这样就能起到
调节同步带张力的目的了！不过，考虑到同步带上也可以增加张紧装置，所以这一步就暂时省略了！

下面还需要在滑块上确定一个位置，以方便今后平台调平。

[image-1]:	/3DP/_images/DSC00398.jpg
[image-2]:	/3DP/_images/yshape.png
[image-3]:	/3DP/_images/DSC00404.jpg
[image-4]:	/3DP/_images/DSC00403.jpg
[image-5]:	/3DP/_images/YCarriageDesign.png

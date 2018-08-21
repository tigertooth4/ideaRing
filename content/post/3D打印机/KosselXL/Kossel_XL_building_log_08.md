---
title: "Kossel XL 构建记 (8) Delivery, Y shape design"
date: "2014-07-31 19:00:00"
tags: ["3DP", "Kossel", "DIY","MIY","Math","Polar","Design"]
draft: false
author: "tt4"
---

今天收了 5 个快递... 截止到目前为止另外还有 4 件在路上。铝框架：![][image-1] ![][image-2] 滑
轮：![][image-3] 还有带圆孔强磁铁以及各种螺丝螺母（没拍照，磁铁真的磁力强到可以夹手哦！）等晚上回家可
以装配了！

昨天经历了史上最严重的一次堵头，等我回家看到时，入料口的 PLA 都已经热胀到这种程度了：![][image-4]。原
因不明，也许是因为料丝粗细不均匀所致。不过真让我下了一跳，我还以为里面已经化到不成样了，不过还好，里
面并没有堵得很厉害。

昨天在 YT 上闲逛的时候突然看到了这个 [Cerberus 3DP][1] 的视频，突然来了灵感：滑车如果像视频中一样设计
成 Y 字形，可以大大减轻重量，并且比现在的 U 盾型可要酷炫多了！于是就想用 OpenSCAD 设计一个（等边三角
形还是用 OpenSCAD 好画！）但是不知道这样的 Y 字形曲线是怎样设计出来的。画了个草图：![][image-5]

Google 了一些关于 OpenSCAD 的资源，看到了下列 OpenSCAD 扩展库
[https://github.com/openscad/openscad/wiki/Libraries][2]，也许可以派上用场！

好吧！晚上可以大干一场了！

----

【更新】晚上本想好好研究一下如何用 OpenSCAD 设计一下 Y-carriage 的造型，想着三个滑轮应该在圆周上
分布，相隔 2 π/3 弧度，然后坐标原点放置一个小圆，中间用 hull 函数做凸包，如图中所示 ![][image-6]这样
的话要算几个距离。

后来一想，完全不用这么 low 啊！用极坐标多好？可以做到自然、平滑的过渡。于是想了一个这样的函数，在
Grapher 中做出图像是这样的：![][image-7] 注意，只有中间那个三叶图是我画的。

嗯，这样就好多了！要多大等比例缩放就好了 ！ 形状可以通过调整 cos 的次数和后面加的常数来调节。。。

----
【更新2】完美主义者为了不留遗憾，又找来 Mathematica 把所有较小的参数组合都试了个遍，想从里面找到
一个最好的方案，见下图：![][image-8]

顺便插一句：Mathematica 的帮助总能给你惊喜，例如这个例子 ![][image-9]

[1]:	https://www.youtube.com/watch?v=32bxll7pv9U
[2]:	https://github.com/openscad/openscad/wiki/Libraries

[image-1]:	/3DP/_images/DSC00391.jpg
[image-2]:	/3DP/_images/DSC00392.jpg
[image-3]:	/3DP/_images/DSC00393.jpg
[image-4]:	/3DP/_images/DSC00388.jpg
[image-5]:	/3DP/_images/DSC00396.jpg
[image-6]:	/3DP/_images/DSC00397.jpg
[image-7]:	/3DP/_images/polarCoordinateDesign.png
[image-8]:	/3DP/_images/all-combo.png
[image-9]:	/3DP/_images/amazing-curve.png

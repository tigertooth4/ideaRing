---
title: "Kossel XL 构建记 (20) Effector"
date: "2014-08-21 17:55:00"
tags: ["3DP", "Kossel", "DIY","MIY","Effector", "Wiring"]
draft: false
author: "tt4"
---


不知不觉，这个系列已经来到第 20 篇了！Effector 的组装今天终于完成！所有的布线都藏在了 Effector 内部，然后从“马桶盖”的孔里穿出。这是最后组装好的照片：
![][image-1]![][image-2]
还有一段视频：
<embed src=https://www.dropbox.com/s/vs9k8lwwbqkfkhc/Clip1.mov></embed>

看起来真的跟 #ATOM3DP 的设计很类似（废话，明明就是参考 ATOM 的设计嘛，能不类似吗？！）但是也是有很多不同的，例如微动开关的位置（ATOM3DP 是放在盖子里的，而我是把微动嵌在了底部；另外由于 ATOM 的加热头是定制的，因此 ATOM3DP 可以把加热头的散热风扇直接嵌在 effector 内部，可是我是用成品 E3D 热头，碍于其长度，放进 effector 内部只能够加大 effector 的体积，增加很多体积和重量。）

在更换了电烙铁以后，我的焊接技术突飞猛进了（工具很重要！）目前步进电机还没到，所以没法大规模组装（趁此机会倒是可以仔细研究一下整体布线的问题。）

----
【更新】发现我的微动开关接线焊错位置了！微动上有三个触点，分别标着 c, no, nc。(nc 不代表脑残哦，而是 normally closed 的缩写；no 是 normally open 的缩写)。接线一般需要连接 c 端与 no, nc 其中一端，如果你的微动处于常关，偶尔触发（开启）的状态，那么应该选择连接 nc，比如大多数的 X,Y,Z 轴的限位开关。而 no 是我应该用在 effector 这里面的。

[image-1]:	/3DP/_images/DSC00523.jpg
[image-2]:	/3DP/_images/DSC00530.jpg

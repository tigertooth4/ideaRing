---
title: "Kossel XL 构建记 (17) Stepper motors"
date: "2014-08-15 14:30:00"
tags: ["3DP", "Kossel", "DIY","MIY"]
draft: false
author: "tt4"
---


Effector 一定是我用 OpenSCAD 实现的最复杂的模型了。而且，布线都藏在了 effector 底部，精细程度是目前我设计的模型中最高的。

今天又在研究步进马达，这个型号 [42BYGHM810][1] 在某宝中可以找到，是 Wantai 出品。0.9°步进，静力矩
4800 g.cm。（绝定用0.9步进的了！）这台电机目前看唯一的缺点是只有光轴电机（也许拿到以后要打磨一下才可
以用 o(╯□╰)o）

[Reprap.org][2] 中关于步进马达的介绍（搜索 step motor） 还是值得一看的！额哦，某宝的这款马达是 2.4v,
2.4A 的，而 Reprap 中说
> stepper motors rated for 3-5 V and 1-1.5 A are generally recommended

看来我不能选这款马达了，因为

> If a motor is rated to more amps or volts than your driver can produce, your motor will not produce the manufacturer's rated torque.

这是不好的，扭矩对于稳定性还是非常重要的。所以看来我要在精度和稳定性之间做一个平衡了。不过这里还有一
款 0.9 步进的，基本能够达到我的要求：[42BYGHM809][3] (2.8v, 1.7A, 4200g.cm )

如果是发烧友，对精度有偏执的追求的话，可以考虑加上减速齿轮，这样可以减小步进角，加大扭矩（当然代价就
是降低了最高转速）。步进角对于 3D 打印机的意义可以参考我之前的博文 [Kossel Log(12)][4].

----

【更新】这里有一个关于 Marlin 使用的介绍：
[http://solidutopia.com/marlin-firmware-user-guide-basic/][5]

哈！Marlin builder! [http://marlinbuilder.robotfuzz.com][6]


[1]:	http://item.taobao.com/item.htm?spm=a230r.1.14.1.CsWZR2&id=1708079780&ns=1&_u=g7veq783097#detail
[2]:	Reprap.org
[3]:	http://item.taobao.com/item.htm?spm=a1z10.5.w4002-2933553768.15.sa7Fpz&id=1708088130
[4]:	kossel-planning-12
[5]:	http://solidutopia.com/marlin-firmware-user-guide-basic/
[6]:	http://marlinbuilder.robotfuzz.com

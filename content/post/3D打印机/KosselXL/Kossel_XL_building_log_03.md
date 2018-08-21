---
title: "Kossel XL 构建记（3） Planning the frame design "
date: "2014-07-24 13:30:00"
tags: ["3DP", "Kossel", "DIY"]
draft: false
author: "tt4"
---

框架的方案确定了：来自 [mming1106][1] 的设计：[2020 motor frame][2] [2020 top frame][3]。2020 motor
frame 已经是第二版，第一版见 2020 top frame，第二版的好处是增加了两个改锥孔，可以帮助拧螺丝，而且增加
了 Kossel 的 logo, 但是我不太喜欢这个第二版的字体（我更喜欢 1515 原版的字体，我是个完美主义者 - -）。
由于作者没有提供 scad 文件，只好有空的时候修改 STL 了，可惜今天 tinkercad.com 无法连接...

回到家后，tinkercad 终于没问题了！Rostock Mini 的回抽还是有问题，今天走之前打的 2020 motor frame 不知
什么原因没有打完。记得我是用 Slic3r 做的切片，回抽的设置可能不对，或者，有可能热端温度太高了，导致回
抽不利，或者是用的白色 PLA 质量不好... 不管了。 花了点时间把热敏电阻中的热缩管给去掉了，这玩意融化以
后散发出非常不好的味道，而且融化的热缩管材质还留下来，把打印件给弄脏了。

现在我想试试 Probeless Hotend autolevelling. 最早作出原型设计的是 David Ng (dnhkng@github) ,[这里][4]有 STL 文件。


[1]:	http://www.thingiverse.com/mming1106/designs
[2]:	http://www.thingiverse.com/thing:298807
[3]:	http://www.thingiverse.com/thing:208458/#files
[4]:	https://github.com/dnhkng/Marlin/tree/deltabot/HotendProbe

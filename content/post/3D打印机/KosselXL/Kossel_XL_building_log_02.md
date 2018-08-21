---
title: "Kossel XL 构建记（2） Hotend decision"
date: "2014-07-23 22:30:00"
tags: ["3dp", "Kossel", "DIY"]
draft: false
author: "tt4"
---

今天搜到一个较为便宜的 [E3D 挤出头][1]，某宝代号为 36891850532。厂家附赠挤出头2个，貌似不错。

编了一下午程序，来计算一个斜洛朗级数的开方。注意，要想开方的话是有条件的，目前我能想到的一类可开方的
算子是当级数的系数环上的自同态是恒等映射的时候，否则要想求解系数的话需要解环上的两个同态方程（我目前
还不知道有没有统一的解法）。这个与主题无关，我会放在另一篇文章中另说。

这个台湾朋友的博客非常好，在此顺便分享下：[http://diy3dprint.blogspot.tw/][2]

关于挤出头散热问题的文章，可以看上述台湾朋友的博客：
[http://diy3dprint.blogspot.tw/2014/01/blog-post.html][3]。我刚看完，涨姿势了

以下是今天看到的一些资源：

* [Kossel 2020 build log][4]
* [Jaydmdigital/Kossell_2020_@github][5]
* [Kossel mini Prime line roller carriage @ thingivise][6]
* [Kossel mini 3d printer vertical movement Tutorial][7]
* 看 台湾朋友关于构造 Atom 印表机的文章也受益匪浅，Atom 的尺寸大概是 360x720

目前需要确定一下框架使用的 STL 文件方案，以及滑轨的方案，这样才能去买滑轮啊

还有，看到 Atom 用的挤出头自调平方案也长草了，明天去谷歌一下 😊

[1]:	http://item.taobao.com/item.htm?spm=a230r.1.14.15.KNxOPA&id=36891850532&ns=1#detail
[2]:	http://diy3dprint.blogspot.tw/search?updated-max=2014-02-24T23:35:00%2B08:00&max-results=7&start=12&by-date=false
[3]:	http://diy3dprint.blogspot.tw/2014/01/blog-post.html
[4]:	http://forums.reprap.org/read.php?178,342575
[5]:	https://github.com/Jaydmdigital/Kossel_2020
[6]:	http://www.thingiverse.com/thing:215438
[7]:	http://www.electronhacks.com/2013/12/kossel-mini-3d-printer-vertical-movement-tutorial/

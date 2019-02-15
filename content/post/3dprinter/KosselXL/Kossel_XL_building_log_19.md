---
title: "Kossel XL 构建记 (19) Wiring plans "
date: "2014-08-19 13:16:00"
tags: ["3DP", "Kossel", "DIY","MIY","mainboard","Assembly","Wiring", "Rumba", "RAMBo"]
draft: false
author: "tt4"
---

讨厌返工，不过之前框架 \<50% 的 infill 还是让我担心整个系统的强度。所以今天回去打算再换 50% 的 infill 打印一遍....

最让人纠结的问题就是整个电路部分应该放在上面还是下面。在网上搜索许久，发现大多数 Kossel Mini 的布局都是把电路部分塞在底部框架里的，这样有个坏处，就是底部机构过于复杂（要考虑到电源如果放在底部的话，电路板几乎没有空间了。而且，如果在底部增加热床的话，散热是一个极大的问题。）所昨天一直在研究如何将电路板移到外侧，考虑到 LCD 电路板和主板的距离不可能太远，一种方案就是把电路板和主板都放在底部外侧，但是这样我显然不太满意，因为 RAMPS 1.4 的板子还是挺大的。今天突然想到：其实可以把电路板放在顶部框架上，这样底部整个的空间都可以被利用起来安放电源、热床等等，也同时解决了主板散热的问题，LCD 也可以和主板捆绑在一起。而且，电线都可以自上而下走向挤出头端（说不定可以把 Bowden 管和电线部分捆扎在一起也说不定）。但是这样的话，就需要很长的电机连线（从低端到顶端）。

关于整个机器的布线，我有一个想法，就是利用 2020 型铝型材的内部空洞来走线。电机的线是 4 股线，可以塞在每根立柱的内侧 ：）

----
【更新】已经购买了 RAMPS 1.4 的主板。但是 RAMPS 双层板子的体积有点大，所以今天又在网上搜了搜，除了 RAMPS 以外，其实还可以尝试 RAMBo，Rumba (这两个太像，不过据说 RAMBo 的稳定性更好些)。关于比较，可参考这里：[http://www.dummies.com/how-to/content/10-options-for-reprap-3d-printers-electronics-and-.html][1] 和 这里 : [http://forums.reprap.org/read.php?1,242647,245155][2].

这里有一篇博客是关于 Kossel 和 Rumba 的，[http://3dwest.blogspot.com/2013/12/wiring-rumba-for-kossel-mini-round-1.html][3]。

【更新】香港的 3DP 论坛：[http://www.hkepc.com/forum/forumdisplay.php?fid=259][4]

[1]:	http://www.dummies.com/how-to/content/10-options-for-reprap-3d-printers-electronics-and-.html
[2]:	http://forums.reprap.org/read.php?1,242647,245155
[3]:	http://3dwest.blogspot.com/2013/12/wiring-rumba-for-kossel-mini-round-1.html
[4]:	http://www.hkepc.com/forum/forumdisplay.php?fid=259

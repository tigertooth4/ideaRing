---
title: "Rostock Mini Pro J-head 挤出头peek管风扇架"
date: "2014-07-25 11:30:30"
tags: ["3dp", "Rostock", "DIY"]
draft: false
author: "tt4"
---

最近总是饱受打印件抽丝的困扰，打印件里外总是有好多打印头运行时拉出来的细丝，极不美观。而且，这个J-head的制造水平实在欠佳，测温探头的导线居然是用热缩管包裹的，加热到200°C以后，热缩管就化了，流出一些棕黑色胶装液体，污染打印件不说，还有股难闻的气味。尝试将热缩管和 J-head 的Peek 管之间加大距离也没有太好的效果。看来，是要想一个解决方案了。

经过一番研究，发现所有这些问题的解决方法，也许就在设法降低 Peek 管的温度上。Peek 管在打印时我感受到温度至少有100°C以上，温度过高至少有两个坏处：

1. Peek 管过热会导致堵头，这个原理请大家参考台湾朋友的博客
2. Peek 管过热会使周围的导线融化

于是，改造方案当然就围绕降低 Peek 管温度来考虑了。在 Thingiverse 上找了半天也没有找到合适的打印件（Rostock Mini Pro 使用的 J-head 大概探出吊台20mm 左右，不算下部的加热块和喷嘴。）所以，必须设计一个大概 20mm 高的打印件。但风扇的大小是 40x40mm, 所以风扇直立的话肯定会超出 J-head 的高度，这样不行。所以，风扇只能倾斜放置。而且，我希望风会包围 Peek 管，因此环形方案值得考虑。经过昨天一晚上的折腾以后，终于给出了一个[设计方案][1]，见：
<iframe width="560" height="350" src="https://tinkercad.com/embed/4dAFjjnJ5B2?editbtn=1" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"> </iframe>
下面是装配完成图。![][image-1] ![][image-2] ![][image-3] 是否有效还要等待时间来检验。



[1]:	https://tinkercad.com/things/4dAFjjnJ5B2

[image-1]:	/3DP/_images/DSC00376.jpg "Side view"
[image-2]:	/3DP/_images/DSC00377.jpg "Bottom side view"
[image-3]:	/3DP/_images/DSC00378.jpg "Top side view"

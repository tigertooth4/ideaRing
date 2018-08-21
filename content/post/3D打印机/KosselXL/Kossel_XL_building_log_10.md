Title: Kossel XL 构建记 (10) Y carriage, steel ball assembly
Date: 2014-8-4 16:15:00
Tags: 3dp, Kossel, DIY, MIY, OpenSCAD
Status: public

昨天一晚上，终于把三颗滑块装配完毕，家里居然没有 M4x12 的螺丝了，于是用了 M4x14 的，要在滑轨背后看不
到的地方把孔开得再深一些。。。 这是零件图：![][image-1]Y型滑轨组装起来的结果见：![][image-2]上面有三
颗螺丝孔是用来固定上面的连杆支架用的。连杆的组装也很容易，最后的组装结果是这样的：![][image-3]注意还
有一颗 M3x20 的长螺丝是要拧在连杆支架上的，这颗螺丝孔的位置我是根据 K800endstop 的位置设计的，作用是
将来当滑轨向上运动时触发微动开关。

还要注意，钢球一定要牢固的固定在支架上，而且，钢球的直径要用游标卡尺确定看看是否一致（不一致的话会对
最后的打印效果产生影响）。而且钢球在水平方向要在一条直线上。![][image-4]

目前，微动开关的固定件采用的是 Kossel-800 的设计，不过微动开关还没有买 ;)

今天还设计了连接磁铁用的连杆头：![][image-5] 因为我订购了两种尺寸的打孔磁铁（OD=10mm, OD=12），所以就
设计了两种不同大小的连杆头。但是，碳纤维杆还没买，所以现在谈设计还只是纸上谈兵。。。

接下来还要采购不少东西：微动开关、步进电机、碳纤维杆等等。趁着采购的东西没到，我可以开始考虑吊台的设
计了。

----

【更新】关于步进电机的购买有些纠结了，因为有1.8°步进的还有0.9°步进的。1.8°在 3D 打印机上是最常见的。
但是，貌似 0.9° 会带来更高的精度。上网查了一下，有人说，对于 笛卡尔系 的3D 打印机，步进电机精度的提
高很难得到打印精度的提高。特别受制与喷嘴的直径。但是对于 Delta 系的打印机，其各个区域的打印精度是不同
的，因此改善步进电机的精度确实能够换来打印质量的提升。但是代价是打印速度会比以前慢，而且步进电机的扭
力也会比以前小一些。

考虑到现在 Rostock 的打印质量，我在纠结是否有必要用 0.9°的步进电机。一块 0.9 步进要比通常的 1.8 步进贵十几块呢。

----

【无果】不过找到了这样一个视频，是讲 mini Kossel Calibration using Repetier FW， 见 [YT][1]. 

哦还有这个网站：讲那些参数是影响 Delta 的重要指标，其中有一句话意味深长：“Accurate dimensions are
far less important than symmetry！”[http://minow.blogspot.com/index.html#4918805519571907051][2]

还有这篇文章值得一看：3d-printer firmware settings stepper motor configuration:
[http://www.matterhackers.com/news/3d-printer-firmware-settings-stepper-motor-configuration][3]

----

【更新2】终于在电机的海洋中找不到方向了。各个厂家，各种型号，各种电流大小。。。实在不知道该怎么选择了。
Reprap 的论坛上居然还说要 12V 的步进。。。然后发现一个电机的型号42BYGHW811 居然在某宝搜到了是在
Wantai 的旗舰店里卖的。高兴了一下，然后再一看，他家的42步进只有光轴的卖，没有D型的怎么固定齿轮伐？只
好继续找。好在最后找到了 Kossel 800 的电机配置：某宝 id 如下：

- 3949282634
- 39692700361
- 9475125162

不过还是对 0.9° 步进有残念。。。 算了，洗洗睡吧，明天继续研究

----

【更新3】David Ng 的google+, 他是磁头连接方式和 probeless hot end 的鼻祖吧？！
[https://plus.google.com/u/0/112215345767735991135/posts/35cLAzCnvXY][4]

----

【更新4】尼玛！KosselXL 这个名字已经被用了：[http://www.builda3dprinter.eu/kosselxl-released/][5] 不
过这个XL并没有多少新东西。。。而且它发布的日期是 7月31号，我显然比他早几天;-)


[1]:	https://www.youtube.com/watch?v=uDB4hE6nyYI
[2]:	http://minow.blogspot.com/index.html#4918805519571907051
[3]:	http://www.matterhackers.com/news/3d-printer-firmware-settings-stepper-motor-configuration
[4]:	https://plus.google.com/u/0/112215345767735991135/posts/35cLAzCnvXY
[5]:	http://www.builda3dprinter.eu/kosselxl-released/

[image-1]:	/3DP/_images/DSC00408.jpg
[image-2]:	/3DP/_images/DSC00409.jpg
[image-3]:	/3DP/_images/DSC00410.jpg
[image-4]:	/3DP/_images/DSC00412.jpg
[image-5]:	/3DP/_images/JointConnector.png

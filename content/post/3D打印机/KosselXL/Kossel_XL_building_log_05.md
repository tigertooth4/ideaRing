Title: Kossel XL 构建记 (5) Kossel frame decision, design goals
Date: 2014-7-28 15:40:00
Tags: 3dp, Kossel, DIY, MIY
Status: public

今天学了个新词汇：MIY (make it yourself). 昨天因为出去吃饭没有记录。

其实，昨天完成了 Kossel 框架的修改，基于：[Jaydmdigital@GitHub][1]，使用 2020 框架铝。他是基于
Johann 的设计。要说 Johann 的设计其实已经顾及到了铝材的尺寸，只要铝材相应的 Channel\_deep 和
Channel\_width 就可以了。在 Jaydmdigital 的代码中，这两个参数没有修改，而是绕过重新定义了两个新的参数
fin\_w 和 fin\_d。Jaydmdigital 的版本这两个参数不适合 2020 国标铝材，因此我又做了调整。另外一处关键的
修改是 frame-motor 上的文字。之前是 *Kossel*。但是因为我正做的这台是基于 2020 铝的，而且要根据我的要
求做很多修改，因此我就改了一个更适合我的 MIY 的名字：*Kossel XL*. *XL* 意思是 *extra large*，当然指的
我的机器尺寸会比较大。另外，*XL* 还是我的名字<s>（以及mvip名字）</s> 的缩写，发音还像 excel
(excellant). 最后在 OpenSCAD 中做出图来是这样：![][image-1]

顺便说说 Kossel XL 的设计目标，有以下几点：
1. 能够达到我现在这台 Prusa i3 的打印尺寸，即约 200x200x200 mm³，同时又可以放在桌面上；由于 Delta 打
   印机的自身结构，要想达到这个尺寸，计算可知框架需要的大致尺寸，最后我选择的尺寸为：330x650，其中
   330mm 为底边三角形长度，650mm 是大致高度。具体打印尺寸可以看 Johann 的 Excel 表格，我已经转换成了
   Numbers 文件，见 [这里][2]。
2. 用铝框架本身做导轨，不使用线性滑轨（为节约成本）。
3. 挤出头 (hotend) 部分要方便拆卸或者更（升）换（级），以便堵头时的清理。为此，考虑使用磁关节连接吊台
   （effector）和吊臂（rods）, 这也是 Kossel 800 和 ATOM 使用的方案；使用线缆插头（连接器）连接吊台上
   的器件。
4. 无探针的平台自调平（Probeless auto-levelling）：最近饱受堵头之苦，大部分情况都是热床和挤出头靠的太
   近了，使得耗材无法被挤出…… 我喜欢机械开关的方式，所以最可能的选择是利用挤出头作为探针，这方面的
   设计在 google 论坛和 github 上都可以找到，但我发现，实际打印出来的模型并不令人满意（要么是关节不灵
   活或无法触发微动开关；要么是整个设计强度不够）。ATOM 采用了自己的设计实现，但网上只能找到基座的
   STL 文件，活动部分无法找到。看来只能自己动手对现有的设计做修改了。
5. 简洁、布线合理、Bowden 管要尽可能短（因为 Bowden 的远端寄出方式经常会浪费掉和 Bowden 管同样长度的
   耗材）因此好的解决方式也许是把挤出机吊在框架的中部位置（或者顶部）？具体设计方案还未确定。

最终配色方案会是这样（说实话原色铝合金配什么都不是太好看了）![][image-2] 和分解图： ![][image-3]

---- 
UPDATE: 在 Prusa i3 上把框架打出来了，打印质量还不错！![][image-4] ![][image-5] ![][image-6]

[1]:	https://github.com/Jaydmdigital/Kossel_2020
[2]:	https://www.icloud.com/iw/#numbers/BAL9HuX5gIdmpRTC4FGBLZ4D8AYeCgS0C7CF/Kossel_frame_calculator

[image-1]:	/3DP/_images/frame_motor.png
[image-2]:	/3DP/_images/blueprint.png
[image-3]:	/3DP/_images/blueprint-exploded.png
[image-4]:	/3DP/_images/DSC00379.jpg
[image-5]:	/3DP/_images/DSC00380.jpg
[image-6]:	/3DP/_images/DSC00381.jpg

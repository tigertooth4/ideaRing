Title: Kossel XL 构建记 (29) ---- The GCode Magic II
Date: 2014-9-25 9:35:00
Tag: 3dp, Kossel, Wiring, Stepper, Motor, GCode
Status: public

抽时间把以前所有的设计组合在一起，画了 Kossel-XL 3DP 的组装完成图

![][img-1] 

以及分解图

![][img-2]

感觉太有成就感了：）！


目前要做的，是赶紧对三个步进电机进行调试，然后加热板的支撑部分也应该考虑了。由于之前电源部分的尺寸稍差（调整起来费事），所以不得不把支撑部分垫高一点，以防
电源盒子的散热部分被加热板挡住。好吧，今晚可以动手绘制加热板的支撑部分了！


以下内容可以参考 [builda3dprinter][1]
## 风扇的接线
需要一直吹的有 hotend 以及 电路部分（？）的风扇。这里由于空间并不充裕，我用的是 25x25mm 的小风扇，依
然是 12V 的电压。风扇有三种可能的接法：

1. 接在供电接口上，这样的话一开机风扇就会一直转。这个接口我想用来接电路部分的散热风扇，以及电源的散
   热风扇；
2. 接在 Ramps 板子第一个 A4988 左侧的那个 12V 辅助输入口，同样，开机以后风扇也会转，因此这个口看来是
接热头风扇的首选接口；
3. Ramps 板子的 D9 接口，这个接口的风扇转速可以调整，因此非常适合吹打印件。


## 其它接口的设置

1. D10 -- 接热头 (hot-end)
2. D8  -- 接热床 (heated bed)

以上网页上交待说风扇要用 G-Code "M106 SXXX" 打开， XXX 是 0-255 之间的一个值，这个还需要再尝试才能确
定；要想关闭风扇，可以用 M106 S0


[1]:        http://www.builda3dprinter.eu/build-manuals/kossel_mini_build_manual/calibration-2/




[img-1]:	/3DP/_images/assemble.png
[img-2]:	/3DP/_images/assembleExpose.png

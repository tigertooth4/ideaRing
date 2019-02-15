Title: Today's random log

Date: 2012-11-19 13:13:56

[mathjax]

# 铁磁流体

[caption id="" align="aligncenter" width="952"]![](http://upload.wikimedia.org/wikipedia/commons/2/21/Ferrofluid_Magnet_under_glass_edit.jpg "Ferrofluid") Ferrofluid( 铁磁流体, Picture from wikipedia）[/caption]

奇妙的是，这东西竟然在磁场下呈现出这样诡异的形状，考虑到黑色部分是液体，当晃动整个系统时，黑色部分还能呈现出果冻般抖动的效果。

more

见[Synchronized Ferrofluid Sculptures](http://www.youtube.com/watch?v=WXvar-4M6VA)

[Mind blowing Ferrofluid sculpture](http://www.youtube.com/watch?v=qlqHosE4LZY&amp;feature=channel&amp;list=UL)

[这里](http://en.wikipedia.org/wiki/Ferrofluid)是维基百科的解释。

# 留数计算

这三天来一直在想一个问题，如何计算如下留数

\[\sum_{i=1}^r\mathrm{Res}_{\eta=z_i}\frac1{(\eta-p)(\bar\eta^r-\eta^r)}\left[\frac{d}{d\eta}\hat\xi_{d_1}^{(r),k_1}(\eta)\cdot \hat\xi_{d_2+1}^{(r),k_2}(\bar\eta)+

\hat\xi_{d_1+1}^{(r),k_1}(\bar\eta)\cdot \frac{d}{d\eta} \hat\xi_{d_2}^{(r),k_2}(\eta)\right]d\eta

\]

其中\(\hat\xi_{n+1}^{(r),k}(\eta) = \frac{\eta}{1-\eta^r}\frac{d}{d\eta}\hat\xi_{n}^{(r),k}(\eta)\), 最终形式是一个有理多项式，分母部分为 \((1-\eta^r)^{2n+1}\)，而分子部分是一个次数小于分母的多项式，\(r\)是自然数；\(z_i\)是单位根，满足\(1-\eta^r=0\)的第i个零点；\(\bar\eta\)是在\(z_i\)附近满足方程 \(\bar\eta e^{-\bar\eta^r/r}=\eta e^{-\eta^r/r}\)却不等于\(\eta\)的另一个解，称之为\(\eta\)的 deck transformation. \(\bar\eta\) 可以在 \(z_i\) 附近展开成 \(\eta\) 的 Taylor 级数，我们用 \(\bar\eta = S_i(\eta)\) 表示.

此问题的难点在于

*   \(\bar\eta\) 没有显示表示，并且只在\(z_i\)附近能够写成\(\eta\)的解析函数

但是我们尝试了一个更简单的留数计算问题，得到了如下结果

**引理1** 当多项式\(f(x)\)的次数小于\(n r\)时，我们有如下留数公式\[\sum_{i=1}^r \mathrm{Res}_{z_i} \frac{f(\eta)}{(\eta-p)(1-\eta^r)^n}d\eta = - \frac{f(p)}{(1-p^r)^n}.\]

证明思路是考虑下图中围道积分：

[caption id="attachment_386" align="aligncenter" width="300"][![](http://www.xjliu.net/blog/wp-content/uploads/2012/11/屏幕快照-2012-11-18-下午9.19.41-300x232.png "屏幕快照 2012-11-18 下午9.19.41")](http://www.xjliu.net/blog/wp-content/uploads/2012/11/屏幕快照-2012-11-18-下午9.19.41.png) 围道积分[/caption]

在\(z_i\) 处的留数和加上在\(p\)处的留数等于在\(\Gamma\)上的围道积分，当围道半径趋于无穷时，围道积分趋于零.

问题：** **当 \(f(x)\) 为 \(x\) 的解析函数时，此时上述积分等于多少？

#  [Leap Motion](https://leapmotion.com)

[caption id="attachment_383" align="aligncenter" width="300"][![](http://www.xjliu.net/blog/wp-content/uploads/2012/11/laptop_detail-8325bc2fc927a09cf6c554cf47956ba6-300x124.jpg "laptop_detail-8325bc2fc927a09cf6c554cf47956ba6")](http://www.xjliu.net/blog/wp-content/uploads/2012/11/laptop_detail-8325bc2fc927a09cf6c554cf47956ba6.jpg) From LeapMotion.com[/caption]

太牛了，啥也不说了，请看上述网站的视频。这个东东的应用很广啊，以后可以用双手演示怎样将一个几何对象形变成另一个了！$70，现在可以预订！
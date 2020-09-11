---
title: Weierstrass 逼近定理的证明
date: '2020-09-07T18:02:00+08:00'
draft: false
tags: ["Weierstrass", "Approximation","Theorem","Math"]

---

为准备一个比赛，第一次较为细致地了解了一下 Weierstrass 逼近定理。本文将介绍一下该定理的内容，以及两种证明方法，其中一种是 Weierstrass 本人给出的，另一种也许是俄罗斯数学家 Bernstein 给出的。

----

## 一、逼近定理

Weierstrass 逼近定理考虑了有界闭区间上的连续函数的一致逼近问题，它的一种陈述形式是：

**考虑任意一个定义在 $[a,b]$ 区间上的连续函数 $f$， 则对于任意 $\varepsilon>0$，都会存在一个多项式 $p(x)$，使得 $|f(x)-p(x)|<\varepsilon$ 对于任意区间 $[a,b]$ 中的点 $x$ 都成立。**

也就是说，定义在 $[a,b]$ 区间上的多项式构成的集合，在 $C([a,b])$ 中稠密！

Weierstrass 逼近定理是德国数学家 Weierstrass 在 1885 年 70岁时完成的。事实上，我们刚才陈述的，是其第一逼近定理，第二逼近定理是关于连续周期函数的三角多项式逼近的。

这个定理有许多种证明方法，其中为我们所熟知的有 Bernstein 的证明、以及 Weierstrass 本人的证明等。事实上，Lebesgue 也给出过他的证明，而且这个证明是 Lebesgue 本人的第一篇论文[^1]

----

## 二、 Weierstrass 本人的证明

以下，我们将先给出 Weierstrass 本人的证明。

### 1. 关键引理

Weierstrass 考虑了 $f$ 与 Gauss 核函数的卷积
$$
F(h,x) := \frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{+\infty} f(u)\exp\left(-\left(\frac{u-x}{h}\right)^2\right) \mathrm{d}u.\tag{1}
$$
他发现，**若 $f$ 在 $\mathbb{R}$ 上有界且一致连续，则 $F(h,x)$ 将随 $h\to 0^+$ 而在 $\mathbb{R}$ 上一致收敛到 $f$ ！** 而且，他立刻注意到这样的结果也可以推广到一般的非负连续且广义可积的偶的核函数 $\psi$，也就是说，对于一般的核函数 $\psi$，有
$$
F(h,x):=\frac{1}{h\omega}\int\_{-\infty}^{+\infty}f(u)\psi\left(\frac{u-x}{h}\right)\mathrm{d}u
$$
当 $h\to 0^+$ 时在 $\mathbb{R}$ 上一致收敛到 $f$，其中 $\omega:= \int_{-\infty}^{+\infty}\psi(u)\mathrm{d}u$.

粗体部分的结论是证明多项式逼近的重要一步，它的证明其实是使用非常标准的分析套路。让我们来比较 $F(h,x)$ 与 $f(x)$，方法就是看差的绝对值 $|F(h,x)-f(x)|$。 注意到 $(1)$ 式中若去掉 $f(u)$ 做积分的话，这个积分的值为 $1$。因此，

$$|F(h,x)-f(x)|\leq \frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{+\infty}|f(u)-f(x)|\exp\left(-\left(\frac{u-x}{h}\right)^2\right) \mathrm{d}u.$$

在上式中，当 $u$ 和 $x$ 比较接近时，我们使用一致连续性，可以控制 $|f(u)-f(x)|$ 使之很小；而当 $u$ 和 $x$ 相去甚远时，我们可以利用 Gauss 核函数的积分值很小的性质。注意到 
$$
\begin{align}
&\frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{+\infty}\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u\\\\\\
=&\frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{+\infty}\exp\left(-\left(\frac{v}{h}\right)^2\right)\mathrm{d}v\\\\\\
=&\frac{1}{\sqrt{\pi}}\int\_{-\infty}^{+\infty}\exp\left(-w^2\right)\mathrm{d}w\\\\\\
=&1.
\end{align}
$$
因此，对于任意 $\varepsilon>0$，都存在 $k>0$，使得 $$\frac{1}{\sqrt{\pi}}\int\_{-\infty}^{-k} + \int\_{k}^{+\infty} \exp(-w^2)\mathrm{d}w<\varepsilon.$$ 也就是说，当 $|u-x|\geq k h$ 的时候，就有 $$\frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{x-kh}+\int\_{x+kh}^{+\infty}\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u<\varepsilon.$$ 

而由一致连续性质，对于任意 $\varepsilon>0$，都存在 $\delta>0$，使得当 $|u-x|<\delta$ 的时候，就有 $|f(u)-f(x)|<\varepsilon/2$。而假设 $f$ 绝对值的界为 $M$，就存在 $k>0$，使得

$$\frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{x-kh}+\int\_{x+kh}^{+\infty}\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u<\frac{\varepsilon}{4M}.$$

综合上述结论，只要使 $h<h_0 = \frac{\delta}{k}$，就有
$$
\begin{align}
&\frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{+\infty}|f(u)-f(x)|\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u\\\\\\
\leq&\frac{1}{h\sqrt{\pi}}\int\_{x-kh}^{x+kh}\frac{\varepsilon}{2}\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u + \frac{1}{h\sqrt{\pi}}\int\_{-\infty}^{x-kh} + \int\_{x+kh}^{+\infty}2M\exp\left(-\left(\frac{u-x}{h}\right)^2\right)\mathrm{d}u\\\\\\
\leq& \varepsilon.
\end{align}
$$


### 2. 连续函数的延拓和逼近多项式的构造

为了利用上节中引理的结论，在考虑 $[a,b]$ 区间上的连续函数 $f$ 时，我们要对它进行延拓，使得它成为 $\mathbb{R}$ 上定义的有界、一致连续函数 $\tilde{f}$。这样的延拓有多种方式，比如，我们可以首先拓展函数 $f$ 的定义域到 $[a-1,b+1]$，使得它在 $[a-1,a]$ 及 $[b,b+1]$ 两端区间上都从端点值直线衰减至 $0$，然后在 $[a-1,b+1]$ 之外进行 $0$-延拓。这样，显然得到的是一个 $\mathbb{R}$ 上定义的有界且一致连续的函数。且实际上这个函数的支集仅在 $[a-1,b+1]$ 这段区间。

接下来，我们利用上节的知识，先构造 $\tilde{f}$ 的积分逼近 $F(h,x)$，然后再考虑如何对积分 $F(h,x)$ 进行多项式逼近。 

首先，对于任意 $\varepsilon>0$，都会存在 $h_0>0$，使得 
$$
|\tilde{f}(x)-F(h_0,x)|<\varepsilon/2,\quad \forall \; x\in\mathbb{R}.
$$
然后，考虑 $F(h_0,x)$ 的定义，我们知道，对高斯核函数部分，可以使用 Taylor （麦克劳林）多项式进行逼近，并且，若考察的是有限区间，这一逼近可以为一致逼近。即，对任意区间 $[-R,R]$，对于任意 $\varepsilon>0$，存在 $N>0$，使得
$$
\left|\exp\left(-\left(\frac{u-x}{h_0}\right)^2\right)-\sum\_{k=0}^N \frac{(-1)^k (u-x)^{2k}}{k! \;h_0^{2k}}\right|<\varepsilon/{4M},\quad \forall \; u-x\in[-R,R].
$$
所以
$$
\left|F(h_0,x)-\sum\_{k=0}^N \int\_{-R}^R \tilde{f}(u) \frac{(-1)^k(u-x)^{2k}}{k! \; h_0^{2k}}\mathrm{d}u\right|<\varepsilon/2.
$$
而后面这个积分是一个关于 $x$ 的多项式。这样就证明了逼近定理。

----

## 三、Bernstein 的证明

 Bernstein 的证明出现在1912/13年。他的证明与众不同，对后来的很多领域也产生了深刻的影响。为讲述他的证明，首先让我们来定义 Bernstein 基，第 $(n,i)$ 个Bernstein 基实际上就是 $(x + 1-x)^n$ 的展开式的第 $i$ 项，即
$$
B\_{n,i}(x)= \binom{n}{i} x^i (1-x)^{n-i}.
$$
因此，根据二项式展开定理，很显然有 
$$
\sum\_{i=0}^n B\_{n,i}(x)\equiv 1.
$$
同时，也显然有 $B\_{n,i}(x)$ 是非负函数，所以 $\{B\_{n,i}(x)\}\_i$ 构成了一组单位分解。为了证明任意 $[a,b]$ 区间上的连续函数可用多项式函数一致逼近，不妨考虑 $f$ 是 $[0,1]$ 区间上的连续函数。这时，由 Cantor 定理，$f$ 在 $[0,1]$ 上一致连续。故对于任意 $\varepsilon>0$，一定存在 $\delta>0$，使得当 $|x-y|<\delta$ 时，$|f(x)-f(y)|<\varepsilon/2$。

下面，对于此 $\delta>0$，我们可以定义两个与 $f$ 相关的函数：
$$
\underline{f}\_\delta(x):=\min\\\{f(y)\;|\; y\in[x-\delta, x+\delta]\,\cap\,[0,1]\\\}
$$

$$
\overline{f}\_\delta(x):=\max\\\{f(y)\;|\; y\in[x-\delta,x+\delta]\,\cap\,[0,1]\\\}
$$

则由定义和一致连续性，显然有
$$
f(x)-\varepsilon/2\le \underline{f}\_\delta(x)\le f \le \overline{f}\_\delta(x)\le f(x)+\varepsilon/2.
$$
我们再定义一个函数
$$
\eta\_n(x):=\sum_{i\;:\;|x-i/n|>\delta}\binom{n}{i}x^i(1-x)^{n-i}.
$$
则显然
$$
1-\eta\_n(x) = \sum\_{i\;:\;|x-i/n|\leq\delta}\binom{n}{i}x^i(1-x)^{n-i}.
$$
关于 $\eta\_n(x)$ 的一个不显然的性质是，当 $n$ 充分大时，总有
$$
\eta\_n(x)\leq \frac{\varepsilon}{4||f||},\quad ||f|| := \max |f(x)|.
$$
现在，我们构造 $f$ 所对应的 Bernstein 多项式，为
$$
B\_n(x) = \sum\_{i=0}^n f\left(\frac{i}{n}\right) B\_{n,i}(x)= \sum\_{i=0}^n f\left(\frac{i}{n}\right)\binom{n}{i}x^i (1-x)^{n-i}.
$$
则若将求和分成两部分：$|x-i/n|\le \delta$ 和 $|x-i/n|>\delta$，则有
$$
\underline{f}\_\delta(x)(1-\eta\_n(x)) - ||f||\eta\_n(x)\le B\_n(x)\le \overline{f}\_\delta(x)(1-\eta\_n(x)) + ||f||\eta\_n(x)
$$
即
$$
f(x) + (\underline{f}\_\delta(x) - f(x)) - \eta\_n(x)(\underline{f}+||f||)\le B\_n(x)\le f(x) + (\overline{f}\_\delta(x)-f(x)) + \eta\_n(x)(||f||-\overline{f}\_\delta(x))
$$
上面的不等式可进一步简化为
$$
f(x)-\varepsilon/2 -2\eta\_n(x)||f||\le B\_n(x)\le f(x)+\varepsilon/2 + 2\eta\_n(x)||f||.
$$
下面，我们断言，当 $n$ 充分大时，一定有
$$
\eta\_n(x)\le \frac{\varepsilon}{4||f||},\quad f\not\equiv 0,
$$
我们实际上就证明了
$$
｜f(x)-B\_n(x)|\le \varepsilon.
$$

----

### 断言的证明

最后，我们只需要证明刚才的断言：
$$
\eta\_n(x)\le \frac{\varepsilon}{4||f||},\quad f\not\equiv 0,
$$

注意到
$$
\begin{aligned}
\eta\_n(x) &= \sum\_{\\\{i\;:\;|x-i/n|\ge\delta\\\}} \binom{n}{i}x^i (1-x)^{n-i}\\\\\\
&\le \sum\_{\\\{i\;:\;|x-i/n|\ge \delta \\\}}\frac{(x-i/n)^2}{\delta^2}\binom{n}{i}x^i (1-x)^{n-i}\\\\\\
&\le \frac{1}{\delta^2}\sum\_{i=0}^n \left(x-i/n\right)^2\binom{n}{i}x^i (1-x)^{n-i}\\\\\\
&= \frac{1}{\delta^2}\sum\_{i=0}^n \left(x^2-2 x \frac{i}{n} + \frac{i^2}{n^2}\right)\binom{n}{i}x^i(1-x)^{n-i}\\\\\\
&= \frac{x^2}{\delta^2}-\frac{2x^2}{\delta^2}\sum\_{i=1}^n\binom{n-1}{i-1}x^{i-1}(1-x)^{n-i}\\\\\\
&\quad+\frac{1}{n\delta^2}\left(\sum\_{i=2}^n \frac{(n-1)!}{(i-2)!(n-i)!}x^i(1-x)^{n-i}+\sum\_{i=1}^n\binom{n-1}{i-1}x^{i}(1-x)^{n-i}\right)\\\\\\
&=\frac{x(1-x)}{n\delta^2}\le \frac{1}{4n\delta^2}.
\end{aligned}
$$
所以，只要将 $n$ 取得充分大，就可以使 $\eta\_n(x)\le \frac{\varepsilon}{4||f||}$。										
						

[^1]: 参考 Allan Pinkus, *Weierstrass and Approximation Theory*, Journal of Approximation Theory, 107(1), 1-66, 2000.
---
title: "Galois理论：一篇粗浅的介绍"
date: 2019-04-20T23:06:35+08:00
draft: false
tags: ["Galois","Math","AlgebraicEquations","Sqrt","Symmetry"]
---

之前为了讲通识课，精心准备了一个名为「在不可能与显然之间」的报告。报告的内容选取了数学中的一些事例，来说明数学为什么有趣，为什么令人惊叹。其中引用了前苏联数学家 Andrei Kolmogorov 的一句

> Mathematics occurs on the boundary between the obvious and the impossible.

其实，这句话也是这个报告标题的灵感来源。

在报告中，我选取的其中一个实例就是 Galois 关于高次代数方程（次数大于等于5）时没有根式解法的证明，用以说明伟大的思想确实可以把不可能变成显然。之所以选这个实例，也是因为自己从没对 Galois 的思想有过大致的了解。想借这个机会好好了解一下。

为了不会以后忘却，趁着报告过去的时间不长，我觉得还是有必要把当时讲的内容记录一下。

所以，我们将要考虑的问题是如下代数方程：
$$
x^n+a_{n-1}x^{n-1}+\cdots + a_1 x + a_0 = 0
$$
的解能否通过对系数 $a_i$ 进行有限次四则运算和开方运算表示出来? 让我们来先看几个例子。

# 二次代数方程的情况

我们中学的时候都学过，二次代数方程 
$$
x^2+a_1 x + a_0 = 0
$$

的解是可以这样表示出来的: 
$$
x_{1,2}=\frac{-a_1\pm \sqrt{a_1^2-4a_0}}{2}
$$

# 三次代数方程的情况

对于三次多项式
$$
x^3+a_2 x^2 + a_1 x + a_0 = 0
$$
来说，其求根公式也可以用如下的方法给出：

- 首先通过变量替换 $z=x-\frac{a_2}{3}$ 消去二次项，得到如下标准形式的三次多项式
  $$
  z^3 + \frac{3a_1-a_2^2}{3} z - \frac{9a_1 a_2-27 a_0 - 2a_2^3}{27}=0
  $$
  

  即如下形式 
  $$
  z^3+pz = q.
  $$
  
- 利用伟达变换 $z=w-\frac{p}{3w}$ 将上述方程变成二次方程:
  $$
  (w^3)^2 - q(w^3) - \frac1{27}p^3=0.
  $$
  从而可以解出 w
  $$
  w = \sqrt[3]{\frac12 q \pm \sqrt{\frac14 q^2 + \frac1{27} p^3}}
  $$

- 最后反解出 z 以及 x.

对于四次代数方程，也有相应的求根公式（由 Ferrari 提出，后发表在 Cardano 的 Ars Magna (1545))。

# 五次及以上的代数方程，为何不存在一般的根式解法？

Galois 的想法是这样的[^stillwell]。假设 $n\geq5$ 次的方程写成
$$
x^n + a_{n-1}x^{n-1} + \cdots + a_1 x + a_0 = 0
$$
设其所有的解为 $x_1,x_2,\cdots, x_n$，则
$$
x^n + a_{n-1}x^{n-1}+\cdots + a_1 x + a_0 = (x-x_1)(x-x_2)\cdots (x-x_n)=0
$$
注意到，上式说明 $a_0, a_1,\cdots, a_n$ 实际上都是 $x_1,x_2,\cdots, x_n$ 的对称多项式
$$
\begin{align}
a_{n-1} &= - (x_1 + x_2 + \cdots + x_n)\\
a_{n-2} &= \sum_{i\neq j} x_i x_j\\
\vdots\quad &= \quad\quad\vdots\\
a_0 &= \pm x_1 x_2 \cdots x_n
\end{align}
$$
因此，若将置换群 $S_n$ 作用在方程的根上，系数 $a_0,a_1,\cdots,a_{n-1}$ 应保持不变。现在，假设所有的解都可以用系数 $a_0,a_1,a_2,\cdots,a_{n-1}$ 的<u>四则运算</u>和<u>根式</u>表达出来。我们

- 记 $\mathbb{Q}(a_0,\cdots,a_{n-1})$ 为对系数 $a_i$ 进行<u>四则运算</u>能够得到的所有数构成的集合（这个集合会对加减乘除封闭，数学上，我们把这样的集合称为一个<u>域</u>。
- 记 $\mathbb{Q}(x_1,\cdots,x_n)$ 为对方程的所有根进行<u>四则运算</u>能够得到的数的集合（也是一个域）。
- 记 $E$ 为对系数 $a_i$ 及其<u>必要的根式</u>进行四则运算能够得到的数的集合（域）。
- 记 $\overline{E}$ 为对 $E$ 中元素再进行下标的置换能够得到的所有数所构成的集合（域）。

例如：对二次多项式 $x^2 + a_1 x + a_0 = 0$，
$$
E = \mathbb{Q}(a_1,a_2,\sqrt{a_1^2-4a_0}), \quad \overline{E} = \mathbb{Q}(a_1,a_2,\sqrt{a_1^2-4a_0},\sqrt{a_0^2-4a_1}).
$$
事实上，$E$ 中已经包含了 $x_1,x_2$：$x_{1,2}=\frac12 a_1 \pm \frac12 \sqrt{a_1^2-4a_0}$. 

若所有的解都能用系数表达，那么我们可以得到如下包含关系
$$
B:=\mathbb{Q}(a_0,\cdots,a_{n-1}) \subset \mathbb{Q}(x_1,\cdots,x_n)\subset E\subset \overline{E}
$$
注意，第二个包含关系成立是由假设条件推出的。第二点要注意的是，在根的置换操作（群 $S_n$ 的作用下），$B$ 和 $\overline{E}$ 是保持不变的。我们定义所有保持 $B$ 不变的 $\overline{E}$ 的操作构成一个群，记为 
$$
\mathrm{Gal}\left(\overline{E}/B\right)
$$
则显然应该有 $S_n\subset \mathrm{Gal}\left(\overline{E}/B\right)$.  

不巧的是， $\mathrm{Gal}\left(\overline{E}/B\right)$ 是一个可解群（即这些操作可以通过对依次添加进来的新的根式进行置换而得到），而当 $n\geq5$ 时，$S_n$ 不是可解群，从而产生了矛盾！

# 结论

简而言之，对称性是解决高次代数方程求根问题的关键，Galois 正是洞察到了这一点！

[^stillwell]: Stillwell, Galois theory for beginners.
---
title: "导函数是否一定黎曼可积？"
date: 2022-05-08T11:59:11+08:00
draft: false
tags: ["knowledge", "math", "teach", "differentiable", "non-integrable", "Riemann","教学感悟","数学分析","studies"]
---

本文来自一个学生的提问。

当时想了想，预感有这样的处处可导，但导函数又不黎曼可积的函数，可不知如何构造。若不要求导函数有界，则有很多例子，但若考虑导函数要有界，这样的反例至少当时没有想出来。上网搜索后，发现反例已经有非常经典的构造了，称为 Volterra 函数。根据 [知乎](https://www.zhihu.com/question/47546046) 上的一个提问，这个函数在 邓纳姆 所著的《微积分的历程》中有提到，是 Volterra 在青年时期发现的一个“不符合微积分基本定理”的病态函数。它是处处可导的有界函数，但导函数并不是黎曼可积函数。关于反例的讨论可见 stackexchange [1]。关于 Volterra 函数的具体介绍，可参见 [2] 。为便于今后参考，本文将在阅读了相关文献的基础上，对 Volterra 函数的构造过程做一个稍具体的描述。

# Smith-Volterra-Cantor 集

反例的构造需要用到 Smith-Volterra-Cantor (SVC) 集 [3]，它的构造非常类似于 Cantor 三分集，只是改变了每次移除的区间的长度。

考虑 $[0,1]$ 区间 

1. 第一步，移除以区间中点 $\frac12$ 为中心，长度为 $1/4$ 的开区间 $(\frac38,\frac58)$ (见下图)；
2. 第二步，对于剩下的两个闭区间，以它们的中点为心，各移除一个长度为 $1/4^2$ 的两个开区间；
3. 第三步，对剩下的四个闭区间，以它们的中点为心，各移除一个长度为 $1/4^3$ 的四个开区间;

等等等.

![24A6A84C-4F63-4BE3-98E0-D9D6C6D32869.jpeg](%E5%AF%BC%E5%87%BD%E6%95%B0%E6%98%AF%E5%90%A6%E4%B8%80%E5%AE%9A%E9%BB%8E%E6%9B%BC%E5%8F%AF%E7%A7%AF%EF%BC%9F%20bc31c391d72d4b81b2ed49d24ec65990/24A6A84C-4F63-4BE3-98E0-D9D6C6D32869.jpeg)

这样，最后剩下的闭集，就称为 SVC 集。显然可以发现，SVC 集的总长度为 

$$
1-\left(\frac14 + \frac{2}{4^2} + \frac{4}{4^3} + \cdots\right) = \frac12 \neq 0.
$$

且其余集稠密（$[0,1]$ 的任何子区间当中都含有不在 SVC 集合中的点）。

# Volterra 函数的构造

利用 SVC 集，我们可以构造 $[0,1]$ 上一个分段定义的函数，使得这个函数在 SVC 集的余集上不恒为零。具体构造过程如下：

1. 考虑一个在$[0,\frac14]$上不恒为零，但在此区间外处处为 $0$ 的函数 $f_1(x)$。在前半个区间 $[0,\frac18]$ 上先找到 $x^2\sin\frac1x$ 导函数的最大零点 $z_1$，定义$f_1(x)$ 在 $[0,z_1]$ 的值与函数 $x^2\sin\frac{1}{x}$相同，而在 $[z_1,\frac18]$ 上定义 $f_1(x)$ 的值恒为 $z_1^2\sin\frac1{z_1}$。再令函数 $f_1(x)$ 在 $[\frac18,\frac14]$ 的图像与它在 $[0,\frac18]$ 的图像对称，即
  
    $$
    f_1(x):=
    \begin{cases}x^2 \sin\frac1x, & x\in[0,z_1)\\ 
    z_1^2 \sin\frac1{z_1}, &x\in[z_1,\frac18)\\ 
    z_1^2\sin\frac1{z_1}, & x\in[\frac18,\frac14-z_1)\\ 
    (\frac14-x)^2\sin\frac1{\frac14-x}, & x\in[\frac14-z_1,\frac14]\\ 
    0, & \text{otherwise.}\end{cases}
    $$
    
    现在，我们将 $f_1(x)$ 的函数图像向右平移 $3/8$ 个单位，得到一个在 $[\frac38,\frac58]$ 上不恒为零，但在此区间之外恒为零的函数 $f_1(x-\frac38)$.
    
2. 考虑一个在$[0,\frac1{4^2}]$上不恒为零，但在此区间外处处为 $0$ 的函数 $f_2(x)$。在前半个区间 $[0,\frac1{2\cdot 4^2}]$ 上先找到 $x^2\sin\frac1x$ 导函数的最大零点 $z_2$，定义$f_2(x)$ 在 $[0,z_2]$ 的值与函数 $x^2\sin\frac{1}{x}$相同，而在 $[z_2,\frac1{2\cdot 4^2}]$ 上定义 $f_2(x)$ 的值恒为 $z_2^2\sin\frac1{z_2}$。再令函数 $f_2(x)$ 在 $[\frac1{2\cdot 4^2},\frac1{4^2}]$ 的图像与它在 $[0,\frac1{2\cdot 4^2}]$ 的图像对称，即
  
    $$
    f_2(x):=\begin{cases}x^2 \sin\frac1x, & x\in[0,z_2)\\ z_2^2 \sin\frac1{z_2}, &x\in[z_2,\frac1{2\cdot 4^2})\\ z_2^2\sin\frac1{z_2}, & x\in[\frac1{2\cdot 4^2},\frac1{4^2}-z_2)\\ (\frac1{4^2}-x)^2\sin\frac1{\frac1{4^2}-x}, & x\in[\frac1{4^2}-z_2,\frac1{4^2}]\\ 0, & \text{otherwise.}\end{cases}
    $$
    
    现在，我们将 $f_2(x)$ 的函数图像分别向右平移 $\frac5{32}$ 和 $\frac{25}{32}$ 个单位，得到一个在 $[\frac5{32},\frac7{32}]$ 和 $[\frac{25}{32},\frac{27}{32}]$ 上不恒为零，但在两区间之外恒为零的函数 。
    
3. 重复上述构造过程。
4. 最后，将构造得到的所有分段函数相加，就得到了 Volterra 函数，记为 $V(x)$。它的图像如下图所示。

![Untitled](%E5%AF%BC%E5%87%BD%E6%95%B0%E6%98%AF%E5%90%A6%E4%B8%80%E5%AE%9A%E9%BB%8E%E6%9B%BC%E5%8F%AF%E7%A7%AF%EF%BC%9F%20bc31c391d72d4b81b2ed49d24ec65990/Untitled.png)

# Volterra 函数的性质

## Volterra 函数的可导性

由 Volterra 函数的构造过程，参考最终得到的函数图像，我们可以看到在 Volterra 函数是处处可导的（在 $x=0$ 时，$x^2\sin\frac1x$ 为 $x$ 的二阶无穷小量，因此可导；在 $x\neq 0$ 时，函数根据乘积函数的求导法则知显然可导）。在 $z_1$, $z_2$ 等等导函数的零点处，左右导数显然均为 $0$, 因此可导。故 Volterra 函数是处处可导的。

但是，$x^2\sin\frac1x$ 的导函数 $2x\sin\frac1x - \cos(\frac1x)$ 在 $x\to 0$ 无极限，且振幅等于2。

## Volterra 函数其导函数在 $[0,1]$的 Riemann 不可积性

首先，容易看出 V’(x) 处处有界。但是，由 SVC 余集的稠密性，$[0,1]$ 区间的任何一个子区间总含有SVC 余集中的点。因此，在任何子区间上，V’(x) 的振幅都等于 $2$， 所以V’(x)在 $[0,1]$ 上为黎曼不可积函数。下图为 Volterra 函数的导函数图像。

![Untitled](%E5%AF%BC%E5%87%BD%E6%95%B0%E6%98%AF%E5%90%A6%E4%B8%80%E5%AE%9A%E9%BB%8E%E6%9B%BC%E5%8F%AF%E7%A7%AF%EF%BC%9F%20bc31c391d72d4b81b2ed49d24ec65990/Untitled%201.png)

# 生成 Volterra 函数的 Mathematica 代码

扫描以下二维码，或点击 [这里](https://www.wolframcloud.com/obj/tigertooth4/Published/Volterra%20Function.nb)，查看 Mathematica 代码。

![Untitled](%E5%AF%BC%E5%87%BD%E6%95%B0%E6%98%AF%E5%90%A6%E4%B8%80%E5%AE%9A%E9%BB%8E%E6%9B%BC%E5%8F%AF%E7%A7%AF%EF%BC%9F%20bc31c391d72d4b81b2ed49d24ec65990/Untitled%202.png)

# 参考文献

[1] [What is an example that a function is differentiable but derivative is not Riemann integrable](https://math.stackexchange.com/questions/257069/what-is-an-example-that-a-function-is-differentiable-but-derivative-is-not-riema)

[2] [Wrestling with the fundamental theorem of calculus](https://www.macalester.edu/~bressoud/talks/AlleghenyCollege/Wrestling.pdf)

[3] [Smith-Volterra-Cantor set - Wikipedia](https://en.wikipedia.org/wiki/Smith%E2%80%93Volterra%E2%80%93Cantor_set)
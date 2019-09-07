---
title: "Weyl 的 equidistribution 定理与数项级数的收敛性"
date: 2019-07-31-T23:28:55+08:00
draft: true
---
在数学分析中有很多习题是关于数项级数的收敛性的。也有很多关于收敛性的判别方法。在这些判别法中，对于一般项级数的判别方法，一般的教材中会介绍绝对收敛，交错级数的 Leibniz 判别法和 Abel-Dirichlet 判别法等。那么是不是一般项级数用这些判别法就一定能判断收敛性了呢？有没有使用这些判别法也无法判断的级数呢？

这样的级数当然存在，比如我们来看如下级数：\\( \sum_{n=1}^\infty \frac{(-1)^n \sin(n)}{n}\\)。

分部求和公式
$$\sum_{k=m}^{n-1} a_{k+1} (b_{k+1}-b_k) + \sum_{k=m}^{n-1} b_k(a_{k+1}-a_k) = a_n b_n - a_m b_m$$

Weyl equidistribution 定理
$$\frac1{n} \sum_{k=1}^n f(\alpha k \mod 1)=\int_0^1 f(x) dx$$

利用分部求和公式和 Weyl 的结论，我们可以估计级数 \\( \sum_{n=1}^\infty \frac{(-1)^n \sin(n)}{n}\\) 的部分和 (设 \\(\sum_{k=1}^n |\sin(k)| = S_n\\) )
$$\sum_{k=1}^{n} \frac{(-1)^n}{n}|\sin(n)| = \frac{(-1)^n}{n} S_n+ |\sin(1)| -\sum_{k=1}^n S_{k}(-1)^k \frac{2k-1}{k(k-1)}$$
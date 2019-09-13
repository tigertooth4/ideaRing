---
title: Weyl 的等分布定理与数项级数的收敛性
date: '2019-07-31T23:28:55+08:00'
draft: true
tags: ["Weyl","Series","Abel-Dirichlet","convergence", "equidistribution"]
---
在数学分析中有很多习题是关于数项级数的收敛性的。也有很多关于收敛性的判别方法。在这些判别法中，对于一般项级数的判别方法，一般的教材中会介绍绝对收敛，交错级数的 Leibniz 判别法和 Abel-Dirichlet 判别法等。那么是不是一般项级数用这些判别法就一定能判断收敛性了呢？有没有使用这些判别法也无法判断的级数呢？

这样的级数当然存在，比如我们来看如下级数：$ \sum_{n=1}^\infty \frac{(-1)^n |\sin(n)|}{n}$ 。若用教材中常见的方法去判断，会发现无论是 Leibniz 判别法，还是 Abel-Dirichlet 判别法都会失效，原因是 $\frac{|\sin(n)|}{n}$ 的单调性无法判断。那么，这个级数的收敛性就无法判断了吗？

这个问题困扰了我很久，一直没有什么思路。直到了解到 Weyl 等分布（Equidistributions) 定理后，我才发现，这个级数的收敛性原来可以用这个定理去判断！那么，什么是 Weyl 等分布定理呢？

# Weyl 等分布定理

或更准确地，应该称为等分布定理，是关于 $a, 2a, 3a, \cdots \quad \mod 1$ 在 $[0,1]$ 区间上均匀分布的定理。这个定理的证明可以追溯到二十世纪初（1909）。它断言，当 $a$ 是无理数时，这个序列模一以后在 $[0,1]$ 区间是均匀分布的。而后，1916年，Weyl 证明了 序列 $a, 2^2 a, 3^2 a,\cdots $ $\mod 1$ 也是均匀分布在 $[0,1]$ 区间上的。1935年，Vinogradov 证明了序列 $p_n a$ （$p_n$ 是第 $n$ 个素数 ) ，模一后也是均匀分布的。

而利用此定理，我们可以得到一个非常有用的结论：

<div>
$$
\lim_{n\to+\infty}\frac{1}{n}\sum_{k=1}^n f((x+ka) \mod 1) =\int_0^1 f(y)dy
$$
</div>

对于几乎所有的 $x$ 和 Lebesgue 可积函数 $f$ 都成立。此定理是由 Khinchin 证明的。



# 分部求和公式

为判断收敛性，我们还需要一些常规“技巧”— 分部求和公式：

<div>
$$
\sum_{k=m}^{n-1} a_{k+1} (b_{k+1}-b_k) + \sum_{k=m}^{n-1} b_k(a_{k+1}-a_k) = a_n b_n - a_m b_m
$$
</div>

# 收敛性的判断

利用分部求和公式和等分布定理，我们可以处理级数 $\sum_{n=1}^\infty \frac{(-1)^n |\sin(n)|}{n}$ 的部分和。

首先设 $\sum_{k=1}^n |\sin(k)| = S_n$，并设 $f(y) = \sin(2\pi y)$。则 $\sin(k) = f(\frac{1}{2\pi}k \mod 1)$。注意 $\frac{1}{2\pi}$ 显然是无理数，因此有 Khinchin 的结论成立：

<div>
$$
\lim_n\frac{S_n}{n} = \lim_n \frac{1}{n}\sum_{k=1}^n |\sin(k)|=\int_0^1 |f(y)| dy = \frac2\pi.
$$
</div>

接下来，利用分部求和公式，我们有

<div>
$$
\sum_{k=1}^{n} \frac{(-1)^k}{k}|\sin(k)| = \frac{(-1)^{n+1}}{n+1} S_n+ S_0 +\sum_{k=1}^{n-1} \frac{S_{k}}{k}(-1)^k \left(\frac{k}{k+2}+\frac{k}{k+1}\right).
$$
</div>

当 $n\to+\infty$ 时，我们会发现上面部分和中的第三项不会收敛，因为第三项求和的通项不会趋于 $0$，所以级数发散。

# 讨论

如果去掉 $\sin(k)$ 外面的绝对值，我们便可以利用 Abel-Dirichlet 定理判断收敛性了！原因是，在级数 

<div>
$$
\sum_{n}\frac{(-1)^n \sin(n)}{n}
$$
</div>

中，$\frac{1}{n}$ 部分是单调递减趋于 0 的；而 $\sum_{n=1}^m(-1)^n\sin(n)$ 有界(可以将 $(-1)^n$ 写为 $\cos(n\pi)$，从而利用三角公式将 $(-1)^n\sin(n)$ 写为 $\frac12 \sin(n(\pi+1)) +\frac12 \sin(n(1-\pi))$，而公差为 $\pi+1$ 的 $\sin$ 的等差数列是有界的。)
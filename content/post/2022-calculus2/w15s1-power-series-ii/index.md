---
title: "W15-S1 Power Series (II)"
draft: false
date: 2022-05-31T15:49:34+08:00
tags: ["power series", "radius", "ratio test", "convergence", " Taylor series", "Maclaurin", "term-by-term differntiation", "term-by-term integration", "multiplication"]
---

周次: 15
日期: June 1, 2022
节次: 1

In this lecture, we will continue the discussions on the power series. A radius of convergence of a power series is emerging from the ratio test for the absolute convergence. We will discuss the basic operations, like differentiation and integrations on a power series, and the multiplication of two power series as well. When a power series is convergent, we can express the coefficients by using derivatives of $f(x)$, which generates the series uniquely. Such presentation is called Taylor series, we explore the Taylor series and its partial sum in this lecture as well.

# Outline

### Example 3. Testing for Convergence Using the Ratio Test

For what values of $x$ do the following power series converge? 

1. $\sum_{n\ge 1}(-1)^n\frac{x^n}{n}$ 
2. $\sum_{n\ge 1}(-1)^n \frac{x^{2n-1}}{2n-1}$
3. $\sum_{n\ge 0} \frac{x^n}{n!}$
4. $\sum_{n\ge0}n! x^n$

What’s amazing about the convergence of the power series, is that the domain of convergence is almost symmetric about its center $x=a$. The following theorem discusses this feature.

## Theorem 18. The Convergence Theorem for Power Series

- If the power series $\sum_{n=0}^\infty a_n x^n = a_0 + a_1 x + a_2 x^2 + \cdots$ converges for $x=c\neq 0$, then it **converges absolutely** for all $x$ with $|x|<|c|$.
- If the series diverges for $x=d$, then it diverges for all $x$ with $|x|>|d|.$

**Proof.**

### Example.

If a power series $\sum_n a_n (x-1)^n$ is converging at $x=2$ and diverging at $x=0$, find its domain of convergence.

## The Radius of Convergence of a Power Series

### Corollary to Theorem 18.

The convergence of the series $\sum_n c_n (x-a)^n$ is described by one of the following three possibilities:

1. ($R>0$) There is a positive number $R$ such that the series diverges for $x$ with $|x-a|>R$ but converges absolutely for $x$ with $|x-a|<R$. The series may or may not converge at either of the endpoints $x=a\pm R$.
2. ($R=\infty$) The series converges absolutely for every $x$ .
3. ($R=0$) The series converges only at $x=a$ and diverges elsewhere.

$R$ is called the **radius of convergence** of the power series and the interval of radius $R$ centered at $x=a$ is called the **interval of convergence**. The interval of convergence may be open, closed, or half-open, depending on the particular series. 

At points $x$ with $|x-a|<R$, the series converges absolutely. If the series converges for all values of $x$, we say its **radius of convergence** is infinite. If it converges only at $x=a$, we say its **radius of convergence** is zero.

## How to Test a Power Series for Convergence

1. Find the Radius of Convergence ( by Ratio Test of $n$-th Root Test) to find where the series converges absolutely. Namely, find $(a-R,a+R)$
2. Test the convergence for endpoints (If the radius $R$ is finite) . Usually, the endpoints can be tested by using a Comparison Test, the Integral Test or the Alternating Series Test.
3. Outside of radius of convergence, the power series diverges, because the n-th term does not approach zero for those values of $x$.

# Term-by-Term Differentiation

One aspect showing the power of the power series, is their compatibility with differentiations and integrations.  A power series can be differentiated term-by-term at each interior point of its interval of convergence.

## Theorem 19. The Term-by-Term Differentiation Theorem

If $\sum_{n} c_n(x-a)^n$ converges for $a-R < x < a+ R$ for some $R>0$, in the interval of convergence, the sum $f$ 

$$
f(x) = \sum_{n=0}^\infty c_n(x-a)^n,\quad a-R < x<a+R,
$$

has derivatives of all orders inside the interval of convergence. We can obtain the derivatives by differentiating the original series term by term: 

$$
f'(x) = \sum_{n=1}^\infty n c_n (x-a)^{n-1}\\ f''(x) = \sum_{n=2}^\infty n(n-1) c_n (x-a)^{n-2},
$$

and so on. Each of these derived series converges at every interior point of the interval of convergence of the original series.

### Example 4. Applying Term-by-Term Differentiation

Find series for $f'(x)$  and $f''(x)$ if 

$$
f(x) = \frac1{1-x} = \sum_{n=0}^\infty x^n, \quad -1 < x < 1.
$$

Solution. (Differentiate Term-by-Term)

### Remark.

The term-by-term differentiation provides a way to find the power series expansion for functions like $\frac{1}{(1-x)^2}$ and $\frac{2}{(1-x)^3}$.

### Remark.

Each of the term-by-term differentiated power series has the same radius of convergence. 

### Caution.

The term-by-term differentiation may not work for other kinds of series. For example, the trigonometric series  

$$
\sum_{n=1}^\infty \frac{\sin(n! x)}{n^2}
$$

converges for all $x$. But if we differentiate term-by-term, we get the series

$$
\sum_{n=1}^\infty \frac{n! \cos(n!x)}{n^2}
$$

which diverges for all $x$. This is not a power series.

# Term-by-Term Integration

Another super power for power series is that the integration can be simply done term-by-term.

## Theorem 20. The Term-by-Term Integration Theorem

Suppose that 

$$
f(x) = \sum_{n=0}^\infty c_n (x-a)^n
$$

converges for $a-R < x < a+R$ ($R>0$). Then inside of any sub-interval $[c,d]\subset (a-R, a+R)$ we have 

$$
\int_c^d f(x) dx = \sum_{n=0}^\infty c_n \int_c^d (x-a)^n dx = \sum_{n=0}^\infty \frac{c_n}{n+1}(x-a)^{n+1}\bigg]_{c}^{d}.
$$

In particular , the definite integral of $f(x)$ obtains

$$
\int_a^x f(t) dt = \sum_{n=0}^\infty \frac{c_n}{n+1}(x-a)^{n+1},\quad a-R < x < a+R
$$

or the indefinite integral obtains

$$
\int f(x) dx = \sum_{n=0}^\infty \frac{c_n}{n+1} (x-a)^{n+1} + C,\quad a-R < x < a+R.
$$

### Example 5. A Power Series for $\arctan(x)$, $-1< x < 1$

Identify the function 

$$
f(x) = x - \frac{x^3}{3} + \frac{x^5}{5} - \cdots, \quad -1 \le x \le 1.
$$

Solution. $f(x) = \arctan(x)$ for $-1< x < 1$. 

### Remark.

Evaluating $f(x)$ and $\arctan(x)$ at $x=\frac1{\sqrt3}$ gives a new result for infinite series 

$$
\frac{\pi}{6} = \frac1{\sqrt3} - \frac{1}{3}\frac{1}{\sqrt{3}^3} + \frac1{5}\frac{1}{\sqrt{3}^5} - \cdots = \sum_{n=0}^\infty \frac{(-1)^n}{2n+1}\frac{1}{\sqrt{3}^{2n+1}}
$$

### Notice.

Indeed, the power series $x-\frac{x^3}3 + \frac{x^5}{5}-\cdots$ converges at $x=\pm1$. Later we will prove that $\arctan(x) = x-\frac{x^3}{3} + \frac{x^5}{5} -\cdots$ holds for $x=\pm1$ as well. Which gives a more elegant infinite expansions of $\pi$ 

$$
\frac{\pi}{4} = 1-\frac13 + \frac15 - \frac17 + \cdots
$$

### Example 6. A  Series for $\ln(1+x)$, $-1 < x \le 1$

The series 

$$
\frac1{1+t} = 1-t+t^2-t^3+\cdots
$$

converges on the open interval $-1 < t < 1$. Therefore, 

$$
\ln(1+x)=\int_0^x \frac1{1+t}dt = x-\frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots,\quad -1 < x < 1
$$

### Notice.

Indeed, $\ln(1+x)= x-\frac{x^2}{2} + \frac{x^3}{3}-\frac{x^4}{4} + \cdots$ holds true for $x=1$ as well, which gives the sum for alternating harmonic series 

$$
\ln(2) = 1-\frac12 + \frac13 -\frac14 + \cdots
$$

but we will see it until section 11.10.

# Multiplication of Power Series

## Theorem 21. The Series Multiplication Theorem for Power Series

If $A(x)=\sum_{n=0}^\infty a_n x^n$ and $B(x)=\sum_{n=0}^\infty b_n x^n$ converges absolutely for $|x|<R$ and 

$$
c_n = \text{sum of all the coefficients of $n$-th order terms in the multiplication}\\ =a_0 b_n + a_1 b_{n-1} + a_2 b_{n-2} + \cdots + a_n b_0 = \sum_{k=0}^n a_k b_{n-k} 
$$

then $\sum_{n=0}^\infty c_n x^n$ converges absolutely to $A(x) B(x)$ for $|x|<R$ 

$$
A(x)B(x) = \left(\sum_{n=0}^\infty a_n x^n\right)\cdot \left(\sum_{n=0}^\infty b_n x^n\right) \underbrace{=}_{\text{important}} \sum_{n=0}^\infty c_n x^n
$$

### Example 7. Multiply the geometric series

Given the power series $\frac1{1-x}  = 1 + x + x^2 + \cdots$, multiplying with itself, one finds the power series form for $\frac1{(1-x)^2}$, for $|x|<1$.

# §11.8 Taylor and Maclaurin  Series

The previous section has shown a sum of power series, when treated as a function $f(x)$, will be infinitely differentiable inside the interval of convergence. In this section, we ask the converse question: If a function $f(x)$ is infinitely differentiable, can we generate a power series from it? And if we can, will the generated power series converges to the function $f(x)$? The answer for the first question can be answered in this section.

Suppose $f(x)$ can be written as the sum of a power series on an interval $(a-R,a+R)$

$$
f(x) = \sum_{n=0}^\infty a_n (x-a)^n = a_0 + a_1(x-a) + a_2 (x-a)^2 + \cdots 
$$

with a positive radius of convergence $R$. By repeated term-by-term differentiation within the interval of convergence $I$ we obtain 

$$
f'(x) = a_1 + 2 a_2 (x-a) + 3a_3(x-a)^2 + \cdots \\ f''(x) = 2a_2 + 3\cdot 2 a_3 (x-a) + 4\cdots 3 a_4 (x-a)^2 + \cdots \\ \vdots \\ f^{(n)}(x) = n! a_n + \text{a sum of terms with $(x-a)$ as a factor}
$$

Since these equations all hold at $x=a$, we have 

$$
f'(a) = a_1,\\ f''(a) = 2! a_2,\\ \vdots \\ f^{(n)}(a) = n! a_n
$$

So if there’s a series converging to $f(x)$, then the coefficients must be

$$
a_n = \frac{f^{(n)}(a)}{n!}.
$$

The series is completely described by $f(x)$ 

$$
f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n.
$$

But what will happen if we only know that $f(x)$ is an infinitely differentiable function on an interval $I$? 

For an $x=a\in I$, we can still generate the series $\sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n$, but we have to study whether this series can converge to $f(x)$ or not. It will be discussed in the next section.

# Taylor and Maclaurin Series

## Definitions. Taylor Series, Maclaurin Series

Let $f$ be a function with derivatives of all orders throughout some interval containing $a$ as an interior point. The **Taylor series generated by $f$ at $x=a$ is** 

$$
\sum_{k=0}^\infty \frac{f^{(n)}(a)}{n!}(x-a)^n.
$$

If $x=0$ is an interior point of the interval, the **Taylor series generated by $f$ at $x=0$  is also called a Maclaurin series (generated by $f$) , which is simply** 

$$
\sum_{n=0}^\infty \frac{f^{(n)}(0)}{n!}x^n.
$$

### Example 1. Finding a Taylor Series

Find the Taylor series generated by $f(x) = 1/x$ at $a=2$. Where does the series converge to $1/x$ ?

**Solution.** The derivatives $f^{(n)}(2) = \frac{(-1)^n n!}{ 2^{n+1}}$. Therefore the Taylor series is 

$$
\sum_{n=0}^\infty \frac{(-1)^n}{2^{n+1}} (x-2)^n.
$$

It is a geometric series converges on $|x-2|<2$, with the sum $\frac{1/2}{1+\frac{(x-2)}{2}} = \frac1{x}$. Therefore the Taylor series converges to $1/x$ on $(0,4)$. 

### Example 2. Finding a Maclaurin Series

Find the Maclaurin series generated by $f(x) = e^x$. 

**Solution.** The Maclaurin series generated is 

$$
\sum_{n=0}^\infty \frac{x^n}{n!}.
$$

# Taylor Polynomials

If the function $f(x)$ has higher order derivatives at $a$, then we can truncate the Taylor series to finite order, resulting in a polynomial function. For example, if $f$ has derivative at $a$, we can truncate the Taylor series to order $1$, ended up with an order $1$ polynomial 

$$
f(a) + f'(a)(x-a)
$$

which is just the linear approximation of $f(x)$ at $x=a$, given in the section 3.8. From this point of view, a higher order Taylor polynomial might be a better approximation of $f(x)$. 

## Definition. Taylor Polynomial of Order $n$ (Partial sum of the Taylor Series)

Let $f$ be a function with derivatives of order $k=1,2,\cdots, N$ in some interval containing $a$ as an interior point. Then for any integer $n\le N$, the **Taylor polynomial of order $n$ generated by $f$ at $x=a$ is the polynomial** 

$$
P_n(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^n + \cdots + \frac{f^{(n)}(a)}{n!}(x-a)^n.
$$

### Notice.

Since the $n$th derivative of $f$ at $a$ maybe $0$, the actual degree for the polynomial might be smaller than $n$. That is why we don’t call $P_n(x)$ a **degree** $n$ polynomial, but use **order** instead.

### Example 2. Finding Taylor Polynomials for $e^x$

Find the Taylor polynomials generated by $e^x$ at $x=0.$

**Solution.** 

The order $n$ polynomial is given by $P_n(x) = \sum_{k=0}^n \frac{x^k}{k!}$ . 

![Untitled](W15-S1%20Power%20Series%20(II)%20d165bfc92d2141b6aef9e3ba1831fff1/Untitled.png)

### Example 3. Finding Taylor Polynomial for $\cos(x)$

Find the Taylor series and Taylor polynomials generated by $\cos(x)$ at $x=0$.

**Solution.**

The $n$th derivative for $\cos(x)$ can be expressed by $\cos^{(n)}(x) = \cos(x + \frac{n\pi}{2})$. The $n$th derivative at $x=0$ is either $0$ or $(\pm1)$ depending on the order. The Taylor series is given by 

$$
\sum_{k=0}^\infty \frac{(-1)^k x^{2k}}{(2k)!}=1-\frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} +\cdots
$$

And the order $2n$ and $2n+1$ Taylor polynomials (they are identical) are given by 

$$
P_{2n}(x) = 1- \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots + \frac{(-1)^n x^{2n}}{(2n)!}
$$

![Untitled](W15-S1%20Power%20Series%20(II)%20d165bfc92d2141b6aef9e3ba1831fff1/Untitled%201.png)

### Example 4. A Function $f$ Whose Taylor Series Converges at  Every $x$ but Converges to $f(x)$ Only at $x=0$

It can be shown that 

$$
f(x) = \begin{cases}0, & x=0\\ e^{-1/x^2}, & x\neq 0 \end{cases}
$$

has derivative of all orders at $x=0$ and that $f^{(n)}(0) = 0$ for all $n$. This means the Taylor series generated by $f$ at $x=0$ is $0$. But the function is only equal to $0$ at $x=0$. Which means the Taylor series converges everywhere but only be equal to $f$ at $x=0$.

![Untitled](W15-S1%20Power%20Series%20(II)%20d165bfc92d2141b6aef9e3ba1831fff1/Untitled%202.png)

## Two Questions

1. For what values of $x$ can we normally expect a Taylor series converges to its generating functions?
2. How accurately do a function’s Taylor polynomial approximate the function on a given interval?
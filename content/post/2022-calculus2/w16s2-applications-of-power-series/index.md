---
title: "W16-S2 Applications of Power Series"
date: 2022-06-10T21:31:17+08:00
draft: false
tags: ["binomial series","integral","arctangent","differential equation", "calculus2","lecture"]
---


周次: 16
日期: June 10, 2022
节次: 2

In this lecture, various applications for Taylor series are demonstrated. And we show how to generate a Fourier series from $f(x)$  in the end of the lecture.



# § 11.10 Applications of Power Series

## The Binomial Series for Powers and Roots

The Taylor series generates by $f(x) = (1+x)^a$, when $a$ is constant, is called the **binomial series**, 

$$
1+a x + \frac{a(a-1)}{2!} x^2 + \frac{a(a-1)(a-2)}{3!} x^3 + \cdots + \frac{a(a-1)(a-2) \cdots (a-k+1)}{k!} x^k + \cdots
$$

This series, converges absolutely for $|x|<1$. 

### Derive the Binomial Series

To see why the function $f(x) = (1+x)^a$ generates the series above, we need to take derivatives. The function and derivatives are listed below

$$
\begin{align*}f(x) &= (1+x)^a \\ f'(x) &= a(1+x)^{a-1} \\ f''(x) &= a(a-1) (1+x)^{a-2} \\ f'''(x) &= a(a-1)(a-2) (1+x)^{a-3} \\ \vdots \\ f^{(k)}(x) &= a(a-1)(a-2) \cdots (a-k+1)(1+x)^{a-k}\end{align*}
$$

If $a$ is a non-negative integer, the series terminates after $a+1$ terms, otherwise the series is infinite. 

### Radius of Convergence

Apply the Ratio Test for absolute convergence we see that 

$$
\left|\frac{u_{k+1}}{u_k}\right| = \left|\frac{a-k}{k+1}x\right|\to |x|
$$

So for $|x|<1$, the binomial series converges, but we will not be able to show that it indeed converges to $(1+x)^a$.

### The Binomial Series

For $-1<x<1$, 

$$
(1+x)^a = \sum_{k=0}^\infty \binom{a}{k} x^k 
$$

where we define 

$$
\binom{a}{0}=1,\quad \binom{a}{k} = \frac{a(a-1)\cdots (a-k+1)}{k!},\quad \text{for } k\ge 1.
$$

### Example 1. Using the Binomial Series

If $a=-1$,  

$$
\binom{-1}{k} = (-1)^k.
$$

So we get 

$$
\frac1{1+x} = \sum_{k\ge 0}(-1)^k x^k
$$

which is again a geometric series. 

### Example 2. Using the Binomial Series

If $a=\frac12$, we find 

$$
(1+x)^{1/2} = \sum_{k\ge 0}\binom{1/2}{k} x^k = 1+\frac{x}{2} -\frac{x^2}{8} + \frac{x^3}{16} - \frac{5 x^4}{128} + \cdots.
$$

Notice that the first two terms is a linear approximation for $(1+x)^{1/2}$, when $x$ is small.

## Summary. The Maclaurin Series for Common Functions

- **Power and Root functions**

$$
(1+x)^a = \sum_{k=0}^\infty \binom{a}{k} x^k, \quad \text{converges absolutely when $|x|<1$}
$$

- **Exponential function**

$$
e^x = 1 + \frac{x}{1!} + \frac{x^2}{2!} + \cdots = \sum_{k=0}^\infty \frac{x^k}{k!}, \quad \text{converges everywhere}.
$$

- **Logarithmic function**

$$
\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots=\sum_{k=1}^\infty \frac{(-1)^{k-1}}{k}x^k, \quad\text{converges absolutely when $|x|<1$}
$$

$$
\ln(1-x) = -x - \frac{x^2}{2} - \frac{x^3}{3} - \frac{x^4}{4} - \cdots=-\sum_{k=1}^\infty \frac{x^k}{k}, \quad\text{converges absolutely when $|x|<1$}
$$

- **Trigonometric functions**

$$
\sin(x) = x-\frac{x^3}{3!} + \frac{x^5}{5!} - \cdots = \sum_{k=0}^\infty \frac{(-1)^k}{(2k+1)!}x^{2k+1},\quad \text{converges everywhere}.
$$

$$
\cos(x) = 1- \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots = \sum_{k=0}^\infty \frac{(-1)^k}{(2k)!}x^{2k},\quad \text{converges everywhere}.
$$

- **Inverse trigonometric functions**

$$
\arctan(x) = x-\frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots = \sum_{k=0}^\infty \frac{(-1)^k}{k}x^{2k+1},\quad \text{converges absolutely when $|x|<1$}
$$

`Remark` The actual interval of convergence is $[-1,1]$. And from the Maclaurin series, we are able to find very interesting result for infinite series. The result will be shown later in this section.

With term-by-term integration, we can actually find the Maclaurin series for $\arcsin(x)$, since  

$$
\arcsin(x) = \int_0^x \frac{1}{\sqrt{1-t^2}}dt = \int_0^x \sum_{k=0}^\infty \binom{-1/2}{k}t^k dt = \sum_{k=0}^\infty \frac{\binom{-1/2}{k}}{k+1}x^{k+1}
$$

Again, the series converges absolutely for $|x|<1$.

## Applications of Power Series

### Evaluating Non-elementary Integrals

### Example 5. Express $\int \sin x^2 dx$ as a power series, and estimate the definite integral $\int_0^1 \sin x^2 dx$ with an error of less than $0.001.$

**Solution.** 

$$
\int \sin x^2 dx = C + \frac{x^3}{3} - \frac{x^7}{7\cdot 3!} + \frac{x^{11}}{11\cdot 5!} - \frac{x^{15}}{15\cdot 7!} + \frac{x^{10}}{19\cdot 9!} - \cdots
$$

$$
\int_0^1 \sin x^2 dx \approx \frac{1}{3} - \frac1{42} \approx 0.310.
$$

### Evaluating Indeterminate Forms

Besides L’Hôpital’s rule, we can use power series to evaluate indeterminate forms.

### Example 7. Limits Using Power Series

Evaluate 

$$
\lim_{x\to 1}\frac{\ln x}{x-1}.
$$

**Solution.** 

Write logarithmic function by Taylor’s formula at $x=1$

$$
\frac{\ln(x)}{x-1} = \frac{\ln(1) + \ln'(1)(x-1) + \frac{\ln''(c)}{2!} (x-1)^2 }{x-1} = \frac{(x-1) -\frac1{2 c^2}(x-1)^2 }{x-1}\to 1
$$

Note that it’s more convenient to use Taylor’s formula with remainder of  Peano-type.  

$$
\frac{\ln(x)}{x-1} = \frac{\ln(1) + \ln'(1)(x-1) + o( (x-1)) }{x-1} = \frac{(x-1) +o(x-1)}{x-1}\to 1
$$

### Example 8. Limits Using Power Series

Evaluate 

$$
\lim_{x\to 0}\frac{\sin(x) - \tan(x)}{x^3}
$$

**Solution.**

We have 

$$
\sin(x) - \tan(x) = \frac{\sin(x)}{\cos(x)} (\cos(x) - 1)  = \frac{\sin(x)}{\cos(x)}\left(1-\frac{x^2}{2!} + o(x^2)-1\right) = \frac{\sin(x)}{\cos(x)}\left(-\frac{x^2}{2!} + o(x^2)\right)
$$

Therefore a

$$
\lim_{x\to0}\frac{\sin(x) -\tan(x)}{x^3} = \lim_{x\to 0} \frac{\sin(x)}{x\cos(x)}\cdot\lim_{x\to 0}\frac{-\frac12 x^2 + o(x^2)}{x^2} = -\frac12.
$$

### Example 9. Approximation Formula for $\csc(x)$

Prove $\csc(x) \approx \frac1x + \frac{x}{6}.$

## Convergence for the endpoints

### Example. Arctangents

We have already seen that the $\arctan(x)$ can be written in power series 

$$
\arctan(x) = x-\frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots \quad \text{for $|x|<1$.}
$$

We have proved this with the term-by-term integration 

$$
\int_0^x \frac{1}{1+t^2}dt = \sum_{n=0}^\infty \int_0^x (-1)^n t^{2n} dt.
$$

The term-by-term integration only works for $x\in(-1,1)$. However, the series 

$$
x-\frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots
$$

converges for $x=\pm1$ as well. Therefore, we would like to know where does the series converge to for $x=\pm 1$, does it have anything to do with $\arctan(x)$  ? We cannot answer this with the term-by-term integration. So it is done by checking the remainder directly. 

Since 

$$
\frac1{1+t^2} = 1-t^2 + t^4 - t^6 + \cdots + (-1)^n t^{2n} + \underbrace{(-1)^{n+1} t^{2n+2} + \cdots}_{\text{add these together as a geometric series}}\\ = 1-t^2 + t^4 - t^6 + \cdots + (-1)^n t^{2n} + \frac{(-1)^{n+1} t^{2n+2}}{1+t^2}.
$$

Integrating both sides 

$$
\int_0^x \frac{1}{1+t^2} dt = \arctan(x) = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots + (-1)^n \frac{x^{2n+1}}{2n+1} + \underbrace{\int_0^x \frac{(-1)^{n+1}t^{2n+2}}{1+t^2} dt}_{\text{the Remainder $R_n(x)$}}.
$$

Thus, the remainder 

$$
|R_n(x)|\le \int_0^{|x|} t^{2n+2} dt = \frac{|x|^{2n+3}}{2n+3}.
$$

If $|x|\le 1$, the remainder approaches $0$ as $n\to \infty$. Therefore we obtain 

$$
\arctan(x) = \sum_{n=0}^\infty (-1)^{2n+1} \frac{x^{2n+1}}{2n+1},\quad \text{for $|x|\le 1$}.
$$

For $x=1$, we get **Leibniz’s formula** 

$$
\frac{\pi}{4} = 1-\frac13 + \frac15 -\frac17 + \frac19 -\cdots.
$$

## Power Series Solutions of Differential Equations and Initial Value Problems

### Example 3. Series Solution of an Initial Value Problem

Solve the initial value problem 

$$
y' - y = x,\quad y(0) = 1.
$$

**Solution**. Assuming the solution $y(x) = \sum_n a_n x^n$, taking into the differential equation, we get a recursion relation on the coefficients $a_n$. Considering the initial value, we will find $a_n$ recursively. Thus a solution can be found.

### Example 4. Solving a Differential Equation

Find a power series solution for 

$$
y'' + x^2 y = 0.
$$

**Solution.** 

The general solution is a linear combination of two separate series 

$$
y = a_0\left(1-\frac{x^4}{3\cdot 4} + \frac{x^8}{3\cdot 4\cdot 7\cdot 8} -\frac{x^{12}}{3\cdot 4 \cdot 7\cdot 8\cdot 11\cdot 12} + \cdots\right) \\ + a_1 \left(x-\frac{x^5}{4\cdot 5}+\frac{x^9}{4\cdot 5\cdot 8\cdot 9}-\frac{x^{13}}{4\cdot 5\cdot8\cdot 9 \cdot 12 \cdot 13} + \cdots\right)
$$

Both series converge absolutely for all $x$, as is readily seen by the Ratio Test.

# § 11.11 Fourier Series

Introduced by Joseph Fourier, the Fourier series approximates functions with sums of sine and cosine functions. Unlike the Taylor series, Fourier series often converges on wide intervals, and often works with discontinuous functions. So it is well suited for many problems in science and engineering.

Suppose we wish to approximate a periodic function $f$ on the interval $[0,2\pi]$ with the periodicity $2\pi$. We wish to use a sum of sine and cosine functions,

$$
f_n(x) = a_0 + \left(a_1 \cos x + b_1 \sin x\right) + \left(a_2 \cos 2x + b_2 \sin 2x\right) + \cdots + \left(a_n \cos nx + b_n \sin nx\right) 
$$

We would like to choose $a_0,a_1,\cdots, a_n$ and $b_0,b_1,\cdots, b_n$ that make $f_n(x)$ a “best possible” approximation to $f(x)$.

“Best possible” is defined as follows:

1. $f_n(x)$ and $f(x)$ give the same value when integrated from $0$ to $2\pi$
2. $f_n(x) \cos kx$ and $f(x)\cos kx$ give the same value when integrated from $0$ to $2\pi$
3. $f_n(x) \sin kx$  and $f(x)\sin kx$ give the same value when integrated from $0$ to $2\pi$

Altogether we impose $2n+1$ conditions on $f_n$

$$
\begin{align*}\int_0^{2\pi} f_n(x) dx &= \int_0^{2\pi} f(x) dx, \\ \int_0^{2\pi} f_n(x) \cos kx dx &= \int_0^{2\pi} f(x)  \cos kx dx,\\ \int_0^{2\pi} f_n(x) \sin kx dx &= \int_0^{2\pi} f(x) \sin kx dx.  \end{align*}
$$

Following from the fact that 

$$
\int_0^{2\pi} \cos kx dx = \int_0^{2\pi} \sin kx dx = 0
$$

$$
\int_0^{2\pi} \cos k x \cdot \cos kx dx = \pi = \int_0^{2\pi}\sin kx \cdot \sin kx dx 
$$

and 

$$
\int_0^{2\pi} \sin kx \cdot \sin mx dx  = \int_0^{2\pi} \cos kx \cos mx dx = 0, \quad m\neq k 
$$

$$
\int_0^{2\pi} \sin kx \cdot \cos mx dx = 0,\quad \forall m, k \in \mathbb{N}
$$

we find that 

$$
\begin{align*}\int_0^{2\pi} f(x) dx &= 2\pi a_0 \\ \int_0^{2\pi} f(x) \cos kx dx &= \pi a_k, \quad k=1,2,\cdots, n\\ \int_0^{2\pi} f(x) \sin kx dx &= \pi b_k,\quad k=1,2, \cdots, n  \end{align*}
$$

Therefore, the best possible $f_n(x)$  is when 

$$
a_0 = \frac1{2\pi} \int_0^{2\pi} f(x) dx,\quad a_k = \frac{1}{\pi}\int_0^{2\pi} f(x) \cos kx dx ,\quad b_k = \frac{1}{\pi}\int_0^{2\pi} f(x) \sin kx dx
$$

If we let $n\to \infty$, then using these rules, the resulting sum is called the **Fourier series for $f(x).$**
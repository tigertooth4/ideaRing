---
title:  "W14-S2 Absolute and Conditional Convergence, Power Series"
date: 2022-05-26T17:51:07+08:00
draft: false
tags: ["absolute","conditional","converge","diverge","rearrange","power series", "calculus2","lecture"]
---

周次: 14
日期: May 27, 2022
节次: 2

In this lecture, we will continue the discussion of absolute and conditional convergence, give the absolute convergence test to show any absolutely convergent series itself must converge.  We also look at the difference between absolute and conditional convergences by showing that an absolute convergent series remains the same even after the rearrangement of the terms. However, a conditionally convergent series maybe change its sum after the rearrangement. 

The next big topic is power series, we discuss the convergence property for this series. 


# Absolute and Conditional Convergence

## Why Absolutely Convergent?

1. It is **easier** to test. (We have a number of tests for the series with non-negative terms)
2. Converges absolutely$\implies$ converges!

## Theorem 16. The Absolute Convergence Test

If $\sum_n |a_n|$ converges, then $\sum_n a_n$ converges.

**Proof**.

### Remark.

Absolutely convergent is a stronger than conditionally convergent. So a conditionally convergent series may fail to be an absolutely convergent series.

### Example 3. Applying the Absolute Convergence Test

1. $\sum_{n=1}^\infty \frac{(-1)^n \ln n}{n^2}$ converges absolutely
2. $\sum_{n=1}^\infty \frac{(-1)^n \ln n}{n}$ converges conditionally

### Example 4. Being Alternating is Good for Convergence

1. If $p$ is a positive constant, then 

$$
\sum_{n=1}^\infty \frac1{n^p} \text{ converges when }p>1, \\ \text{but }\sum_{n=1}^\infty \frac{(-1)^n}{n^p} \text{ converges when } p>0.
$$

| ⁍ | ⁍ | ⁍ |
| --- | --- | --- |
| Converge | ✔️ | ✔️ |
| Absolutely | ❌ | ✔️ |
| Conditionally | ✔️ | ❌ |

The difference between absolute and conditional convergences is best shown from the following phenomenon. 

$$
\text{Absolute Convergent Series: Rearrange the terms does not change the sum}\\ \text{Conditional Convergent Series: Rearrange the terms DOES change the sum!}
$$

# Rearranging Series

## Theorem 17. The Rearrangement Theorem for Absolutely Convergent Series

If $\sum_n a_n$ **converges absolutely**, and $b_1,b_2,b_3,\cdot, b_n,\cdots$ is any rearrangement of the sequence $\{a_n\}$, then $\sum_n b_n$ converges absolutely and 

$$
\sum_n b_n = \sum_n a_n.
$$

### Example 5. Rearrangement on Absolutely Convergent Series

$$
1-\frac14 + \frac19 -\frac1{16} + \cdots
$$

Can be rearranged to 

$$
1-\frac14 - \frac1{16} + \frac19 + \frac1{25} + \frac1{49} - \frac1{36}-\frac1{64} -\frac1{100}-\frac1{144} + \cdots
$$

And since the series absolutely convergent, it really doesn’t matter how we rearrange it. It keeps absolutely converging to the same value.

However, a rearrangement on a conditionally convergent series is more interesting! 

### Example 6. Rearranging the Alternating Harmonic Series

The alternating harmonic series is **conditionally convergent series**! Thus

$$
1-\frac12 + \frac13 -\frac14 + \frac15 -\frac16 + \cdots
$$

can be rearranged to reach different sums.

- Rearrange to $1/2$ of the original sum.  Consider the following rearrangement
  
    $$
    \scriptsize\left(1-\frac12 -\frac14\right) + \left(\frac13 -\frac1{6} -\frac1{8}\right) + \left(\frac15-\frac1{10}-\frac1{12}\right) + \cdots + \left(\frac{1}{2n+1}-\frac{1}{4n+2} -\frac{1}{4n+4}\right) + \cdots
    $$
    
    Note that the grouping partial sum has the following form 
    
    $$
    \scriptsize\sum_{n=0}^\infty \left(\frac{1}{2n+1}-\frac{1}{4n+2}-\frac{1}{4n+4}\right) = \sum_{n=0}^\infty \left(\frac{1}{4n+2}-\frac1{4n+4}\right) = \frac12 \sum_{n=0}^\infty \left(\frac{1}{2n+1}-\frac{1}{2n+2}\right)
    $$
    
- Rearrange to a divergent series.  Since series of terms $\sum \frac{1}{2n-1}$ diverges to $+\infty$, and the series of terms $\sum\frac{-1}{2n}$ diverges to $-\infty$, we construct the following rearrangement
  
    $$
    \scriptsize\underbrace{\overbrace{\underbrace{1+\frac13 + \frac15 + \cdots + \frac1{2m_1+1}}_{\text{Larger than } 2} - \frac1{2}-\frac14 - \cdots - \frac{1}{2n_1 +1}}^{\text{smaller than }-3}+\frac{1}{2m_1+3}+\frac1{2m_1+5} + \cdots + \frac1{2m_2+1}}_{\text{larger than }4}+\cdots
    $$
    
    such that the partial sum swings large in either direction
    
- Rearrange to converge to 1. Making the partial sum swings about 1
    - Adds 1 (Making the partial sum just $\ge 1$)
    - Subtracts $\frac12$ (Making the partial sum just down to a value < 1)
    - Adds $\frac13$, $\frac15$ (Making the  partial sum just >1 again)
    - Subtracts $\frac14$ (Making the partial sum just < 1 again)
    - Adds $\frac1{7}$, $\frac19$ (Making the partial sum just > 1 again)
    - …
    
    The new arrangement looks like 
    
    $$
    \scriptsize 1-\frac12 + \frac13 + \frac15 -\frac14 + \frac17 +\frac19 -\frac16 + \frac1{11} + \frac1{13} -\frac18 +\frac1{15} + \frac1{17} -\frac1{10} + \frac1{19} + \frac1{21} \\ -\frac1{12} + \frac1{23} + \frac1{25} -\frac1{14} + \frac1{27} - \frac1{16} + \cdots
    $$
    
    Since the amount by which our partial sums exceed 1 or fall below it approaches zero, the new series converges to 1.
    

# Summary

![Untitled](W14-S2%20Absolute%20and%20Conditional%20Convergence,%20Power%20658eeafd84034e7bbb8a02c581abe5ee/Untitled.png)

# § 11.7 Power Series

## Intuition

- Power series = Infinite Order Polynomials
- Power series has Super Power! (Evaluating it gives  sum to some series)
- The algebraic manipulations like $+$, $-$,$\times$, $\frac{d}{dx}$ and $\int\cdot dx$ work for Power series

## Formal Definitions (Power Series, Center, Coefficients)

A **power series** about $x=0$ is a series of the form 

$$
\sum_{n=0}^\infty c_n x^n = x_0 + c_1 x + c_2 x^2 + \cdots + c_n x^n + \cdots
$$

A **power series** about $x=a$ is a series of the form 

$$
\sum_{n=0}^\infty c_n (x-a)^n = c_0 + c_1 (x-a) + c_2 (x-a)^2 + \cdots + c_n (x-a)^n + \cdots
$$

in which the **center $a$** and the **coefficients $c_0,c_1,c_2,\cdots, c_n, \cdots$** are constants.

## A Geometric Series View On the Convergence of Power Series

### Example 1. A Geometric Series As a Power Series Centered At $0$

If taking all the coefficients to be $1$, then a power series looks like 

$$
\sum_{n=0}^\infty x^n = 1+x+x^2 + \cdots + x^n + \cdots
$$

Since the ratio is $x$, it converges to $\frac1{1-x}$ for $|x|<1$. 

Rethink of the partial sums $P_n(x) = 1+x+x^2 + \cdots + x^{n-1}$ the approximation for the function $\frac1{1-x}$. Then we have a sequence of polynomial functions  

$$
P_1(x)=1, \\P_2(x)=1+x,\\ \cdots,\\ P_n(x)=1+x+\cdots+x^{n-1},\\ \cdots
$$

they are approaching $\frac1{1-x}$ if you are focusing on each number $x$ (point-wisely). The following graph shows the approximation. 

![Untitled](W14-S2%20Absolute%20and%20Conditional%20Convergence,%20Power%20658eeafd84034e7bbb8a02c581abe5ee/Untitled%201.png)

### Example 2. A Geometric Series As a Power Series Centered At $2$

The power series 

$$
1-\frac12(x-2) + \frac14(x-2)^2 + \cdots + \left(-\frac12\right)^n(x-2)^n + \cdots 
$$

is centered at $a=2$, with $c_0 = 1,$ $c_1 = -\frac12$, etc. This is a geometric series with the ratio $-\frac12(x-2)$. It converges for 

$$
\left|\frac{x-2}2\right|<1,\quad \text{or} \quad 0< x < 4.
$$

The sum is 

$$
\frac1{1+\frac{x-2}{2}} = \frac2{x}.
$$

So we view the convergence as a sequence of polynomial functions ( according to the partial sums) are approximating $f(x) = \frac2{x}$ for values of $x\in(0,4)$. Shown in the following graph.

![Untitled](W14-S2%20Absolute%20and%20Conditional%20Convergence,%20Power%20658eeafd84034e7bbb8a02c581abe5ee/Untitled%202.png)

### Example 3. Testing for Convergence Using the Ratio Test

For what values of $x$ do the following power series converge? 

1. $\sum_{n\ge 1}(-1)^n\frac{x^n}{n}$ 
    - First apply the Ratio Test to the series for absolute convergence: $\sum_{n\ge 1} \left|(-1)^n \frac{x^n}{n}\right|$ .
      
        It finds the ratio is approaching $|x|$, which means if $|x|<1$ then the series converges.
        
    - For $|x|>1$, the n-th term test confirms that the series  
    $\sum_n (-1)^n \frac{x^n}{n}$ diverges.
    - For $x=1$, the series converges according to the alternating series test (alternating harmonic series indeed).
    - For $x=-1$, the series diverges because it is the harmonic series.

1. $\sum_{n\ge 1}(-1)^n \frac{x^{2n-1}}{2n-1}$
2. $\sum_{n\ge 0} \frac{x^n}{n!}$
3. $\sum_{n\ge0}n! x^n$

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
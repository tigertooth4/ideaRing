---
title: "W14-S1 The Root Test, Alternating Series, Absolute and Conditional Convergence"
date: "2022-05-24T16:19:55+08:00"
draft: false
tags: ["root","test", "alternating series", "absolute", "conditional", "convergence","lectures","calculus2"]
---

周次: 14
日期: May 25, 2022
节次: 1

In this lecture, we continue the discussion on the root test (for the series with non-negative terms). And we discuss alternating series, there’s a test called Leibniz’s or alternating series test. Alternating series converges in a manner that positive and negative terms cancelling each other by a large amount. With this fact, we define the absolute convergence and conditional convergence, and find them totally different from the rearrangement perspective. 


# The Root Test ( For the Series with Non-negative Terms)

The ratio test is convenient for the case when $a_{n+1}/a_n$ is relatively simple. For more complicated series, we may need  other test method. For example

### Guiding Example

Let $a_n = \begin{cases}n/2^n, & n \text{ odd},\\ 1/2^n, & n\text{ even}\end{cases}$, does $\sum_n a_n$  converge? 

This is not a geometric series, and the $n$th term approaches $0$. So we do not know the series diverges. The Integral Test does not applicable as the sequence $a_n$ is not decreasing. The Ratio Test produces 

$$
\frac{a_{n+1}}{a_n} = \begin{cases}\frac1{2n}, & n\text{ odd} \\ \frac{n+1}{2}, & n\text{ even}\end{cases}
$$

As $n\to \infty$, the ratio has no limit. 

A test that will answer the question is the Root Test.

## Theorem 13. The Root Test

Let $\sum a_n$ be a series with $a_n\ge 0$ for $n\ge N$, and suppose that 

$$
\lim_n \sqrt[n]{a_n} = \rho.
$$

Then 

(a)  the series converges if $\rho < 1$

(b)  the series diverges if $\rho > 1$

(c)  the test is inconclusive if $\rho = 1.$

**Proof.**

### Example 3. Applying the Root Test

(a)  $\sum_{n=1}^\infty \frac{n^2}{2^n}$

( Converges )

(b)  $\sum_{n=1}^\infty \frac{3^n}{(1+\frac1n)^{n^2}}$

( Diverges )

(c) $\sum_{n=1}^\infty \left(\frac{1}{1+n}\right)^n$ 

( Converges )

### Guiding Example (Revisited)

Let $a_n = \begin{cases}n/2^n, & n \text{ odd},\\ 1/2^n, & n\text{ even}\end{cases}$, does $\sum_n a_n$  converge?

( Converges )

# Alternating Series

A series in which the terms are alternately positive and negative is an **alternating series.**

### Examples (Alternating Series)

- $1-\frac12 + \frac13 -\frac14 +\cdots + \frac{(-1)^{n+1}}{n} + \cdots$  **(alternating harmonic series, converges)**
- $-2 + 1 -\frac12 + \frac14 - \frac18 + \cdots + \frac{(-1)^n 4}{2^n}+\cdots$ **(converges)**
- $1-2+3-4 + 5-6 + \cdots +(-1)^{n+1}n + \cdots$ **(diverges)**

These are alternating series.

## **Theorem 14. (The Alternating Series Test , Leibniz’s Theorem)**

If $u_n\searrow\,0$ (starting from $n\ge N$), then the alternating series 

$$
\sum_{n=1}^\infty (-1)^{n+1} u_n = u_1 -u_2 + u_3 - u_4 + \cdots 
$$

converges.

**Proof.**

### Example 1. The alternating harmonic series

$$
\sum_{n=1}^\infty (-1)^{n+1}\frac1n = 1-\frac12 + \frac13 - \frac14 + \cdots\quad \text{converges}
$$

### Graphical Interpretation on Convergence

Why for $u_n\searrow 0$, the series 

$$
u_1-u_2+u_3-u_4 + u_5 -\cdots
$$

converges ? 

![Untitled](W14-S1%20The%20Root%20Test,%20Alternating%20Series,%20Absolute%20a8e63c2b08f644b7be79936601e4518f/Untitled.png)

From the graphical interpretation, we also learned that if the sum for alternating series is $L$, then the distance of the partial sum  $s_n$ and the total sum $L$ satisfies 

$$
|L-s_n|<u_{n+1}, \quad \forall \, n\ge N
$$

## Theorem 15. The Alternating Series Estimation Theorem

If the alternating series $\sum_n (-1)^{n+1} u_n$ satisfies $u_n\searrow 0$, then for $n\ge N$ the partial sum 

$$
s_n=u_1-u_2 +u_3- \cdots + (-1)^{n+1} u_n
$$

approximates the sum $L$ with an error whose absolute value is less than $u_{n+1},$ the numerical value of the first unused term. Furthermore, the remainder $L-s_n$ has the same sign as the first unused term.

### Example 2. Try Theorem 15 on the series whose sum we know

$$
\sum_{n} (-1)^n \frac1{2^n} = 1-\frac12 + \frac14 - \frac18 + \frac1{16} - \frac1{32} + \frac1{64} -\frac1{128} \bigg|+ \frac1{256} - \cdots 
$$

The sum of the series is $2/3$. And the partial sum indicating by the $\big|$ sign is $\frac23(1-(-\frac12)^6).$

The remainder, $\frac23(-\frac12)^8$ , is positive and less than $\frac1{2^8}.$

# Absolute and Conditional Convergence

## Definition. Absolutely Convergent

A series $\sum_n a_n$ **converges absolutely** (is **absolutely convergent**) if the corresponding series of absolute values, $\sum|a_n|$，converges.

## Definition. Conditionally Convergent

A series that converges but does not converge absolutely **converges conditionally.**

### Examples.

- All convergent series with non-negative terms converge absolutely
- $1+\frac{\sin(1)}{1^2}+\frac{\sin(2)}{2^2} + \frac{\sin(3)}{3^2} + \cdots$  converges absolutely
- $1-\frac12 + \frac13 - \frac14 + \cdots$  converges, but not absolutely. (Conditionally convergent)

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

| $\sum_n \frac{(-1)^n}{n^p}$ | $0<p\le 1$ | $p>1$ |
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

![Untitled](W14-S1%20The%20Root%20Test,%20Alternating%20Series,%20Absolute%20a8e63c2b08f644b7be79936601e4518f/Untitled%201.png)
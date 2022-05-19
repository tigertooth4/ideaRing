---
title: "W13-S2 The Limit Comparison Test and The Ratio and Root Tests"
date: 2022-05-19T14:41:38+08:00
draft: false
tags: ["comparison", "limit comparison", "test", "convergence","divergence","series", "ratio","root"]
---

周次: 13
日期: May 20, 2022
节次: 2

In this lecture, the Comparison Test is upgraded to the limit case. In addition, two new tests based on the comparison with respect to the geometric series is given. These are called the Ratio Test and the Root Test, respectively. Note that all the tests are designed for a series with non-negative terms.



# § 11.4 The Limit Comparison Test

**Note in this lecture all the series are considered to have all the terms being non-negative.**

## Recap: Theorem 10. The Comparison Test

1. If there is a convergent series $\sum_n c_n$ such that 
  
    $$
    a_n \le c_n\quad (\forall \, n\ge N)
    $$
    
    then $\sum_n a_n$ also converges.
    
2. If there is a divergent series $\sum_n d_n$ such that 
  
    $$
    a_n\ge d_n \quad (\forall\, n\ge N)
    $$
    
    then $\sum_n a_n$ also diverges.
    

**Ideas behind the Proof.** 

For case 1, the partial sum 

$$
\sum_{k=1}^n a_k \le \sum_{k=1}^n c_k \nearrow \sum_{k=1}^\infty c_k<\infty.
$$

For case 2, the partial sum 

$$
\sum_{k=1}^n a_k \ge \sum_{k=1}^n d_k \nearrow \sum_{k=1}^\infty d_k = \infty.
$$

### Example 1. Applying the Comparison Test

(a)  $\sum_{n=1}^\infty \frac{5}{5n-1}$

( Diverges. Compared with Harmonic series $\sum_n \frac1n$. Because $\frac{5}{5n-1} \ge \frac1n$.  )

(b)  $\sum_{n=0}^\infty \frac1{n!}$ 

( Converges. Compared with the Telescoping series $\sum_{n=2}^\infty \frac{1}{n(n-1)}$. Because $\frac1{n!}\le \frac{1}{n(n-1)}$ for all $n\ge 2$.  Alternatively, one can compare it with the geometric series $\sum_n \frac{1}{2^{n-1}}$ ) 

(c)  $5 +\frac23 + \frac17 + 1 + \sum_{n=1}^\infty \frac1{2^n+\sqrt{n}}$ 

( Converges. Compared with the geometric series $\frac1{2^n+\sqrt{n}} \le \frac1{2^n}$)

## Remarks

- The $p$-series and geometric , telescoping series are frequently been used to be compared with.
- The Comparison Test  **ONLY WORKS** for the series with non-negative terms (or with non-positive terms).
  
    For example, the following series with both positive and negative terms
    
    $$
    \sum_{n=0}^\infty a_n  = 1-2 + \frac12 - 4 +\frac1{2^2}-6 + \frac1{2^3}-8 + \cdots
    $$
    
    diverges, although all the terms $a_n\le \frac1{\sqrt{2}^{n}}$.
    
- That’s been said, if a series has only finite many negative terms, the comparison test is still applicable. For example

$$
-2 -3 + \sum_{n=3}^\infty \frac{1}{n^2 \ln n}
$$

## The Limit Comparison Test

Based on the experiences built up from the comparison test, we may get the feeling that testing for convergence is largely about recognizing how fast the $n$th term is approaching $0$. 

Therefore, the concepts of *growth rate* or *order* can be applied to the convergence test.  

## Theorem 11. Limit Comparison Test

Suppose that $a_n>0$ and $b_n>0$ for all $n\ge N$ ($N$ an integer).

1. If
  
    $$
    \lim_{n\to \infty}\frac{a_n}{b_n} = c > 0 \quad (a_n\, \text{and }  b_n \text{ have the same order})
    $$
    
     then $\sum_n a_n$ and $\sum_n b_n$ both converge or both diverge.
    
1. If  
  
    $$
    \lim_{n\to\infty}\frac{a_n}{b_n}=0 ,\quad(a_n\text{ is much smaller}) \quad \text{and}\quad \sum_n b_n \, \text{converges}
    $$
    
    then $\sum_n a_n$ converges.
    
1. If 
  
    $$
    \lim_{n\to\infty}\frac{a_n}{b_n} = \infty,\quad (a_n \text{ is much bigger})\quad\text{and}\quad \sum_n b_n \, \text{diverges}
    $$
    
    then $\sum_n a_n$ diverges.
    

**Proof.**

### Example 2. Using the Limit Comparison Test

Which of the following series converges, and which diverge? 

1.  

$$
\frac34 + \frac59 + \frac7{16} +\cdots + \frac{2n+1}{(n+1)^2} + \cdots
$$

b. 

$$
\frac11 + \frac13 + \frac17 + \frac1{15} + \cdots + \frac{1}{2^n-1} + \cdots
$$

c. 

$$
\frac{1+2\ln2}{9} + \frac{1+3\ln 3}{14} + \frac{1+4\ln 4}{21} + \cdots + \frac{1+n\ln n}{n^2+5} + \cdots
$$

### Example 3. Does $\sum_{n=1}^\infty \frac{\ln n}{n^{3/2}}$ converge?

# §11.5 The Ratio and Root Tests

## The Ratio Test

For a geometric series $\sum_n a r^n$, the ratio is a constant

$$
\frac{a_{n+1}}{a_n} \equiv r,\quad \sum_n a r^n \text{ converges iff |r|<1}.
$$

For other series, it appears that we can measure the rate of growth (or decline) by extending the “Ratio Test”. 

## Theorem 12. The Ratio Test

Let $\sum_n a_n$ be a series with positive terms and suppose that 

$$
\lim_{n\to\infty}\frac{a_{n+1}}{a_n} = \rho.
$$

Then 

(a)  the series converges if $\rho < 1$,

(b)  the series diverges if $\rho > 1$,

(c)  the test is inconclusive if $\rho = 1$.

**Proof.** 

### Example 1. Applying the Ratio Test

(a)  $\sum_{n=0}^\infty \frac{2^n + 5}{3^n}$

( Converges )

(b)  $\sum_{n=1}^\infty \frac{(2n)!}{n!n!}$

( Diverges ) 

(c)  $\sum_{n=1}^\infty \frac{4^n n! n!}{(2n)!}$

( Diverges, but inconclusive from the Ratio Test )

## The Root Test

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
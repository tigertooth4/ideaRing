---
title: "W12-S2 Series"
date: 2022-05-12T13:20:39+08:00
draft: false
tags: ["series", "geometric series", "telescoping series", "converge","diverge", "sum", "test", "calculus2", "lecture"]
---

周次: 12
日期: May 13, 2022
节次: 2

In this lecture, we will talk about series, we introduce the sigma notation, and utilize limit to define the sum of a series. Primarily, there are two types of series whose sums can be found directly, by definition. Those are called Geometric Series and Telescoping Series. To study a divergent series, we introduce the $n$th term divergence test and finally we will look at combining series and give rules for finding the sums.

# Outline

# Reviews on the Supreme and Infimum

## Simplified Definition.

- A supreme (**least upper bound**) for  sequence $\{a_n\}$ is

$$
\sup \{a_n\} = \text{The Smallest Upper Bound for }\{a_n\}.
$$

- An infimum (**greatest lower bound**) for sequence $\{a_n\}$ is

$$
\inf\{a_n\} = \text{The Largest Lower Bound for }\{a_n\}.
$$

## Existence.

- A supreme of $\{a_n\}$ exists, if $\{a_n\}$  is bounded from above,
- An infimum of $\{a_n\}$ exists, if $\{a_n\}$ is bounded from below.

**The existence of supreme and infimum is a fundamental property for real number system.**

## Uniqueness.

- A supreme of  $\{a_n\}$ if exists then it is unique
- An infimum of $\{a_n\}$ if exists then it is unique

## Properties.

- $\sup\{a_n\}$ is an upper bound for $\{a_n\}$, but any smaller  number will not be an upper bound anymore, i.e.

$$
\forall \epsilon>0, \quad \exists \, a_{n_0}, \quad s.t. \quad a_{n_0} > \sup\{a_n\} - \epsilon.
$$

- $\inf\{a_n\}$ is a lower bound for $\{a_n\}$, but any greater number will not be a lower bound anymore, i.e.

$$
\forall \epsilon>0,\quad \exists a_{n_0},\quad s.t. \quad a_{n_0}< \inf\{a_n\} + \epsilon.
$$

### Theorems.

- A bounded from above, increasing sequence $\{a_n\}$ converges to its least upper bound $\sup\{a_n\}$,
- A bounded from below, decreasing sequence $\{a_n\}$ converges to its greatest lower bound $\inf\{a_n\}$,
- Any convergent sequence is **bounded. (**But not every bounded sequence converges! )
- Every bounded, monotonic sequence converges !

### Example. An important limit

The sequence $\{(1+\frac1n)^n\}$ is increasing and bounded from above, therefore it converges. 

### Example.

Show that the sequence $a_{n+1} = \sqrt{2 a_n}$  with $a_1 = 1$ is monotonic and bounded. And find the limit from the recursive definition.

# §11.2 Infinite Series

An infinite series is the sum of an infinite sequence of numbers 

$$
a_1+a_2+a_3 + \cdots + a_n +\cdots
$$

The goal of this section is to understand the meaning of such an infinite sum and to develop methods to calculate it. 

Since there are infinite many terms, we cannot just keep adding to see what comes out. Instead we look at what we get by summing the first $n$ terms and stopping. 

$$
s_n = a_1 + a_2 + a_3 + \cdots + a_n.
$$

The sum is a normal addition and we call it the $n$th **partial sum**. As $n$ gets larger, we expect the partial sums ( sequence $\{s_n\}$ ) to get closer and closer to a limiting value. 

### Example. An Geometric Series

$$
1+\frac12 + \frac14 +\frac18 + \cdots + \frac1{2^n} + \cdots
$$

The **partial sum** is given by the formula 

$$
s_n = 1+\frac12 + \frac14 + \cdots + \frac1{2^{n-1}} = \frac{1-\frac1{2^n}}{1-\frac12} = 2 - \frac1{2^{n-1}}.
$$

$s_n$ is approaching $2$. Thus we say (define) the infinite series has a value $2.$  Notice that any finite sum in this series is not equal to $2$. So $2$ is the number that the **partial sum** could only get arbitrarily close to but never reach. 

## Definition. Partial Sum, Converges, Sum of Infinite Series

Given a sequence of numbers $\{a_n\}$, an expression of the form 

$$
a_1 + a_2 + a_3 + \cdots + a_n + \cdots
$$

is an **infinite series**. The sequence $\{s_n\}$ defined by 

$$
s_n = a_1 + a_2 + \cdots + a_n
$$

is the **sequence of partial sums** of the series. 

- If the sequence $\{s_n\}$ converges to a limit $L$, we say the series **converges** and that its **sum** is $L$. And write

$$
\sum_{n=1}^\infty a_n := a_1 + a_2 + a_3 +\cdots + a_n +\cdots = L.
$$

- If the sequence $\{s_n\}$ diverges, we say the series **diverges.**

### The Sigma Notation

Whether it is convergent or not, we use sigma notation to denote the infinite sum. We can write a series as 

$$
\sum_{n=1}^\infty a_n, \quad \sum_{k=1}^\infty a_k,\quad \text{or} \quad \sum a_n.
$$

## Geometric Series

**Geometric series** are series of the form 

$$
a + a\,r + a \, r^2 + \cdots + a \, r^{n-1} + \cdots =\sum_{n=1}^\infty a \, r^{n-1}
$$

in which $a$ and $r$ are fixed real numbers and $a\neq 0$. The series can also be written as $\sum_{n=0}^\infty a\, r^{n}$. 

The geometric series satisfies 

$$
a_{n+1}/a_n =r = \text{constant},
$$

where $r$ is the **ratio.** It can be either positive or negative. 

- For example
  
    $$
    1+\frac12 + \frac14 + \cdots + \frac1{2^n} + \cdots 
    $$
    
    is a geometric series with $r = \frac12.$  
    
- As in
  
    $$
    1-\frac13 + \frac19 - \cdots + \left(-\frac13\right)^{n-1} + \cdots
    $$
    
    is a geometric series with $r=-\frac13$. 
    
- If $r=1$, the geometric series is a sum of infinite many constants

$$
a + a+a + \cdots + a +\cdots
$$

### The Partial Sum for Geometric Series

Thanks to the polynomial factorization formula 

$$
1-x^{n+1} = (1-x) ( 1 + x + x^2 + \cdots + x^n)
$$

We see that 

$$
1+x+x^2 + \cdots + x^n = \frac{1-x^{n+1}}{1-x}.
$$

This formula helps us to find the partial sum form for geometric series $\sum_{k=0}^n a \, r^k$ with $r\neq 1$: 

$$
s_n = \sum_{k=0}^n a \, r^k = a \frac{1-r^{n+1}}{1-r}. 
$$

For $r=1$, it is even simpler: 

$$
s_n=\sum_{k=0}^n a \, 1^k = \underbrace{a+a+\cdots + a}_{n+1} = (n+1)a.
$$

- For $|r|<1$, the partial sum converges since $r^{n+1}\to 0$ as $n\to \infty$, so

$$
\sum_{n=0}^\infty a \, r^n = \lim_{n\to\infty} s_n = \frac{a}{1-r}.
$$

- For $|r|\ge 1$, the partial sum of geometric series $\sum a r^n$ is given either by

$$
a \frac{1-r^{n+1}}{1-r},\quad (r\neq1),\quad \text{or}\quad (n+1) a \quad (r=1).
$$

Either case, the partial sum diverges. 

### Conclusion (Simple but Important)

- For $|r|<1$, the geometric series $\sum_{n=0}^\infty a \, r^n$ converges to $\dfrac{a}{1-r}$;
- For $|r|\ge 1$, the geometric series $\sum_{n=0}^\infty a\, r^n$ diverges.

### Example 1. Index Starts with $n=k\in \mathbb{N}$

A geometric series with $r=\frac13$ is given by 

$$
\frac1{3^k} + \frac1{3^{k+1}} + \frac{1}{3^{k+2}} \cdots = \sum_{n=k}^\infty \left(\frac{1}{3}\right)^n = ?
$$

### Example 2. Index Starts with $n=0$

The series 

$$
\sum_{n=0}^\infty \frac{(-1)^n 5}{4^n}
$$

is a geometric series with $a=5$ and $r=-\frac14$. It converges to ? 

### Example 3. Repeating Decimals

Express the repeating decimal $5.91,91,91\ldots$ as a rational number?

(Solution: $5\frac{91}{99}$)

### Example. $0.999\ldots = 1$

Express the repeating decimal $0.999\ldots$ as a rational number.

## Telescoping Series

A telescoping series is usually referring to the case when 

$$
\sum_n a_n = \sum_n (b_n-b_{n-1}).
$$

As taking the partial sum, 

$$
s_n = a_1 + a_2 + \cdots + a_n = (b_1-b_0) + (b_2-b_1) + \cdots + (b_n-b_{n-1}) = b_n - b_0.
$$

Thus the summation has been greatly simplified. 

### Example 5. A Telescoping Series

Find the sum of the series $\sum_{n=1}^\infty \frac{1}{n(n+1)}$.

### Example 6. A Divergent Telescoping Series

Find the divergence for the series $\sum_{n=1}^\infty \ln\frac{n+1}{n}$.

**`Remark` In general, it is very rare that the sum of a series can be calculated directly. The geometric series and telescoping series are two such examples. The calculation of series has been done largely by evaluating function series at some specific locations.**

## Divergent Series

### Example 6. Partial Sums for Two Divergent Series

1. The series 

$$
\sum_{n=1}^\infty n^2 = 1 + 4 + 9 + \cdots + n^2 + \cdots
$$

b. The series

$$
\sum_{n=1}^\infty \frac{n+1}{n} = \frac21 + \frac32 + \frac 43 + \cdots + \frac{n+1}{n} + \cdots
$$

## The $n$th-Term Test for Divergence

It is obvious that 

### Theorem 7.

If $\sum_{n=1}^\infty a_n$ converges, then $a_n\to 0.$

It leads to the following test for detecting the kind of divergence occurred in the previous Example 6. 

### The $n$th Term Test for Divergence

$\sum_{n=1}^\infty a_n$ diverges if $\lim_{n\to\infty} a_n$ fails to exist or is different from $0.$

### Example 7. Applying the $n$th Term Test

1. $\sum_n n^2$ 
2. $\sum_n \frac{n+1}{n}$
3. $\sum_n (-1)^{n+1}$
4. $\sum_n \frac{-n}{2n+5}$

**`Remark` The $n$th term test is a necessary condition for convergence, it does not mean that if a series passes the test, then it converges.**

### Example 8. A Series Diverges Even $a_n\to 0$

Find the Harmonic Series 

$$
1 + \frac12 + \frac13 + \frac14 + \cdots + \frac1{n} + \cdots 
$$

diverges.

## Combining Series

Whenever we have two convergent series, we can add them term by term, subtract them term by term, or multiply them be constants to make new convergent series.

### Theorem 8

If $\sum a_n = A$ and $\sum b_n = B$ are convergent series, then 

1. *Sum Rule:* 

$$
\sum (a_n+b_n) = \sum a_n + \sum b_n =A+B
$$

1. *Difference Rule:* 

$$
\sum(a_n-b_n) = \sum a_n - \sum b_n = A-B
$$

1. Constant Multiple Rule: 

$$
\sum k\, a_n = k\sum a_n = k A
$$

**`Remark` These rules can be summarized to a single linear rule:  For any constants $\alpha$  and $\beta,$**

$$
\sum (\alpha a_n + \beta b_n ) = \alpha \sum a_n + \beta \sum b_n = \alpha A + \beta B
$$

### Corollaries

1. Every nonzero constant multiple of a divergent series diverges
2. If $\sum a_n$ converges and $\sum b_n$ diverges, then $\sum(a_n\pm b_n)$  diverges

**`Caution` If both series diverge, combining series may be not diverge.**

$$
\sum_n 1\quad \text{and}\quad \sum_n (-1)
$$

both diverge, but $\sum (1+ (-1)) = \sum_n 0$ converges.

### Example 9. Find the sum of the following series

Find the sum of 

$$
\sum_{n=1}^\infty \left(\frac{3^{n-1}-1}{6^{n-1}}+\frac{1}{n(n+1)}\right)
$$

## Adding or Deleting Terms

Adding or deleting finite many terms from a series, does not change the convergence/ divergence nature of the series.

## Shifting the Index

$$
\sum_{n=1}^\infty a_n = \sum_{n=-6}^\infty a_{n+7}
$$

This type of operation doesn’t alter the series at all.
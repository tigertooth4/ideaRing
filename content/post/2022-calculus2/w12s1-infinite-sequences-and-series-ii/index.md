---
title: "W12-S1 Infinite Sequences and Series (II)"
date: 2022-05-10T16:37:28+08:00
draft: false
tags: ["sequence","series", "L'Hôpital","bounded-monotonic", "geometric-series","telescoping", "lecture","divergence","test","lecture","calculus"]
---

周次: 12
备注: Attendance check
日期: May 11, 2022
节次: 1

In this lecture, we continue the discussion of infinite series. We introduce the L’Hôpital’s Rule to the limit finding problems, and conclude this section by an important type of convergent sequences, called **bounded monotonic sequences.** Then we will talk about series, we introduce the sigma notation, and utilize limit to define the sum of a series. Primarily, there are two types of series whose sums can be found directly, by definition. Those are called Geometric Series and Telescoping Series. To study a divergent series, we introduce the $n$th term divergence test and finally we will look at combining series and give rules for finding the sums.

# Outline

# § 11.1 Infinite Sequences

We’ve mentioned previously 

- The representations of infinite sequences
- Definitions of Convergence / Divergence (by $\epsilon-N$ statement)
    - Divergence to infinity
    - Divergence but bounded
    - General Divergence
- Basic Rules to the Limit
    - Linear rule
    - Multiplication rule
    - Quotient rule
- Sandwich Theorem for Sequences
- Continuous Functions Theorem for Sequences

## Using l’Hôpital’s Rule

### Guiding Example

Occasionally we may consider the following sequence 

$$
\left\\{\frac{\ln n} n\right\\}_{n=2}^\infty
$$

To find the limit, it brings up to the using of  l’Hôpital’s Rule. However, l’Hôpital’s rule does not apply, because $n$ is not a continuous variable but discrete one. So in order to use l’Hôpital’s rule, we need to bridge the continuous and discrete problems. The following theorem does exactly as we expect.

### Theorem 4.

Suppose that $f(x)$ is a function defined for all $x\ge n_0$ and that $\{a_n\}$ is a sequence of real numbers such that $a_n = f(n)$ for $n\ge n_0$. Then

$$
\lim_{x\to\infty} f(x) = L\quad \implies \quad \lim_{n\to\infty} a_n =L.
$$

### Example 7. Applying L’Hôpital’s Rule

Show that $\lim_{n\to\infty} \frac{\ln n}{n} = 0$.

### Example 8. Applying L’Hôpital’s Rule

Find $\lim_{n\to \infty} \frac{2^n}{5n}.$

### Example 9. Applying L’Hôpital’s Rule to Determine Convergence

Does the sequence $a_n = \left(\frac{n+1}{n-1}\right)^n$ converge? 

## Commonly Occurring Limits

### Theorem 5.

The following six sequences converges to the limits listed below:

1. $\lim_{n\to \infty}\frac{\ln n}{n} = 0$
2. $\lim_{n\to\infty}\sqrt[n]{n} = 1$
3. $\lim_{n\to\infty}x^{1/n} = 1,\quad (x>0)$
4. $\lim_{n\to\infty}x^n = 0,\quad (|x|<1)$
5. $\lim_{n\to\infty}\left(1+\frac{x}{n}\right)^n = e^x,\quad (\forall\, x)$
6. $\lim_{n\to\infty} \frac{x^n}{n!} = 0,\quad (\forall\, x)$

### Example 10. Applying Theorem 5

1. $\frac{\ln(n^2)}{n} \to ?$
2. $\sqrt[n]{n^2}\to ?$
3. $\sqrt[n]{3n}\to ?$
4. $\left(-\frac12\right)^n\to?$
5. $\left(\frac{n-2}{n}\right)^n\to ?$
6. $\frac{100^n}{n!}\to ?$

## Bounded Monotonic Sequences

An important special type of sequence is one for which terms are monotonically increasing or decreasing, i.e. 

$$
\forall \, n,\quad a_n\le a_{n+1} \quad \text{or} \quad \forall \, n, \quad a_n\ge a_{n+1}.
$$

`**Remark**`. In this course, increasing is equivalent to nondecreasing. And when $a_n<a_{n+1}$ for all $n$, we could say sequence $\{a_n\}$ is strictly increasing.

### Example 12. Increasing (Nondecreasing) Sequences

1. $1,2,3,\cdots, n,\cdots$
2. $\frac12, \frac23,\frac34,\cdots, \frac{n-1}{n},\cdots$ 
3. $3,3,3,\cdots, 3,\cdots$
4. $\frac21, (\frac32)^2, (\frac43)^3,\cdots, (\frac{n+1}{n})^n,\cdots$

What’s important for a monotonic sequence, is it makes the discussion of limit simpler.

For example, if one looks at a sequence 

$$
\left \\{ \sqrt[n]{n}\right \\}_{n=1}^\infty
$$

We can find for very large $n$, the sequence is decreasing. And it certainly has a lower bound $0$. Therefore the sequence converges. 

### Definition. Bounded , Upper Bound, Least Upper Bound

- A sequence $\{a_n\}$ is **bounded from above** if there exists a number $M$ such that $a_n\le M$ for all $n$. The number $M$ is called an **upper bound** for $\{a_n\}$.
- A sequence $\{a_n\}$ is **bounded from below** if there exists a number $N$ such that $N\le a_n$ for all $n$. The number $N$ is called an **lower bound** for $\{a_n\}$.
- A sequence $\{a_n\}$ is **bounded,** if there exists a number $M$ such that $|a_n|\le M$ for all $n.$ The number $M$ is called a **bound** for $\{a_n\}$.

### Example 13. Applying the Definition for Boundedness

1. The sequence $1,2,3,\cdots, n,\cdots$ has no upper bound, but there is a lower bound.
2. The sequence $\frac12, \frac23,\frac34,\cdots, \frac{n}{n+1},\cdots$ is bounded above by $M=1$, and bounded below by $N=0$ or any number less or equal to $1/2$. 

**`Remark`** The bound is usually not unique. For example, $1$ is an upper bound for sequence $\{\frac{n}{n+1}\}$, and $2$ is another upper bound for it. 

### Definition. Least Upper Bound (Supreme) and Greatest Lower Bound (Infimum)

- If a number $S$ is an upper bound for $\{a_n\}$,  and among all the upper bounds, $S$ is the smallest one, then $S$ is called a **least upper bound (or a supreme)** for $\{a_n\}.$ And it is denoted by $\sup \{a_n\}$
- If a number $I$ is a lower bound for $\{a_n\}$, and among all the lower bounds, $I$ is the biggest one, then $I$ is called a **greatest lower bound (or a infimum)** for **$\{a_n\}$.** It is denoted by $\inf\{a_n\}$.

**`Remarks.`** 

- $\sup\{a_n\}$, if exists, is an upper bound for $\{a_n\}$.
- $\inf\{a_n\}$ , if exists, is a lower bound for $\{a_n\}$.

### Theorem.

- Any sequence if it has an upper bound, then it must have a least upper bound, or supreme.
- Any sequence if it has a lower bound, then it must have a greatest lower bound, or infimum.

This theorem is a property of completeness for the real number system. Therefore we omit the proof. 

However, we will prove a proposition by using the concept of least upper bound or greatest lower bound. 

### Proposition.

Suppose $\{a_n\}$ is an increasing sequence with least upper bound $L$, then $\lim_{n\to\infty}a_n = L.$

### Theorem 6. The Monotonically Bounded Theorem

- An increasing sequence of real numbers converges **if and only if** it is bounded from above. If  it is bounded from above, it converges to its least upper bound.
- A decreasing sequence of real numbers converges **if and only if** it is bounded from below. It it is bounded from below, it converges to its greatest lower bound.

![Untitled](W12-S1%20Infinite%20Sequences%20and%20Series%20(II)%201737eed4fc524166954bf274709f5c1b/Untitled.png)

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
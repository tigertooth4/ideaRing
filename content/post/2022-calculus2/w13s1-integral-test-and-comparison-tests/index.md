---
title: "W13-S1 The Integral Test and Comparison Tests"
date: 2022-05-17T16:45:17+08:00
draft: false
tags: ["integral", "test","comparison","limit","convergence","calculus2","lecture","series"]
---


周次: 13
日期: May 18, 2022
节次: 1

In this lecture, we develop some convergence tests for the series with non-negative terms. These are the Integral Test and Comparison Tests. Both tests are based on the Monotonic Bounded Theorem for partial sum sequences. Before developing the tests, we will recap the previous section first.



# I. Recap: § 11.2 Series

## Basic Problems for Series

Primarily, given a series $\sum_n a_n$, we have two questions:

1. Does the series converge?
2. If it converges, what is its sum?

For most series, we expect answers to the first question. As a practical matter, the second question is also important. Unfortunately, only few of the sums can be computed precisely. 

## Key Results in § 11.2

- Infinite sum:  Consider the limit of partial sum sequence $\{s_n\}$
- Two computable series: Geometric and Telescoping
- Divergence Test: if $a_n\not\to 0$, then $\sum_n a_n$ diverges
- Have not covered: Combining Series, shift the index, add / delete finite many terms

Starts from the last part of section 11.2. >>>

---

## Combining Series

Whenever we have two **convergent** series, we can add them term by term, subtract them term by term, or multiply them by constants to make new convergent series.

### Theorem 8 (Combination of Series)

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

**Proof.** 

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

# § 11.3 The Integral Test for Series with Non-negative Terms

In this section and the next two, we study series with terms being all non-negative , or all non-positive. i.e. the series 

$$
\sum_n a_n\quad \text{with}\quad a_n\ge 0,\quad \text{or} \quad \sum_n a_n \quad \text{with}\quad a_n\le 0.
$$

Without loss of generality, the following discussion are based on the series with non-negative terms only. 

## Nondecreasing Partial Sums

For series $\sum_n a_n$ with $a_n\ge 0$, it is easy to see that $s_{n+1} = s_n + a_n \ge s_n$. Thus the partial sum sequence is a nondecreasing sequence. The Nondecreasing Sequence Theorem tells us that the series will converge if and only if the partial sums are bounded from above.

$$
\sum_n a_n\quad \text{where}\quad a_n\ge 0,\quad \implies \quad s_n = a_1 + \cdots + a_n\, \text{is } \nearrow.
$$

Hence, in order to converge, it only need the partial sum $s_n$ to be bounded from above. 

### Example 1. The Harmonic Series

The series $\sum_n \frac1{n} = 1 + \frac12 + \frac13 + \cdots$ is called the **harmonic series.** Although it passes the $n$th term test ($\frac1n\to 0$), it still diverges because of the unbounded partial sum. To see the partial sums are unbounded, we can use

1. Grouping the terms    
  
    $$
    1+ \frac12 + \underbrace{\frac13 + \frac14}_{>\frac12} + \underbrace{\frac15 + \frac16 + \frac17 + \frac18}_{>\frac48 = \frac12} + \underbrace{\frac19 + \frac1{10} + \cdots + \frac1{16}}_{>\frac8{16} = \frac12} + \cdots
    $$
    
2. An inequality $\frac1n \ge \ln\frac{n+1}{n}$. 

The following graph shows the growth of partial sum against the growth of $\ln(x)$.

![Untitled](W13-S1%20The%20Integral%20Test%20and%20Comparison%20Tests%207f7c5394d7a644859eb3fbd5301d0d72/Untitled.png)

## The Integral Test

### Guiding Example

Does the following series converge? 

$$
\sum_{n=1}^\infty \frac{1}{n^2} = 1 + \frac14 + \frac19 + \frac1{16} + \cdots + \frac1{n^2} + \cdots
$$

The value for each term can be plotted as columns in the following graph

![Untitled](W13-S1%20The%20Integral%20Test%20and%20Comparison%20Tests%207f7c5394d7a644859eb3fbd5301d0d72/Untitled%201.png)

The partial sum is equal to the total area of the first $n$-columns. To show the sum is bounded from above, we look at the area under the function $y=\frac{1}{x^2}$ (from $1$ to $\infty$)

![guidingEg.gif](W13-S1%20The%20Integral%20Test%20and%20Comparison%20Tests%207f7c5394d7a644859eb3fbd5301d0d72/guidingEg.gif)

Since the integral $\int_1^\infty \frac{dx}{x^2}$ is finite, the total area for $n$-columns is bounded. Here is a plot of partial sums for $n$ from $1$ to $80$. As the graph shown, the partial sum is bounded from above.

![Untitled](W13-S1%20The%20Integral%20Test%20and%20Comparison%20Tests%207f7c5394d7a644859eb3fbd5301d0d72/Untitled%202.png)

## Theorem 9. The Integral Test

Let $\sum_n a_n$ be non-negative series. Suppose that $a_n = f(n)$, where $f$ is a continuous, non-negative and decreasing function of $x$ for all $x\ge N$ ($N$ is a positive integer). Then the series $\sum_{n=N}^\infty a_n$ and the integral $\int_N^\infty f(x) dx$ both converge or both diverge.

**Proof.**

### Example 3. The $p$-Series

Show that the $p$-series 

$$
\sum_{n=1}^\infty \frac{1}{n^p} = \frac1{1^p} + \frac1{2^p} + \frac1{3^p} + \cdots + \frac1{n^p} + \cdots
$$

converges if $p>1$, and diverges if $p\le 1$.

***`Remark.`*** The $p$-Series are very important type of convergent series.

### Example 4. A Convergent Series

Show the series 

$$
\sum_{n=1}^\infty \frac{1}{n^2+1}
$$

converges by the Integral Test.

# § 11.4 Comparison Tests (for Series with Non-negative Terms)

For many series with non-negative terms, we can find the upper bound for the partial sum by comparing the series with another series whose convergence is known. 

### Guiding Example.

Study the convergence / divergence of the following series 

$$
\sum_{n\ge 2} \frac{1}{n^2 \ln(n)}. 
$$

## Theorem 10. The Comparison Test

Let $\sum_n a_n$ be a series with non-negative terms.

1. $\sum_n a_n$ converges if there is a convergent series $\sum c_n$ with $a_n \le c_n$ for all $n>N$, for some integer $N$.
2. $\sum_n a_n$ diverges if there is a divergent series of nonnegative terms $\sum_n d_n$ with $a_n\ge d_n$ for all $n>N$, for some integer $N$.

**Proof.**

### Example 1. Applying the Comparison Test

1. Show the series 

$$
\sum_{n=1}^\infty \frac{5}{5n-1}
$$

diverges.

b. Show the series 

$$
\sum_{n=0}^\infty \frac1{n!}
$$

converges.

c. Show the series 

$$
5 +\frac23 + \frac17 + 1 + \sum_{n=1}^\infty \frac1{2^n+\sqrt{n}}
$$

converges.

## The Limit Comparison Test

Based on the experiences established by the examples, we have a feeling that testing for convergence is largely about finding how fast the $n$th term is approaching $0$. 

## Theorem 11. Limit Comparison Test

Suppose that $a_n>0$ and $b_n>0$ for all $n\ge N$ ($N$ an integer).

1. If

$$
\lim_{n\to \infty}\frac{a_n}{b_n} = c > 0
$$

 then $\sum_n a_n$ and $\sum_n b_n$ both converge or both diverge.

1. If  

$$
\lim_{n\to\infty}\frac{a_n}{b_n}=0,\quad \text{and}\quad \sum_n b_n \, \text{converges}
$$

then $\sum_n a_n$ converges.

1. If 

$$
\lim_{n\to\infty}\frac{a_n}{b_n} = \infty,\quad \text{and}\quad \sum_n b_n \, \text{diverges}
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
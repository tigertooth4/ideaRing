---
title: "W11-S1 Infinite Sequences and Series"
date: 2022-05-05T11:43:25+08:00
draft: false
tags: ["series", "sequence", "converge","diverge", "overview","calculus","lecture"]
---
 

周次: 11
日期: May 6, 2022
节次: 2

In this lecture, we will discuss series and sequences, these are new concept and very important ones. Before talking about series, we will talk about sequences. 


# Overview

In this chapter we study how to add together infinitely many numbers. This is a subject of the theory of **infinite series**. 

It is clear that infinite sum sometimes have a finite value, as in 

$$
\frac12 + \frac14 + \frac18 + \frac1{16} + \cdots = 1
$$

![Untitled](W11-S1%20Infinite%20Sequences%20and%20Series%2018da047d3a0e44259dc04cc8ac2b8c3a/Untitled.png)

Other infinite series do not have a finite sum, as with 

$$
1+2+3+ 4+5 + \cdots
$$

With some infinite series, such as the *harmonic series* 

$$
1+\frac12 + \frac13 + \frac14 + \frac15 +\frac16 + \cdots
$$

it is not obvious whether a finite sum exists. 

To explore such problems, we need to exam the limit for infinite many numbers first. A list of infinite many numbers is called a **sequence**.

# § 11.1. Sequences

## Definition and Examples

A sequence is a list of infinite many numbers 

$$
a_1, a_2, a_3,\cdots, a_n,\cdots
$$

in a given order. Each of $a_1,$ $a_2$, $a_3$ and so on represents a number. These are the **terms** of the sequence. For example the sequence 

$$
2, 3, 5, 7, 11, 13, \cdots
$$

has first term $a_1 = 2$, second term $a_2 = 4$ and $n$th term $a_n$ is the $n$th prime number. The integer $n$ is called the **index** of $a_n$, indicating where $a_n$ occurs in the list. We can think of the sequence as a function of $n$.

### Definition (Infinite Sequence)

An **infinite sequence** of numbers is a function whose domain is the set of positive integers.

### Examples

- The sequence

$$
12, 14, 16, 18, 20, 22, \cdots
$$

is described by the formula $a_n = 10 + 2n$. Or it can be described by the simpler formula $b_n = 2n$, where the index $n$  starts at $6$ and increases. To allow such simpler formulas, we let the first index of the sequence be any integer. 

We denote a sequence by $\{a_n\}$. The order is important. The sequence $1,2,3,4,\cdots$ is not the same as the sequence $2,1,3,4,\cdots$

### Ways to represent sequences

- Sequence can be described by writing rules at specify their terms, such as

$$
a_n =\sqrt{n},\quad b_n = (-1)^{n+1} \frac1n,\quad c_n = \frac{n-1}{n},\quad d_n = (-1)^{n+1}.
$$

or by listing terms, 

$$
\{a_n\} = \{\sqrt1, \sqrt 2, \sqrt 3,\cdots, \sqrt{n},\cdots\}
$$

$$
\{b_n\} = \{1, -\frac12, \frac13, -\frac14,\cdots,(-1)^{n+1}\frac1n,\cdots\}
$$

$$
\{c_n\}=\{0, \frac12, \frac23,\frac34,\cdots, \frac{n-1}{n},\cdots\}
$$

$$
\{d_n\}=\{1,-1,1,-1,1,-1,\cdots, (-1)^{n+1},\cdots\}.
$$

Sometimes write 

$$
\{a_n\} = \{\sqrt{n}\}_{n=1}^\infty.
$$

- Two ways to represent sequences graphically.

![Untitled](W11-S1%20Infinite%20Sequences%20and%20Series%2018da047d3a0e44259dc04cc8ac2b8c3a/Untitled%201.png)

## Convergence and Divergence

Sometimes the number in the sequence approach a single value as the index $n$ increases, as with $\{a_n = \frac1n\}.$  In sequence $\{c_n=\frac{n-1}{n}\}$， terms approach $1$. In sequence $\{d_n = (-1)^{n+1}\}$ the sequence bounce back and forth between $1$ and $-1$, never converging to a single value.

### Definitions (Converges, Diverges, Limit)

The sequence $\{a_n\}$ **converges** to the number $L$ if to every positive number $\epsilon$ there corresponds an integer $N$ such that for all $n>N$ it has 

$$
|a_n-L|< \epsilon.
$$

If no such number $L$ exists, we say that $\{a_n\}$ **diverges.**

If $\{a_n\}$ converges to $L$, we write $\lim_{n\to\infty}a_n= L,$ or simply $a_n\to L$, and call $L$ the **limit** of the sequence.

`**Remark**` The definition is very similar to the definition of the limit of a function $f(x)$ as $x$ approaches $\infty$. We will exploit this connection to calculate limits of sequences.

### Example 1. Applying the definition

Show that 

1. $\lim_{n\to\infty}\frac1n = 0$
2. $\lim_{n\to \infty} c = c$, (for any constant sequence $\{a_n \equiv c\}$)  

### Example 2. A divergent sequence

Show that the sequence $\{1,-1,1,-1,1,-1,\cdots\}$ diverges.

### Example 3. An unbounded sequence diverges

Show that the sequence $\{\sqrt{n}\}_{n=1}^\infty$ diverges.

### Definition (Diverge to Infinity)

The sequence $\{a_n\}$ **diverges to infinity** if for every number $M$ there is an integer $N$ such that for all $n$ larger than $N$, $a_n>M$. If this condition holds we write 

$$
\lim_{n\to \infty} a_n  = \infty,\quad \text{or}\quad a_n\to \infty.
$$

Similarly if for every number $m$ there  is an integer $N$ such that for all $n>N$ we have $a_n<m$, then we say $\{a_n\}$ **diverges to  negative infinity** and write

$$
\lim_{n\to \infty}a_n = -\infty,\quad \text{or} \quad a_n \to -\infty.
$$

`**Remark**` A sequence may diverge without diverging to infinity or negative infinity. As an example $\{1, 0, 2,0, 3,0,\cdots\}$ is also divergence.

## Calculating limits of Sequences

### Theorem 1

Let $\{a_n\}$ and $\{b_n\}$ be sequences of real numbers and let $A$ and $B$ be real numbers. The following rules hold if $\lim_{n\to \infty} a_n = A$ and $\lim_{n\to \infty} b_n = B.$

1. *Linear Rule:*  $\lim_{n\to\infty} (\alpha a_n\pm \beta b_n) = \alpha A \pm \beta B$, for constants $\alpha$ and $\beta$,
2. *Product Rule: $\lim_{n\to\infty}(a_n\cdot b_n) = A\cdot B$,*
3. *Quotient Rule: $\lim_{n\to\infty} \frac{a_n}{b_n} = \frac{A}{B}$* if *$B\neq 0$.*

### Example 3. Applying Theorem 1

By combining Theorem 1 with the limits of Example 1, we have 

1. $\lim_{n\to\infty}\left(-\frac{1}{n}\right) = - \lim_{n\to \infty}\frac{1}{n} = 0$
2. $\lim_{n\to\infty}\left(\frac{n-1}{n}\right) = \lim_{n\to\infty}\left(1-\frac{1}{n}\right) = \lim_n 1 - \lim_n \frac{1}{n} = 1.$
3. $\lim_{n\to\infty}\frac{4-7n^6}{n^6+3} = \lim_{n\to \infty}\frac{4/n^6 - 7}{1+3/n^6} = -7$

**`Remark`** It does not mean if the sum $\{a_n+b_n\}$ has a limit, then $\{a_n\}$ and $\{b_n\}$ both have limits.

**`Remark`** Every non-zero multiple of a divergent sequence $\{a_n\}$ diverges. 

### Theorem 2. The Sandwich Theorem for Sequences

Let $\{a_n\}$, $\{b_n\}$ and $\{c_n\}$ be sequences of real numbers. If $a_n\le b_n\le c_n$ holds for all $n$ beyond some index $N$, and if $\lim_{n\to\infty} a_n = \lim_{n\to\infty} c_n = L$, then $\lim_{n\to\infty}b_n = L$  as well.

**`Remark`** An immediate consequence of **Theorem 2** is that, if $|b_n|\le c_n$ and $c_n\to 0$, then $b_n\to 0$ as well, because $-c_n \le b_n \le c_n$.

### Example 4. Applying the Sandwich Theorem

Since $1/n\to 0$, we know that 

1. $\frac{\cos n}{n} \to 0$
2. $1/2^n\to 0$
3. $(-1)^n \frac1n \to 0$

### Theorem 3. The Continuous Function Theorem for Sequences

Let $\{a_n\}$ be a sequence of real numbers. If $a_n\to L$ and if $f$ is a function that is continuous at $L$ and defined at all $\{a_n\}$, then $f(a_n)\to f(L)$.

### Example 5. Applying Theorem 3

Show that $\sqrt{n/(n+1)}\to 1$.

### Example 6. The Sequence $\{\sqrt[n]{k}\}$

Show that $k^{1/n}\to 0$

## Using l’Hôpital’s Rule

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

## Recursive Definitions

For the sequences that defined **recursively** by giving 

1. The value(s) of the initial term or terms, and 
2. A rule, called a **recursion formula,** for calculating any later term form terms that precede it.

### Example 11. Sequence Constructed Recursively

1. $a_1 = 1$ and $a_n = a_{n-1} + 1$
2. $a_1 = 1$ and $a_n = n\cdot a_{n-1}$
3. $a_1 = a_2 =1$ and $a_{n+1} = a_n + a_{n-1}$ (**Fibonacci numbers**)
4. $x_0=1$ and $x_{n+1} = x_n - \frac{\sin x_n - x_n^2}{\cos x_n - 2 x_n}$ defined a sequence that converges to a solution of the equation $\sin x - x^2 = 0.$

## Bounded Nondecreasing Sequences

An important special type of sequence is one for which each term is at least as large as its predecessor.

### Definition. Nondecreasing Sequence

If a sequence $\{a_n\}$ has the property that $a_n\le a_{n+1}$ for all $n$, then it is called a **nondecreasing sequence.**

### Example 12. Nondecreasing Sequences

1. $1,2,3,\cdots, n,\cdots$
2. $\frac12, \frac23,\frac34,\cdots, \frac{n-1}{n},\cdots$ 
3. $3,3,3,\cdots, 3,\cdots$
4. $\frac21, (\frac32)^2, (\frac43)^3,\cdots, (\frac{n+1}{n})^n,\cdots$

### Definition. Bounded , Upper Bound, Least Upper Bound

A sequence $\{a_n\}$ is **bounded from above** if there exists a number $M$ such that $a_n\le M$ for all $n$. The number $M$ is an **upper bound** for $\{a_n\}$. If $M$ is the *minimum* upper bound among all the upper bounds for $\{a_n\}$, then $M$ is called  **least upper bound** for $\{a_n\}.$

### Example 13. Applying the Definition for Boundedness

1. The sequence $1,2,3,\cdots, n,\cdots$ has no upper bound.
2. $\frac12, \frac23,\frac34,\cdots, \frac{n}{n+1},\cdots$ is bounded above by $M=1.$

A nondecreasing sequence that is bounded from above always has a least upper bound. The existence for the least upper bound is the property of completeness of the real number system. We will prove that if $L$ is the least upper bound then the sequence converges to $L$.

### Proposition.

Suppose $\{a_n\}$ is a nondecreasing sequence with least upper bound $L$, then $\lim_{n\to\infty}a_n = L.$

### Theorem 6. The Nondecreasing Sequence Theorem

A nondecreasing sequence of real numbers converges if and only if it is bounded from above. If a nondecreasing sequence converges, it converges to its least upper bound.

![Untitled](W11-S1%20Infinite%20Sequences%20and%20Series%2018da047d3a0e44259dc04cc8ac2b8c3a/Untitled%202.png)
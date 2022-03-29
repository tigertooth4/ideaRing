---
title: "W6-S1 Integration by Parts and Integration of Rational Functions"
date: 2022-03-29T14:07:16+08:00
draft: false
tags: ["integration-by-parts", "rational", "lecture","calculus","partial-fraction"]
---

周次: 6
日期: March 30, 2022
节次: 1

In this lecture, we’ll learn a new technique for integration, called *Integration by Parts*. The second part of the lecture will be devoted to the partial fractions decomposition of rational functions. By using such technique, we are able to integrate all the rational functions! 


# § 8.2 Integration by Parts

Integration by parts is a technique for simplifying integrals of the form 

$$
\int f(x)g(x)dx.
$$

It is useful when $f$ can be differentiated repeatedly and $g$ can be integrated repeatedly without difficulty. For example the integral $\int x e^x dx$ and $\int e^x \sin(x)d x$ can be such type.

## Product Rule in Integral Form

> **Integration by Parts Formula**
> 

$$
\int u(x)\, v'(x) \, dx = u(x)\, v(x) -\int u'(x) \, v(x) \, dx.
$$

The mindset behind the formula is that to transfer a difficult integration to an easier one. 

Sometimes it is easier to remember the formula if we write it in differential form. 

$$
\int u dv = uv - \int v du.
$$

## Why it works?

The formula for integration by parts is coming from the Product Rule for derivatives 

$$
\frac{d}{dx}\left(u(x) v(x)\right) = u'(x) v(x) + u(x) v'(x).
$$

### Example 1. Using Integration by Parts

Find 

$$
\int x\cos(x) \, dx.
$$

### Example 3. Integral of the Natural Logarithm

Find 

$$
\int \ln(x) dx.
$$

### Example 4. Repeated Use of Integration by Parts

Find 

$$
\int x^2 e^x dx
$$

### Example 5. Solving for the Unknown Integral (An Circling-Back Integration)

Find 

$$
\int e^x \cos(x) dx.
$$

## Evaluating Definite Integrals by Parts

Combining the Fundamental Theorem of Calculus with the Product Rule, we find the following formula for definite integrals 

$$
u(x) v(x) \bigg]_a^b = \int_a^b u'(x) v(x) dx + \int_a^b u(x) v'(x) dx.
$$

Therefore we can find the following integration by parts formula for definite integrals.

> **Integration by Parts Formula for Definite Integrals**
> 

$$
\int_a^b u(x) v'(x) dx= u(x) v(x) \bigg]_a^b - \int_a^b u'(x) v(x) dx.
$$

### Example 6. Finding Area

Find the area of the region bounded by the curve $y=x e^{-x}$ and the $x$-axis from $x=0$ to $x=4.$

![Untitled](W6-S1%20Inte%207b7fe/Untitled.png)

### Example 7. Repeating Multiple Times. Ft. The Tabular Integration Method

Find 

$$
\int x^3 \sin(x) dx.
$$

![Untitled](W6-S1%20Inte%207b7fe/Untitled%201.png)

### Example 9. A Reduction Formula (Iterative Formulas)

Find the integral 

$$
I_n = \int \cos^n(x) dx
$$

### Example 10. Using the Reduction Formula

Find 

$$
\int \cos^3(x) dx.
$$

# § 8.3 Integration of Rational Functions by Partial Fractions

This section shows how to express a rational function as a sum of simpler fractions, called *the method of  partial fractions,* which are easily integrated. For example 

$$
\dfrac{5x-3}{x^2-2x -3} = \dfrac{2}{x+1}  + \dfrac{3}{x-3}.
$$

By doing so, an anti-derivative can be found easily. 

$$
\int \dfrac{5x-3}{x^2-2x-3} dx = 2\ln|x+1| + 3\ln|x-3| + C.
$$

`**Note` Any rational function can be integrated by using this method!**

## The General Description of the Method

The method is not a guess work. Its efficiency can be proved rigorously. To show case by the previous example, for 

$$
\dfrac{5x-3}{x^2-2x-3}
$$

we first remark on the degrees: the degree of $5x-3$ is lower than the degree of $x^2-2x-3$, which is good! Then, factoring $x^2-2x-3$ gives two factors $x+1$ and $x-3$. Therefore, we can pretend the rational function is a linear combination of partial fractions 

$$
\dfrac{5x-3}{x^2-2x-3} = \dfrac{A}{x+1}+\dfrac{B}{x-3}.
$$

We call $A$ and $B$ **undetermined coefficients.** 

To find $A$ and $B$, simply clear the above fractions, and compare the coefficients of like powers of $x$ on the two-sides.  

$$
A+B = 5,\quad -3A + B = -3.
$$

Solving these equations simultaneously gives $A=2$  and $B=3.$

## Method of Partial Fractions ( for $f(x)/g(x)$ Proper)

1. Factorize the denominator $g(x)$, obtain all its linear and quadratic factors, as well as their powers. In general, the denominator has the factorization looks like  

$$
\dfrac{f(x)}{g(x)} = \dfrac{f(x)}{(x-r_1)^{m_1}\cdots (x-r_k)^{m_k} (x^2+p_1 x + q_1)^{n_1}\cdots(x^2+p_l x + q_l)^{n_l}}
$$

where all the linear and quadratic factors are distinct. And $x^2+p_i x +q_i$ should not be factorized anymore ( called *irreducible* ). 

`**Note` The feasibility of this factorization is guaranteed  by the Fundamental Theorem of Algebra.** 

1. For each linear factor   $(x-r)^m$ of $g(x)$,  the fraction $f(x)/g(x)$ should include the following partial fractions, with undetermined coefficients $A_k$.

$$
\dfrac{A_1}{(x-r)} + \dfrac{A_2}{(x-r)^2} + \cdots \dfrac{A_m}{(x-r)^m}
$$

1. For each quadratic factor  $(x^2+px+q)^n$ of $g(x)$, the obtained partial fractions should include  

$$
\dfrac{B_1 x + C_1}{x^2+px+q} + \dfrac{B_2 x + C_2}{(x^2+px+q)^2} +\cdots + \dfrac{B_n x + C_n}{(x^2+px+q)^n}
$$

1. Set the original fraction $f(x)/g(x)$ equal to the sum of all these partial fractions. Clear the resulting equation of fractions and arrange the terms in decreasing powers of $x$.
2. Equate the coefficients of corresponding powers of $x$ and solve the resulting equations for the undetermined coefficients.

### Example 1. Distinct Linear Factors

Evaluate 

$$
\int \dfrac{x^2+4x+1}{(x-1)(x+1)(x+3)}dx
$$

using partial fractions. 

( Solution: $\frac34 \ln|x-1|+\frac12\ln |x+1| -\frac14 \ln |x+3| + C$ .)

### Example 2. A Repeated Linear Factor

Evaluate 

$$
\int \dfrac{6x+7}{(x+2)^2}dx
$$

( Solution: $6\ln|x+2| + \frac{5}{x+2} + C$ )

### Example 3. Integrating an Improper Fraction

Evaluate 

$$
\int \dfrac{2x^3-4x^2-x-3}{x^2-2x-3}dx
$$

( Solution: $x^2 + 2\ln |x+1| + 3\ln |x-3| + C$ )

### Example 4. Integrating with an Irreducible Quadratic Factor

Evaluate 

$$
\int \dfrac{-2x+4}{(x^2+1)(x-1)^2}dx
$$

(Solution: $\ln(x^2+1) + \arctan x - 2\ln|x-1| - \frac1{x-1} + C$  )

### Example 5. A Repeated Irreducible Quadratic Factor

Evaluate

$$
\int \dfrac{dx}{x(x^2+1)^2}.
$$

( Solution: $\ln \dfrac{|x|}{\sqrt{x^2+1}} + \dfrac1{2(x^2+1)} + C.$  ) 

## The Heaviside “Cover-up” Method for Linear Factors

For proper fraction $f(x)/g(x)$, if $g(x) = (x-r_1) (x-r_2) \cdots (x-r_n)$ is a product of $n$ distinct linear factors, each raised to the first power, there is a quick way to find the undetermined coefficients. 

### Learn Heaviside  “Cover-up” Method by Example

Find $A$, $B$ and $C$ in the partial-fraction expansion 

$$
\dfrac{x^2+1}{(x-1)(x-2)(x-3)}= \dfrac{A}{x-1} + \dfrac{B}{x-2} + \dfrac{C}{x-3}.
$$

### Example 7.  Integrating with the Heaviside Method

Evaluate 

$$
\int \dfrac{x+4}{x^3+3x^2-10 x}dx.
$$

( Solution : $-\frac25 \ln |x| + \frac37 \ln |x-2| - \frac1{35} \ln |x+5| + C$. )

## Other ways to Determine the Coefficients

### Example 8.  Using Differentiation

Find $A$, $B$ and $C$ in the equation 

$$
\frac{x-1}{(x+1)^3}= \dfrac{A}{x+1} + \dfrac{B}{(x+1)^2} + \dfrac{C}{(x+1)^3}.
$$

( Solution : $A=0$, $B=1$ , $C=-2$ )

### Example 9. Assigning Numerical Values to $x$ (Equivalent to “Cover-up” Method)

Find $A$, $B$ and $C$ in 

$$
\dfrac{x^2+1}{(x-1)(x-2)(x-3)} = \dfrac{A}{x-1} + \dfrac{B}{x-2} + \dfrac{C}{x-3}
$$

( Solution : $A=1$, $B=-5$, $C=5$ )
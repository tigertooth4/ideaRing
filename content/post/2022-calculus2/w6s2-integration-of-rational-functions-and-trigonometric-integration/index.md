---
title: "W6-S2 Integration of Rational Functions and Trigonometric Integrals"
date: 2022-03-31T11:42:35+08:00
draft: false
tags: ["rational", "integration", "trigonometric", "calculus","lecture"]
---

周次: 6
日期: April 1, 2022
节次: 2

In this lecture, we continue presenting the integration of rational functions. After finishing this part, we are going to discuss some trigonometric integration techniques. 

# Outline

# § 8.3 Integration of Rational Functions

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

# § 8.4 Trigonometric Integrals

In this section, we consider the integrals involving algebraic combinations of the six basic trigonometric functions. For example the integration $\int \sec^2(x) dx$ , $\int \sec^3(x) \cot(x) dx$ etc.

## Products of Powers of Sines and Cosines

 Consider the integrals of the form 

$$
\int \sin^m(x)\cos^n(x) dx
$$

where $m$ and $n$ are nonnegative integers. 

### Case 1.  If $m$ is odd, set $m = 2k+1$

$$
\int \sin^m(x) \cos^n(x)dx = -\int \sin^{2k}(x) \cos^n(x) d(\cos x)
$$

It suggests changing $\sin^2(x)$  by $1-\cos^2(x)$ then the integration is reduced to a polynomial in $\cos(x)$ 

$$
-\int \left(1-\cos^2 x\right)^k \cos^n (x) d(\cos x)
$$

### Case 2. If $n$ is odd,  set $n=2l+1$

Then similarly, we can change 

$$
\int \sin^m(x) \cos^n(x) dx = \int \sin^m (x) \cos^{2l}(x) d(\sin x) = \int \sin ^m(x) \left(1-\sin^2 x\right)^l d(\sin x)
$$

Then integrated by the substitution $y=\sin(x)$.

### Case 3. If both $m$ and $n$ are even

In this case we use the substitution 

$$
\sin^2(x) = \dfrac{1-\cos 2x}{2},\quad \cos^2(x) = \dfrac{1+\cos 2x}{2}
$$

to reduce the integrand to one in lower powers of $\cos 2x$.

### Example 1.  $m$ is odd

Evaluate 

$$
\int \sin^3 x \cos^2 x dx.
$$

(Solution : $\frac15 \cos^5 x - \frac13 \cos^3 x + C.$ )

### Example 2.  $m$ is even, $n$ is odd

Evaluate 

$$
\int \sin^2 x \cos^5 x dx
$$

Solution.

### Example 3. $m$ and $n$ are both even

Evaluate 

$$
\int \sin^2(x) \cos^4(x) dx
$$

(Solution: $\frac1{16} \left(x - \frac14 \sin 4x + \frac13 \sin^3(2x)\right) + C$ )

## Eliminating Square Roots

Sometimes we can use the identity 

$$
\cos^2 x = \dfrac{1+\cos 2x}{2}
$$

to eliminate a square root. 

### Example 4.

Evaluate 

$$
\int_0^{\pi/4}\sqrt{1+\cos 4x }dx.
$$

( Solution: $\frac{\sqrt2}{2}$ )

## Integrals of Powers of $\tan x$ and $\sec x$

To integrate higher powers of $\tan x$ and $\sec x$, we use the identities $\tan^2 x = \sec^2 x -1$ and $\sec^2 x = \tan^2 +1$ to reduce the higher powers to lower powers. 

### Example 5.

Evaluate 

$$
\int \tan^4 x dx.
$$

( Solution: $\frac13 \tan^3 x - \tan x + x + C$ )

### Example 6.

Evaluate 

$$
\int \sec^3 x dx.
$$

( Solution: $\frac12 \sec x  \tan x + \frac12 \ln |\sec x + \tan x| + C.$ )

## Products of Sines and Cosines

The integrals 

$$
\int \sin mx \sin nx \, dx, \quad \int \sin mx \cos nx \, dx, \quad \text{and} \int \cos mx \cos nx\, dx
$$

can be evaluated by integration by parts. But also more conveniently by using the following identities 

$$
\sin mx \sin nx = - \frac12 \left[\cos (m+n) x -\cos (m-n) x\right]
$$

$$
\sin mx \cos nx = \frac12 \left[\sin(m-n) x + \sin (m+n) x\right]
$$

$$
\cos mx \cos nx = \frac12 \left[\cos (m-n) x + \cos (m+n) x\right]
$$

### Example 7.

Evaluate 

$$
\int \sin 3x \cos 5x\, dx
$$

(Solution: $-\frac{\cos 8x}{16} + \frac{\cos 2x }{4} +C$  )
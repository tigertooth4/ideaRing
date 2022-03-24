---
title: "W5-S2 Integration Techniques"
date: 2022-03-24T11:20:27+08:00
draft: false
tags: ["integration","Integration-by-parts", "calculus", "lecture", "techniques"]
---


周次: 5
日期: March 25, 2022
节次: 2

In this course, we will discuss the definition of hyperbolic functions. And we shift our attention to several integration techniques. These techniques can help us integrate more functions. A typical technique called “Integration by Parts” will be discussed as well. 


# § 7.8 A Brief Introduction on Hyperbolic Functions

Let’s recall the odd and even functions. We have stated that for every function $f$ defined on an interval centered at the origin can be written in a unique way as the sum of one even function and one odd function. The decomposition is 

$$
f(x) = \underbrace{\frac{f(x) + f(-x)}{2}}_{\text{even part}} + \underbrace{\frac{f(x)-f(-x)}{2}}_{\text{odd part}}
$$

No exception for exponential function $e^x$ , it can be decomposed. And we assigned two new functions to the decomposition.

$$
\cosh(x) := \text{even part of }e^x = \frac{e^x + e^{-x}}{2}
$$

$$
\sinh(x) := \text{odd part of }e^x = \frac{e^x - e^{-x}}{2}
$$

$\cosh(x)$ is pronounced as “kosh $x$”, rhyming with “gosh $x$”, and $\sinh(x)$ is pronounced as “cinch $x$”, rhyming with “pinch $x$”.

## Graphs of Hyperbolic Functions

![Untitled](W5-S2%20Inte%20f45f7/Untitled.png)

![Untitled](W5-S2%20Inte%20f45f7/Untitled%201.png)

## Identities for Hyperbolic Functions

$$
\cosh^2(x) - \sinh^2(x) = 1
$$

$$
\sinh(2x) = 2\sinh(x)\cosh(x)
$$

$$
\cosh(2x) = \cosh^2(x) + \sinh^2(x)
$$

## Other Hyperbolic Functions

Analogous to trigonometric functions, the $\tanh(x)$, $\coth(x)$, $\mathrm{sech}(x)$ and $\mathrm{csch}(x)$ can all be defined, following the same pattern. 

$$
\tanh(x) :=\dfrac{\sinh(x)}{\cosh(x)},\quad \coth(x):=\dfrac{\cosh(x)}{\sinh(x)}, \quad \text{etc.}
$$

## The Derivative and Anti-derivative of Hyperbolic Functions

$$
\frac{d}{dx}\sinh(x) = \cosh(x),\quad \frac{d}{dx}\cosh(x) = \sinh(x)
$$

Therefore the anti-derivatives read

$$
\int\sinh(x) = \cosh(x) + C,\quad \int\cosh(x) = \sinh(x) + C.
$$

# Chapter 8. Techniques of Integration

In this chapter we study a number of important techniques for finding indefinite integrals of more complicated functions 

## § 8.1 Basic Integration Formulas

 Try to match integrals that confront us against one of the standard types. This usually involves a certain amount of algebraic manipulation as well as use of the substitution rules.

Recall that the substitution rule is 

$$
\int f(g(x))g'(x)dx = \int f(u) du,
$$

where $u=g(x)$ is a differentiable function whose range is an interval $I$ and $f$ is continuous on $I.$ Success in integration often hinges on the ability to spot what part of the integrand should be called $u$ in order that one will also have $du$, so that a known formula can be applied. This means that the first requirement for skill in integration is a thorough mastery of the formulas for differentiation.

![Untitled](W5-S2%20Inte%20f45f7/Untitled%202.png)

`**Note`** Students should have a good mastery of formulas 12, 13, 18, 19. For 20 and 22, we provide an alternative (equivalent) anti-derivative 

$$
\int\dfrac{du}{\sqrt{u^2\pm a^2}} = \ln |u+\sqrt{u^2\pm a^2}| + C
$$

For 20, we have an alternative way to show the anti-derivative, by applying the integration table.

$$
\int\dfrac{du}{u\sqrt{u^2-a^2}} = \int \dfrac{du}{u^2\sqrt{1-\left(\frac{a}{u}\right)^2}}=-\frac1a\int \dfrac{d\left(\frac{a}u\right)}{\sqrt{1-\left(\frac{a}{u}\right)^2}}=-\frac1a \arcsin\left(\frac{a}{u}\right) + C
$$

### Example 1. Making a Simplifying Substitution

Evaluate 

$$
\int\dfrac{2x-9}{\sqrt{x^2-9x+1}}dx
$$

### Example 2. Completing the Square

Evaluate 

$$
\int\dfrac{dx}{\sqrt{8x-x^2}}dx
$$

### Example 3. Expanding a Power and Using a Trigonometric Identity

Evaluate 

$$
\int (\sec x + \tan x)^2 dx.
$$

### Example 4. Eliminating a Square Root

Evaluate 

$$
\int_0^{\pi/4} \sqrt{1+\cos 4x} \,dx.
$$

### Example 5. Reducing an Improper Fraction

Evaluate 

$$
\int \dfrac{3x^2-7x}{3x+2}\,dx.
$$

### Example 6. Separating a Fraction

Evaluate 

$$
\int \dfrac{3x+2}{\sqrt{1-x^2}}\,dx.
$$

### Example 7. Integral of $y=\sec(x)$ — Multiplying by a Form of $1$

Evaluate

$$
\int \sec x \,\,dx
$$

Similarly, one can find 

$$
\int \csc x\,\, dx
$$

![Untitled](W5-S2%20Inte%20f45f7/Untitled%203.png)

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

![Untitled](W5-S2%20Inte%20f45f7/Untitled%204.png)

### Example 7. Repeating Multiple Times. Ft. The Tabular Integration Method

Find 

$$
\int x^3 \sin(x) dx.
$$

![Untitled](W5-S2%20Inte%20f45f7/Untitled%205.png)

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
---
title: "W5-S1 Transcendental Functions (3) and Integration Techniques"
date: 2022-03-22T15:10:00+08:00
draft: false
tags: ["transcendental", "calculus", "integration", "technique", "inverse","trigonometric", "hyperbolic"]
---

周次: 5
日期: March 23, 2022
节次: 1

In this lecture, we define the inverse trigonometric functions, and develop some basic properties. The properties we are focusing on are the differentiation and integration properties. A brief introduction on hyperbolic functions, in particular the hyperbolic cosine and hyperbolic sine functions are given. 

As the second half, we discuss some integration techniques. Those techniques could help us to find more anti-derivatives and as a result, evaluate more definite integrals.


# § 7.7 Inverse Trigonometric Functions

The six basic trigonometric functions are not one-to-one. However, we can restrict their domain to intervals on which they are one-to-one. The sine function increases from $-1$ at $x=-\pi/2$ to $1$ when $x=\pi/2$. By restricting its domain to the interval $[-\pi/2,\pi/2]$ we make it one-to-one, so it has an inverse $\sin^{-1}(x)$.

![Untitled](W5-S1%20Tran%208d9bc/Untitled.png)

The cosine function is one-to-one on $[0,\pi]$.

![Untitled](W5-S1%20Tran%208d9bc/Untitled%201.png)

The tangent function is one-to-one on $(-\pi/2,\pi/2)$.

![Untitled](W5-S1%20Tran%208d9bc/Untitled%202.png)

The cotangent function is  one-to-one on $(0,\pi)$.

![Untitled](W5-S1%20Tran%208d9bc/Untitled%203.png)

The secant function is one-to-one on $[0,\pi/2)\cup (\pi/2,\pi]$.

![Untitled](W5-S1%20Tran%208d9bc/Untitled%204.png)

The cosecant function is one-to-one on $[-\pi/2,0)\cup(0,\pi/2].$

![Untitled](W5-S1%20Tran%208d9bc/Untitled%205.png)

Those restricted trigonometric functions have inverses, denoted by (arc). So we have $\arcsin(x)$, $\arccos(x)$, $\arctan(x)$, $\mathrm{arccot}(x)$, $\mathrm{arcsec}(x)$ and $\mathrm{arccsc}(x)$. 

## The Arcsine and Arccosine Functions

> **Definition.**  **Arcsine and Arccosine Functions**
> 
- $y=\sin^{-1}(x)=\arcsin(x)$ is the angle in $[-\pi/2,\pi/2]$ whose sine is $x$.
- $y=\cos^{-1}(x) = \arccos(x)$ is the angle in $[0,\pi]$ whose cosine is $x$.

![Sine (blue) and arcsine (yellow) functions ](W5-S1%20Tran%208d9bc/Untitled%206.png)

Sine (blue) and arcsine (yellow) functions 

The graph of $y=\arcsin(x)$ is symmetric about the origin, therefore an odd function. 

$$
\arcsin(-x) = -\arcsin(x).
$$

![Cosine (blue) and arccosine (yellow) functions](W5-S1%20Tran%208d9bc/Untitled%207.png)

Cosine (blue) and arccosine (yellow) functions

The graph of $y=\arccos(x)$ does not have symmetry about the origin or about the $y$-axis.

### Example 1. Common values of arcsine function

- $\arcsin(\frac12) = \frac\pi6$ ; $\arcsin(\frac{\sqrt{3}}{2}) = \frac{\pi}{3}; \arcsin(\frac{\sqrt{2}}{2}) = \frac\pi 4.$
- $\arcsin(0) = 0$; $\arcsin(1) = \frac\pi2$; $\arcsin(-1) = -\frac\pi2.$

### Example 2. Common values of arccosine function

- $\arccos(\frac12) = \frac\pi3$; $\arccos(\frac{\sqrt3}{2}) = \frac\pi 6$; $\arccos(\frac{\sqrt2}{2}) = \frac{\pi}{4}.$
- $\arccos(0) = \frac{\pi}{2};$ $\arccos(1) = 0$; $\arccos(-1) = \pi$.

## Identities Involving Arcsine and Arccosine

> **Basic Identities**
> 

Since $\cos(\pi-x) = -\cos(x)$, we have 

$$
\arccos(-x) = \pi - \arccos(x),\quad \text{or}\quad \arccos(x) + \arccos(-x) = \pi.
$$

Since $\cos(\frac\pi2-x) = \sin(x),$ we have

$$
\arcsin(x) = \frac{\pi}2 - \arccos(x), \quad or \quad \arcsin(x) + \arccos(x) = \frac\pi2.
$$

## Inverses of $\tan(x)$, $\cot(x)$, $\sec(x)$ ,and $\csc(x)$

> **Definition. Arctangent and Arccotangent Function**
> 
- $y=\arctan(x)$ is the angle in $(-\pi/2,\pi/2)$ for which $\tan(y) = x$
- $y=\mathrm{arccot}(x)$ is the angle in  $(0,\pi)$ for which $\cot(y) =x.$

![The graph of arctan(x)](W5-S1%20Tran%208d9bc/Untitled%208.png)

The graph of arctan(x)

The graph of $\arctan(x)$ is symmetric with respect to the origin. Namely, And $\mathrm{arccot}(x)$ has no such symmetries.

$$
\tan(-x) = - \tan(x).
$$

![The graph of arccot(x)](W5-S1%20Tran%208d9bc/Untitled%209.png)

The graph of arccot(x)

### Example 3. Common Values of Arctangent Function

- $\arctan(\frac1{\sqrt{3}}) = \frac\pi6$; $\arctan(\pm\sqrt{3}) = \pm \frac{\pi}{3}.$

### Example 4. Find $\cos(\alpha)$, $\tan(\alpha)$, $\sec(\alpha)$, if

$$
\alpha = \arcsin\left(\frac23\right)
$$

### Example 5. Find $\sec(\arctan\frac{x}{3})$

## The Derivative of Arcsine Function

Find $\frac{d}{dx} \arcsin(x)$ by using the formula 

$$
\frac{d}{dx} f^{-1}(x) = \frac{1}{f'(f^{-1}(x))}
$$

The Chain Rule shows 

$$
\frac{d}{dx}\arcsin (g(x)) = 
$$

### Example 7. Applying the Derivative Formula

$$
\frac{d}{dx} \arcsin(x^2) = 
$$

## The Derivative of Arctangent Function

Find $\frac{d}{dx} \arctan(x) =$ 

## Derivatives of the Other Two

> **Inverse Function-Inverse Cofunction Identities**
> 

$$
\arccos(x) = \frac{\pi}{2} - \arcsin(x),\\ \mathrm{arccot}(x) =\frac{\pi}{2}-\arctan(x)
$$

Thus 

$$
\frac{d}{dx} \arccos(x) = -\frac{1}{\sqrt{1-x^2}},\\ \frac{d}{dx}\mathrm{arccot}(x) = -\frac{1}{1+x^2}
$$

### Example 10. A Tangent Line to the Arccotangent Curve

Find an equation for the line tangent to the graph of $y=\mathrm{arccot}(x)$ at $x=-1$.

### Derivatives Table

![Untitled](W5-S1%20Tran%208d9bc/Untitled%2010.png)

## Integration Formulas

> **The Integration Formulas**
> 

$$
\int \frac{1}{\sqrt{1-x^2}}dx = \arcsin(x) + C
$$

$$
\int\frac{1}{1+x^2}dx = \arctan(x) + C
$$

For integrations like $\int\frac{1}{\sqrt{a^2-x^2}}dx$ and $\int \frac{1}{a^2+x^2} dx$, we can use substitution of variables 

$$
\int\frac{1}{\sqrt{a^2-x^2}}dx = \int\frac{1}{a\sqrt{1-(x/a)^2}}dx = \int\frac{d(x/a)}{\sqrt{1-(x/a)^2}} = \arcsin(x/a) + C
$$

Similarly, 

$$
\int\frac{1}{a^2+x^2}dx = \frac1a \arctan(x/a) + C.
$$

### Example 11. Using the Integral Formulas

1. $\int_{\sqrt2/2}^{\sqrt3/2}\frac{dx}{\sqrt{1-x^2}} = \frac{\pi}{2}$
2. $\int_0^1 \frac{dx}{1+x^2} = \frac{\pi}{4}$
3. $\int\frac{dx}{\sqrt{9-x^2}}$ 
4. $\int\frac{dx}{\sqrt{3-4x^2}}$

### Example 13. Completing the Square

- Evaluate

$$
\int \frac{dx}{\sqrt{4x-x^2}}.
$$

- Evaluate

$$
\int \frac{dx}{4x^2+4x + 2}.
$$

### Example 15. Using Substitution

Evaluate 

$$
\int\frac{dx}{\sqrt{e^{2x} - 6}}.
$$

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

![Untitled](W5-S1%20Tran%208d9bc/Untitled%2011.png)

![Untitled](W5-S1%20Tran%208d9bc/Untitled%2012.png)

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

![Untitled](W5-S1%20Tran%208d9bc/Untitled%2013.png)

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

![Untitled](W5-S1%20Tran%208d9bc/Untitled%2014.png)
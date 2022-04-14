---
title: "W8-S2 Improper Integrals and Differential Equations"
date: 2022-04-14T12:36:20+08:00
draft: false
tags: ["Improper Integral", "Convergence", "Divergence", "calculus", "lecture","Differential Eqaution", "Slope field"]
---

周次: 8
日期: April 15, 2022
节次: 2

In this lecture, we discuss the improper integral of type II, as well as the convergence test for improper integral of type I with non-negative integrands. In the section part, we will talk about the simplest differential equations, the geometric visualization of a differential equation with slope fields, and separable equations.


## Type II Improper Integrals

**Definition.** Integrals of functions that becomes infinite at a point within the interval of integration are **Improper integrals of Type II.**

1. If $f(x)$ is continuous on $(a,b]$ and is discontinuous at $a$ then 

$$
\int_a^b f(x)dx := \lim_{h\to 0^+}\int_{a+h}^b f(x)dx.
$$

![plot4.png](W8-S2%20Impr%20699d7/plot4.png)

1. If $f(x)$ is continuous on $[a,b)$ and is discontinuous at $b$, then 

$$
\int_a^b f(x)dx :=\lim_{h\to0^+}\int_a^{b-h}f(x)dx.
$$

![plot5.png](W8-S2%20Impr%20699d7/plot5.png)

1. If $f(x)$ is discontinuous at $c$, where $a<c<b$, and continuous on $[a,c)\cup (c,b]$, then 

$$
\int_a^bf(x)dx :=\lim_{h\to0^+}\int_a^{c-h} f(x)dx + \lim_{s\to0^+}\int_{c+s}^b f(x)dx.
$$

![plot6.png](W8-S2%20Impr%20699d7/plot6.png)

In each case, if the limit is finite we say the improper integral **converges** and that the limit is the **value** of the improper integral. If the limit does not exist, the integral **diverges**.

**`Note` In Part 3, the integral on the left side of equation converges if *both* integrals on the right side converge; otherwise it diverges.**

### Example 4. A Divergent Improper Integral

Investigate the convergence of 

$$
\int_0^1 \dfrac{1}{1-x}dx.
$$

![Untitled](W8-S2%20Impr%20699d7/Untitled.png)

**Solution.**

### Example 5. Vertical Asymptote at an Interior Point

Evaluate 

$$
\int_0^3 \dfrac{dx}{(x-1)^{2/3}}dx
$$

![Untitled](W8-S2%20Impr%20699d7/Untitled%201.png)

**Solution.**

### Example 6. A Convergent Improper integral

Evaluate

$$
\int_2^\infty \dfrac{x+3}{(x-1)(x^2+1)}dx.
$$

### Example 7. Finding the Volume of an Infinite Solid

![Untitled](W8-S2%20Impr%20699d7/Untitled%202.png)

The cross-sections of the solid horn in this graph perpendicular to the $x$-axis are circular disks with diameters reaching from the $x$-axis to the curve $y=e^x$, $-\infty<x\le \ln2.$ Find the volume of the horn.

**Solution.**

### Example 8. An Incorrect Calculation

$$
\int_0^3 \dfrac{dx}{x-1} = \ln |x-1|\bigg]_{0}^3 = \ln 2- \ln 1 = \ln 2.
$$

This example illustrates what can go wrong if you mistake an improper integral for an ordinary integral. Whenever you encounter an integral $\int_a^b f(x)dx$  you **MUST** examine the function $f$ on $[a,b]$ and then decide if the integral is improper. If $f$ is continuous on $[a,b]$, it will be proper, an ordinary integral.

# Test for Convergence and Divergence

Sometimes, the integral might be very hard to evaluate directly. A good strategy is trying to determine whether it converges or diverges. Then if it is converges, we can evaluate numerically to get an approximation at least. 

The principal tests for convergence of divergence are the **Direct Comparison Test** and the **Limit Comparison Test.**

**`Note`**  The following tests only works for non-negative or non-positive functions.

### Example 9. Investigating Convergence

![Untitled](W8-S2%20Impr%20699d7/Untitled%203.png)

Does the integral $\int_1^\infty e^{-x^2}dx$ converge? 

**`Solution.`**

## Theorem 1. Direct Comparison Test

Let $f$ and $g$ be continuous on $[a,+\infty)$ with $0\le f(x)\le g(x)$ for all $x\ge a$. Then 

1. $\int_a^\infty f(x)dx$  converges if $\int_a^\infty g(x)dx$ does,
2. $\int_a^\infty g(x)dx$ diverges if $\int_a^\infty f(x)dx$  does.

**`Proof.`**

### Example 10. Using the Direct Comparison Test

$$
(a)\qquad\qquad\qquad \int_1^\infty \dfrac{\sin^2 x}{x^2} dx\quad \text{converges}
$$

$$
(b) \qquad\qquad\qquad\int_1^\infty \dfrac{1}{\sqrt{x^2-0.1}}dx\qquad \text{diverges}
$$

## Theorem 2. Limit Comparison Test

If the positive functions $f$ and $g$ are continuous on $[a,+\infty)$ and if 

$$
\lim_{x\to+\infty}\dfrac{f(x)}{g(x)} = L,\qquad 0<L<\infty ,
$$

then 

$$
\int_a^\infty f(x)dx\quad \text{and} \quad \int_a^\infty g(x)dx 
$$

both converge or both diverge.

**`Sketch for the proof.`**

### Example 11. Using the Limit Comparison Test

Show that 

$$
\int_1^\infty \dfrac{dx}{1+x^2}
$$

converges by comparison with $\int_1^\infty \frac{dx}{x^2}$. Find and compare the two integral values.

### Example 12. using the Limit Comparison Test

Show that 

$$
\int_1^\infty \dfrac{3}{e^x+5}dx
$$

converges.

# Chapter 9.  Further Applications of Integration

## Overview.

Previously we’ve learned anti-derivative. For a continuous function $f$, we found the general solution $F(x)$, whose derivative is $f(x)$, can be expressed by indefinite integral $\int f(x)dx$.

Another view for the concept of anti-derivative, is that we are solving an equation related with function $f$ and an unknown function $F$, such that  

$$
\frac{d F}{dx} = f(x).
$$

Any equation involving the derivative for unknown functions can be called a differential equation. Therefore what we did, was to solve a simplest differential equation. 

In this chapter, we study several more involved differential equations, having the form 

$$
\frac{dy}{dx} = f(x,y),
$$

where $f$ is a function of *both* the independent and dependent variables. We use the theory of indefinite integration to solve these differential equations, and investigate analytic, graphical and numerical solution methods.

# § 9.1 Slope Fields and *Separable* Differential Equations

## General First-Order Differential Equations and Solutions.

**Definition.** A **First-order differential equation**  is an equation 

$$
\begin{equation}\frac{dy}{dx} = f(x,y)\end{equation}
$$

in which $f(x,y)$ is a function of $x$ and $y$ defined on a region in the $xy$-plane.

The term “first-order”, refers to the highest order of derivative is having order $1$ in the equation.

**Definition.** A **Solution** of equation (1) is a differentiable function $y=y(x)$ defined on an interval $I$ of $x$-values such that 

$$
\frac{d}{dx}y(x) = f(x,y(x))
$$

on that interval. 

**Definition.** A **general solution** to equation (1) is a solution that contains all possible solutions. It may contain arbitrary constants, so that when constants are being fixed, then we get a particular solution.

### Example 1. Verifying Solution Functions

Show that every member of the family of functions 

$$
y=\frac{C}{x}+2
$$

is a solution of the first-order differential equation 

$$
\frac{dy}{dx} = \frac1x(2-y),\quad \text{on } (0,\infty)
$$

![Untitled](W8-S2%20Impr%20699d7/Untitled%204.png)

Sometimes we need a  *particular* solution rather than the general one to a differential equation 

$y' = f(x,y).$ The **particular solution** satisfying the initial condition $y(x_0) = y_0$ is the solution for differential equation, whose value at $x_0$ is $y_0$. Thus the graph of the particular solution passes through the point $(x_0,y_0)$ in the $xy$-plane. 

The **first-order initial value problem** is a differential equation $y'=f(x,y)$ whose solution must satisfy an initial condition $y(x_0) =y_0.$

### Example 2. Verifying That  a Function Is a Particular Solution

Show that the function 

$$
y=(x+1)-\frac13 e^x
$$

is a solution to the first-order initial value problem 

$$
\frac{dy}{dx} = y-x,\quad y(0)=\frac23.
$$

![Untitled](W8-S2%20Impr%20699d7/Untitled%205.png)

## Slope Fields: Viewing Solution Curves

Any particular solution to a differential equation can be viewed as a graph, a plane curve, at every point $(x,y)$ of the curve, the slope for the curve has been assigned with the value $f(x,y)$.

Indeed, before solving the differential equation, we could illustrate the slope for each point on the plane by line segments. Each line segment has the slope indicating by $f(x,y)$. The resulting picture with those line segments is called a **slope field ( or direction field)** and gives a visualization for the general shape of the solution curves.

![Untitled](W8-S2%20Impr%20699d7/Untitled%206.png)

### Slope Field and General Solutions

Here are some of the slope fields for particular $f(x,y)$ functions.

![Untitled](W8-S2%20Impr%20699d7/Untitled%207.png)

![Untitled](W8-S2%20Impr%20699d7/Untitled%208.png)

![Untitled](W8-S2%20Impr%20699d7/Untitled%209.png)

### For Example 1

![Untitled](W8-S2%20Impr%20699d7/Untitled%2010.png)

![Untitled](W8-S2%20Impr%20699d7/Untitled%2011.png)

### For Example 2

![Untitled](W8-S2%20Impr%20699d7/Untitled%2012.png)

![Untitled](W8-S2%20Impr%20699d7/Untitled%2013.png)

## Separable Equations

In the equation $y'(x) =f(x,y)$, if $f$ can be expressed as a product of two functions, one is a function of $x$, the other is a function of $y$, then the differential equation will be called separable. It has the following form

$$
\frac{dy}{dx} = g(x) H(y).
$$

For our convenience, let’s rewrite it in the form 

$$
\frac{dy}{dx} = \frac{g(x)}{h(y)}.
$$

Moving terms with different variables to different sides, then we get 

$$
h(y) dy = g(x) dx.
$$

Then we simply integrate both sides of this equation: 

$$
\begin{equation}\int h(y)dy = \int g(x) dx.\end{equation}
$$

Equation (2) indication an implicit relation between $x$ and $y$, i.e. $H(y) = G(x)$. Then a general hope is to solve $y$ explicitly to get a solution in a “regular” form. 

### The Justification

To justify the procedure, we use the differential relation $dy/dx = g(x)/h(y)$.  For any solution $y(x)$ to the differential equation, the integral of $h(y)$ will satisfy the following 

$$
\int h(y) dy = \int h(y(x)) y'(x) dx = \int h(y(x))\frac{g(x)}{h(y(x))}dx = \int g(x) dx.
$$

### Example 3. Solving a Separable Equation

Solving the differential equation 

$$
\frac{dy}{dx} = (1+y^2) e^x.
$$

### Example 4. Solve the equation

$$
(x+1)\frac{dy}{dx}  = x(y^2+1).
$$

### Example 5. The Initial Value Problem

$$
\frac{dy}{dx} = ky,\quad y(0) = y_0.
$$

### Torricelli’s Law

If you drain a tank, the rate at which the water runs out is a constant times the square root of the water’s depth $x.$ the constant depends on the size of the drainage hole. 

### Example 6. Drain a Tank

A right circular cylindrical tank with radius $5$ ft and height $16$ ft that was initially full of water is being drained at the rate of $0.5\sqrt{x}$ $\text{ft}^3/\text{min}$. Find a formula for the depth and the amount of water in the tank at any time $t$. How long will it take to empty the tank? 

![Untitled](W8-S2%20Impr%20699d7/Untitled%2014.png)
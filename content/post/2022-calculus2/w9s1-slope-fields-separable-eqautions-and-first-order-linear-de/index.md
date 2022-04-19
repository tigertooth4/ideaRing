---
title: "W9-S1  Slop Fields, Separable and First-Order Linear Differential Equations"
date: 2022-04-19T15:17:23+08:00
draft: false
tags: ["differential equations", "Slope", "Separable", "First-order", "Linear", "calculus", "lectures"]
---

周次: 9
日期: April 20, 2022
节次: 1

In this lecture, we introduce some basic concept for differential equations, how to think of them, how to describe them and how to solve them. The most important thing is to know how to solve a differential equation. We will solve typical separable differential equations as well as the  first-order linear differential equations.


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

**Definition.** A **Solution** to equation (1) is a differentiable function $y=y(x)$ defined on an interval $I$ of $x$-values such that 

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

![Untitled](W9-S1%20Slop%20ed222/Untitled.png)

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

![Untitled](W9-S1%20Slop%20ed222/Untitled%201.png)

## Slope Fields: Viewing Solution Curves

Any particular solution to a differential equation can be viewed as a graph, a plane curve, at every point $(x,y)$ of the curve, the slope for the curve has been assigned with the value $f(x,y)$.

Indeed, before solving the differential equation, we could illustrate the slope for each point on the plane by line segments. Each line segment has the slope indicating by $f(x,y)$. The resulting picture with those line segments is called a **slope field ( or direction field)** and gives a visualization for the general shape of the solution curves.

![Untitled](W9-S1%20Slop%20ed222/Untitled%202.png)

### Slope Field and General Solutions

Here are some of the slope fields for particular $f(x,y)$ functions.

![Untitled](W9-S1%20Slop%20ed222/Untitled%203.png)

![Untitled](W9-S1%20Slop%20ed222/Untitled%204.png)

![Untitled](W9-S1%20Slop%20ed222/Untitled%205.png)

### For Example 1

![Untitled](W9-S1%20Slop%20ed222/Untitled%206.png)

![Untitled](W9-S1%20Slop%20ed222/Untitled%207.png)

### For Example 2

![Untitled](W9-S1%20Slop%20ed222/Untitled%208.png)

![Untitled](W9-S1%20Slop%20ed222/Untitled%209.png)

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

![Untitled](W9-S1%20Slop%20ed222/Untitled%2010.png)

# § 9.2 First-Order Linear Differential Equations

Differential equations are, in general, difficult or even impossible to solve explicitly. However, for some particular classes, for example: linear differential equations, we can show that it is solvable.

In this section, we are looking at a simplest type of linear differential equations, which can be solved explicitly.  The type we are looking at is called *First-order Linear Differential Equations.*

## Definition (First-Order Linear Differential Equations)

A differential equation 

$$
\begin{equation}\frac{dy}{dx} + P(x) \, y = Q(x),\end{equation}
$$

where $P$ and $Q$ are continuous functions of $x$ is called **First-Order Linear DE.**  Equation $(3)$ is the linear equation’s **standard form.**

### Remark 1. ****

- **What does first-order mean?**

First-order refers to the highest order derivative appeared in the equation is **first-derivative.**

- **What does linear mean?**

Linear means all the operations occurring on $y$ are linear, i.e. 

$$
\frac{d}{dx} + P(x) 
$$

is a linear operator. Which means, for any linear combination $y=\lambda y_1 + \mu y_2$, the linear operator acts like 

$$
\left(\frac{d}{dx} + P(x) \right) y = \lambda \left(\frac{d}{dx}+P(x)\right)y_1 + \mu \left(\frac{d}{dx} + P(x)\right)y_2.
$$

For example, $\sqrt{\frac{dy}{dx}} +P(x) y = Q(x)$ is first-order DE. however, it is not linear.

### Remark 2.

A linear DE is much easier to solve. Suppose $y_1$ and $y_2$ are two solutions to the linear DE  

$$
\frac{d}{dx}y + P(x)\, y=0
$$

then $\lambda y_1 + \mu y_2$ is another solution.

### Example 1. Finding the Standard Form

Put the following equation in standard form: 

$$
x \frac{dy}{dx} = x^2 + 3y,\quad x>0.
$$

# Solving Linear Equations

We solve the equation 

$$
\dfrac{dy}{dx} + P(x)\, y = Q(x)
$$

by transforming the left side into the derivative of certain product function $v(x)\cdot y$. 

### Why does multiplying by v(x) work?

Suppose by multiplying a function $v(x)$, the equation has transformed into 

$$
\begin{align}v(x) \frac{dy}{dx} + v(x) P(x) y &= v(x) Q(x)\\ \frac{d}{dx}\left(v(x)\cdot y\right) &= v(x) Q(x) \\ v(x) \cdot y &= \int v(x) Q(x) dx \\ y &= \frac{1}{v(x)}\int v(x) Q(x)dx.\end{align}
$$

Solution of equation (3) was expressed in terms of the function $v(x)$ and $Q(x).$ We call $v(x)$  an **integrating factor.**

### How such v(x) is found?

If step (4) can be transformed into step (5) successfully, then 

$$
\begin{align}v(x) \frac{dy}{dx} + v'(x) y = v(x)\frac{dy}{dx} + v(x) P(x) y\end{align}
$$

Therefore 

$$
v'(x) = v(x) P(x).
$$

It is another first-order linear DE which can be solved by assuming $v(x)$ being positive function. 

$$
\begin{align}\frac{dv}{dx} &= v P \\ \frac{dv}{v} &= P dx\\ \int \frac{dv}{v} &= \int P dx\\ v &= e^{\int P dx}  \end{align}
$$

### Summary

<aside>
🔥 To solve the linear equation $y' + P(x) y = Q(x)$, multiply both sides by the integrating factor $v(x) = \exp\int P(x)dx$ and integrate both sides.

</aside>

### Example 2. Solving  a First-Order Linear Differential Equation

Solve the equation 

$$
x \frac{dy}{dx} = x^2 + 3y,\quad x>0.
$$

Solution. ($y=-x^2 + C x^3,\quad x>0.$)

### Example 3. Solving a First-Order Linear Initial Value Problem

Solve the equation 

$$
x y' = x^2 + 3y,\quad x>0,
$$

given the initial condition $y(1) = 2.$

Solution. ($y = -x^2+3x^3$)

### Example 4. Find the particular solution of

$$
3x y' - y = \ln x + 1,\quad x>0,
$$

satisfying $y(1) = -2.$

Solution. ( $y=2x^{1/3} - \ln x -4.$ )

### Note.

If the function $Q(x)$ is identically zero in the standard form 

$$
\frac{dy}{dx} + P(x) y = 0,
$$

the linear equation is separable:  

$$
\frac{dy}{y} = - P(x) dx.
$$

Then the DE can be solved by integration.

# Applications.

## RL Circuits

![Untitled](W9-S1%20Slop%20ed222/Untitled%2011.png)

An electrical circuit whose resistance is $R$ ohms, and whose self-inductance, shown as a coil, is $L$ henries. There is a switch whose terminals at $a$ and $b$ can be closed to connect a constant electrical source of $V$  volts.

Ohm’s law for such a circuit has to be modified. The modified form is 

$$
L \frac{di}{dt} + Ri = V
$$

where $i$ is the intensity of the current in amperes and $t$ is the time in seconds. 

### Example 5. Electric Current Flow

The switch in the RL circuit is closed at time $t=0$. How will the current flow as a function of time?
---
title: "W10-S1 Euler’s Method and Graphical Solutions for Autonomous DE"
date: 2022-04-26T13:48:51+08:00
draft: false
tags: ["euler-method", "graphical-solution", "autonomous", "solve","differential", "equation", "calculus", "lecture"]
---
 

周次: 10
日期: April 27, 2022
节次: 1

In this lecture, we talk briefly on the numerical method for solving an initial value problem for a  general first order differential equation. The method is called **Euler’s Method,** it is the most simplest numerical method for solving a differential equation. Secondly, we will look at how to sketch graphical solution curves for a first-order autonomous differential equations and give some examples.

# Outline

# § 9.3 Euler’s Method

In this section, we would like to take a glance at numerical method for solving the general first-order differential equation with the initial condition being proposed. The method is the simplest one, called the **Euler’s method**. 

As a numerical solution to the differential equation, what we really need is not finding the solution as a function,  but providing a table containing pairs of $x$’s and $y$’s, i.e. find the correspondence relation on some sampling points.

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled.png)

Suppose a first-order initial value problem has the form  

$$
\begin{align}&\dfrac{d y}{dx} = f(x,y),\\ &y(x_0) = y_0.\end{align}
$$

with the initial condition (2). Geometrically, one can trace the slope field starting from the initial position $(x_0,y_0)$ to get a  curve roughly demonstrating a solution.  Euler’s method will be a mathematical realization of this idea.

## Euler’s Method

Suppose we are starting from point $(x_0,y_0)$. Given a very small increment $\Delta x$ in variable $x$, we would like to predict a $y$ from the equation (10). Denoting $x_1 = x_0+\Delta x,$ the linearization for unknown function $y$ provides a very good approximation for $y(x_1)$. Indeed, 

$$
y(x_1)\approx y(x_0) + y'(x_0) (x_1-x_0).
$$

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%201.png)

But according to the DE, $y'(x_0)$  is equal to $f(x_0,y_0)$, which can be computed directly. Therefore, we would like to think that, roughly speaking, $y(x_1)$  can be replaced with the linear approximation of it.

$$
y(x_1) \approx y(x_0) + f(x_0,y_0) (x_1-x_0):=L(x_1).
$$

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%202.png)

This completed the first Euler step.

For the second Euler step, we start from $(x_1,y_1),$ use linear approximation of $y$ at $x_1$ to predict a $y_2$ 

$$
y_2 \approx y_1 + f(x_1,y_1)(x_2-x_1)
$$

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%203.png)

By repeating this process again and again, we get an approximated solution to the DE. 

### Example 1. Using Euler’s Method

Find the first three approximations $y_1$, $y_2$, $y_3$ using Euler’s method for the initial value problem 

$$
y' = 1+y,\quad y(0)=1,
$$

starting at $x_0 = 0$ with $\Delta x = 0.1.$

**Solution.**

1. Send $x_0 = 0,$ $y_0=1$,  then $y_1 = y_0 + (1+y_0) \Delta x = 1.2$
2. Send $x_1 = 0.1$, $y_1=1.2$, then $y_2 = y_1 + (1+y_1)\Delta x = 1.42$
3. Send $x_2 = 0.2$, $y_2 = 1.42$, then $y_3 = y_2 + (1+y_2)\Delta x = 1.662$.

 

### Demonstrations On Euler’s Method

- For $\frac{dy}{dx} = (1-x)y+\frac{x}{2}$, with initial value indicated by cross point. Blue curve shows the real solution, red curve shows the line segment obtained by Euler’s method.

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%204.png)

- Second Example $\frac{dy}{dx} = y-x^2$

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%205.png)

- Third Example $y' = - \frac{2xy}{1+x^2}$.

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%206.png)

# § 9.4 Graphical Solutions of Autonomous Differential Equations

## Autonomous Differential Equation

For example, consider an implicit equation 

$$
\frac15 \ln(5y-15) = x+1.
$$

By differentiating this equation, we obtain 

$$
\frac15 \left(\frac{1}{y-3}\right)\frac{dy}{dx} = 1.
$$

Therefore the derivative $\frac{dy}{dx}$ is a function  of $y$ only. (Not explicitly depends on $x$).

### Definition.

A differential equation for which $dy/dx$ is a function of $y$ only is called an **autonomous** differential equation. 

### Examples

- $\frac{dy}{dx} = 3 (y-1) \sin (y)$ is an autonomous differential equation
- $\frac{dy}{dx} = 3(y-x) sin(y)$ is not an autonomous DE.

## Equilibrium Values

Think of a differential equation is defining how the derivative $\frac{dy}{dx}$ behaves. 

$$
\frac{dy}{dx} = 5(y-3)(1-y)
$$

Then for an autonomous differential equation,  at **what value** $y$ the the $\frac{dy}{dx}$ vanishes  is called an **Equilibrium value** or a 

**rest point.**

Thus, equilibrium values are those at which no change occurs in the dependent variable, so $y$ is at **rest**.

### Example 1. Finding Equilibrium Values

The equilibrium values for autonomous differential equation 

$$
\frac{dy}{dx} = (y+1)(y-2).
$$

### Example. Finding Equilibrium Values

The equilibrium values for autonomous differential equation 

$$
\frac{dy}{dx} = k y.
$$

## Sketch the Graphical Solutions to an Autonomous DE

To sketch graphical solutions to the autonomous differential equation, we need to analyze the signs of $y'$ and $y''$, these informations can be read from the differential equation. 

### Example 2. Sketching Solution Curves

Sketch solutions to the equation 

$$
\frac{dy}{dx} = (y+1)(y-2).
$$

### Step 1. Mark the equilibrium values on the $xy$-plane.

The equilibrium values are $y=-1$ and $y=2$, where $dy/dx = 0.$ 

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%207.png)

### Step 2. Identify and label the intervals (regions) where $y'>0$ and $y'<0.$

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%208.png)

### Step 3. Calculate $y''$ and mark the intervals where $y''>0$ and $y''<0$.

Since

$$
y' = (y+1)(y-2) = y^2 - y -2.
$$

Differentiate both sides with respect to $x$, using implicit differentiation 

$$
y'' = 2yy'-y' = (2y-1)y' = (2y-1)(y+1)(y-2).
$$

Thus we add the sign information to the **phase line**.

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%209.png)

### Step 4. Sketch an assortment of solution curves in the $xy$-plane

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%2010.png)

### Example 3. Cooling Soup

What happens to the temperature of the soup when a cup of hot soup is placed on a table in a room? What does a typical temperature curve look like as a function of time?

By Newton’s law of cooling, there is a constant $k$ such that 

$$
\frac{dH}{dt} = -k(H-15),
$$

where $15$ is the ambient temperature in Celsius. 

Since $H'' = -k H' = k^2(H-15)$, we can sketch the phase line and general solutions on the $xy$-plane below.

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%2011.png)

### Example 4. Analyzing the Fall of a Body Encountering a Resistive Force (Omitted)

### Example 5. Analyzing Population Growth in a Limiting Environment

If $P$ represents the number of individuals and we neglect departures and arrivals, then 

$$
\frac{dP}{dt} = kP,
$$

where $k>0$ is the birthrate minus the death rate per individual per unit time. 

As the population approaches the **limiting population** or **carrying capacity,** resources become less abundant and the growth rate $k$ decreases. Suppose the limiting population is denoting by $M$. Then a simple relationship exhibiting this behavior is 

$$
k=r(M-P),
$$

where $r>0$ is a constant.  Notice that $k$ is negative if $P$ is greater than $M$. Then the model is 

$$
\begin{equation}\frac{dP}{dt} = r(M-P) P = rMP-rP^2\end{equation}
$$

Equation (3) is referred to as **logistic growth.**

Since 

$$
\frac{d^2 P}{dt^2} = rM P' - 2r P P' = r(M-2P)P' = r^2(M-2P)(M-P)P,
$$

we can analyze the phase line and sketch a graph on it. 

![Untitled](W10-S1%20Euler%E2%80%99s%20Method%20and%20Graphical%20Solutions%20for%20%203b6cdf3aefd244cc98c1da12597f5164/Untitled%2012.png)
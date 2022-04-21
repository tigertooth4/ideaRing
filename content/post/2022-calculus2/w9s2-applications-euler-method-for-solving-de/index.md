---
title: "W9-S2 Applications, Euler’s Method for Numerical DE  Solving"
date:  2022-04-21T23:24:40+08:00
draft: false
tags: ["application", "fat", "weight", "circuit", "calculus", "differential", "Euler", "lecture"]
---

周次: 9
日期: April 22, 2022
节次: 2

In this lecture, we would like to give several examples on solving differential equations. Three examples will be shown. And Euler’s method for numerical solution for the initial value problem of differential equations will also be explored. 


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

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled.png)

An electrical circuit whose resistance is $R$ ohms, and whose self-inductance, shown as a coil, is $L$ henries. There is a switch whose terminals at $a$ and $b$ can be closed to connect a constant electrical source of $V$  volts.

Ohm’s law for such a circuit has to be modified. The modified form is 

$$
L \frac{di}{dt} + Ri = V
$$

where $i$ is the intensity of the current in amperes and $t$ is the time in seconds. 

### Example 5. Electric Current Flow

The switch in the RL circuit is closed at time $t=0$. How will the current flow as a function of time?

## Mixture Problems

A chemical in a liquid solution runs into a container holding the liquid with, possibly, a specified amount of the chemical dissolved as well. The mixture is kept uniform by stirring all the time. And mixture flows out of the container at a known rate. 

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%201.png)

The amount of chemical changing within the container is based on the following equation 

$$
\begin{pmatrix}\text{Rate of change}\\ \text{of amount} \\ \text{in container}\end{pmatrix} = \begin{pmatrix}\text{rate at which}\\ \text{chemical} \\ \text{arrives}\end{pmatrix} - \begin{pmatrix}\text{rate at which}\\ \text{chemical} \\ \text{departs}\end{pmatrix}.
$$

- $y(t)$ :  The amount of chemical in the container at time $t$
- $V(t)$ :  The total volume of liquid in the container at time $t$

Then the departure rate of the chemical at time $t$ 

$$
\text{Depature Rate} = \dfrac{y(t)}{V(t)}\cdot (\text{outflow rate})
$$

So 

$$
\dfrac{dy}{dt} = \left(\text{chemical's arrival rate}\right) - \dfrac{y(t)}{V(t)}\cdot (\text{outflow rate})
$$

### Example 6. Oil Refinery Storage Tank

In an oil refinery, a storage tank contains $2000$ gallons of gasoline that initially has $100 \text{ lb}$  of an additive dissolved in it. Gasoline containing $2\text{ lb}$ of additive per gallon is pumped into the tank at a rate of $40\;\text{gal/min}$. The well-mixed solution is pumped out at a rate of $45\;\text{gal/min}$. How much of the additive is in the tank $20\; \text{min}$ after the pumping process begins.

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%201.png)

## Weight Growth

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%202.png)

### Can Our Body Weights Keep Growing Unboundedly, If We Keep Eating Same Amount Everyday and Do Nothing Else ? ${}^{[1]}$

We eat everyday. Suppose we eat the same amount everyday, and lie flat for the rest of the time. Can our body weights grow unboundedly eventually? Math will tell you the answer.

Assume the energy intake for our body comes entirely from the food. The energy intake is counted in kilo-Calories ($\text{k.Cal}$). A surprising fact is, our body consumes energy even when we lying flat. The energy is consumed by our organs to keep their normal functions. This energy consumption is called **Basal Metabolism (BM, in $\text{k.Cal}$).**   

*Indeed, the basal metabolism is forming the majority of  our energy consumption.* 

Biologically, BM is affected by multiple factors.  For example, gender, age, body weight, body height, etc. A simple empirical formula for BM per day is   

$$
(\text{BM for Female}) = 661 + 9.6\times (\text{weight (kg)}) + 1.72\times (\text{height (cm)}) - 4.7\times (\text{age})
$$

$$
(\text{BM for Male}) = 67 + 13.73\times (\text{weight (kg)}) + 5 \times (\text{height (cm)}) - 6.9 \times (\text{age})
$$

A typical man at his 40’s with height = $175\text{ cm}$ and weight = $75\text{ kg}$ has  $\text{BM} = 1695.75 \text{ k.Cal/day}$.

If the energy intake is not fully consumed, the rest of it will be used for synthesizing fat, which leads to the growing in weight. Approximately, each kilogram of body weight growth needs $9000\text{ k.Cal}$ of energy. 

According to these facts, the formula for energy is 

$$
(\text{energy intake}) = \begin{pmatrix}\text{energy  consumed}\\ \text{by BM}\end{pmatrix} +\begin{pmatrix}\text{energy consumed}\\ \text{by other activities} \end{pmatrix} + \begin{pmatrix}\text{energy for}\\ \text{synthesizing or}\\ \text{ decomposing fat}\end{pmatrix}\text{}
$$

### Can Weight Grows Unbound If We Lie Flat ?

Suppose in a short period, age and height remain unchanged. Denote the body weight  by $m(t)$. Then BM is directly related to body weight and becoming a function of $m(t)$. We have the following assumptions

- The energy intake is constant $I \text{ k.Cal/day}$.
- The BM is denoted by $Q(m(t))\approx 13.73 \, m(t) + C$, where $C\approx 666$.

Then 

$$
 I \cdot (t-t_0) = \int_{t_0}^t Q(m(s))ds + 9000 \cdot(m(t)-m(t_0)).  
$$

By taking derivative with respect to $t$, a differential equation displayed is  

$$
I = 13.73\, m + 666 + 9000\frac{d m}{dt}.
$$

Suppose initially the body weight at $t=t_0=0$ is $75\,{\text{kg}}$. Then the general solution for the first-order initial value problem is 

$$
m(t) = \frac{I-666}{13.73/9000} + D \cdot e^{-\frac{13.73}{9000}t}
$$

Take the initial condition in consideration, 

$$
D = m(0) - \frac{I-666}{13.73/9000}.
$$

### Conclusions

- If energy intake is an amount such that  $D$ remains positive, then the body weight is dropping down, and eventually will be stabilized around $I-666 \over 13.73/9000$.
- if energy intake is so large so that $D$ becomes negative, then the body weight is growing up, but eventually stabilized around $I-666 \over 13.73/9000$ as well.

Either case, the body weight **cannot** grow unboundedly. 

# § 9.3 Euler’s Method

In this section, we would like to take a glance at numerical method for solving the general first-order differential equation with the initial condition being proposed. The method is the simplest one, called the **Euler’s method**. 

As a numerical solution to the differential equation, what we really need is not finding the solution as a function,  but providing a table containing pairs of $x$’s and $y$’s, i.e. find the correspondence relation on some sampling points.

Suppose a first-order initial value problem has the form  

$$
\begin{align}&\dfrac{d y}{dx} = f(x,y),\\ &y(x_0) = y_0.\end{align}
$$

with the initial condition (11). Geometrically, one can trace the slope field starting from the initial position $(x_0,y_0)$ to get a  curve roughly demonstrating a solution.  Euler’s method will be a mathematical realization of this idea.

## Euler’s Method

Suppose we are starting from point $(x_0,y_0)$. Given a very small increment $\Delta x$ in variable $x$, we would like to predict a $y$ from the equation (10). Denoting $x_1 = x_0+\Delta x,$ the linearization for unknown function $y$ provides a very good approximation for $y(x_1)$. Indeed, 

$$
y(x_1)\approx y(x_0) + y'(x_0) (x_1-x_0).
$$

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%203.png)

But according to the DE, $y'(x_0)$  is equal to $f(x_0,y_0)$, which can be computed directly. Therefore, we would like to think that, roughly speaking, $y(x_1)$  can be replaced with the linear approximation of it.

$$
y(x_1) \approx y(x_0) + f(x_0,y_0) (x_1-x_0):=L(x_1).
$$

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%204.png)

This completed the first Euler step.

For the second Euler step, we start from $(x_1,y_1),$ use linear approximation of $y$ at $x_1$ to predict a $y_2$ 

$$
y_2 \approx y_1 + f(x_1,y_1)(x_2-x_1)
$$

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%205.png)

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

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%206.png)

- Second Example $\frac{dy}{dx} = y-x^2$

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%207.png)

- Third Example $y' = - \frac{2xy}{1+x^2}$.

![Untitled](W9-S2%20Applications,%20Euler%E2%80%99s%20Method%20for%20Numerical%20D%208802583e526549c6814072894fee3a9d/Untitled%208.png)

# References

[1]. [​为什么减肥之后，体重会反弹？——数学给出答案](https://www.notion.so/3a193ca4614b4c16974ea55d1e7fc48d) 

[​为什么减肥之后，体重会反弹？--数学给出答案](https://mp.weixin.qq.com/s?__biz=MzIyNzUxMjE1Mw==&mid=2247517575&idx=1&sn=73cbfa3fcd6a4db2546dfc79a5f973e5&chksm=e862dfb1df1556a7572bc142d7501bf5d9c73064996c410c57db06cac8a2b43256b8d69e2a5b#rd)
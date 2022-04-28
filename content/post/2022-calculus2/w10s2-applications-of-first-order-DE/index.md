---
title: "W10-S2 Applications of First-Order Differential Equations"
date: 2022-04-28T16:22:21+08:00
draft: false
tags: ["application","differential","equations", "solve","coasting","population","orthogonal","lecture","calculus"]
--- 

周次: 10
日期: April 29, 2022
节次: 2

In today’s lecture, we are going to look at three typical applications of first-order differential equations. 

1. Analyzes an object moving along a straight line while subject to a force opposing its motion.
2. A model of population growth which takes into account factors in the environment placing limits on growth.
3. A curve or curves intersecting each curve in a second family of curves *orthogonally (at right angles).*

The rest of the lecture will be devoted to the review of quiz2 exercises and a guideline for important contents from chapter 6 to the end of chapter 9.

# Outline

# Example. Resistance Proportional to Velocity

Resistance encountered by a moving object, such as a car **coasting (空驶)** to a stop. The faster the object moves, the more its forward progress resisted by the air through which it passes. 

Consider an object with a mass $m$ moving along a coordinate line with position function $s(t)$ and velocity $v(t)$ at time $t$. Assume the resistance force is proportional to velocity by a factor $k$. According to *Newton’s second law of motion,* 

$$
\text{(Force)} = \text{(mass)}\times \text{(acceleration)} = m \frac{dv}{dt}.
$$

Then we can express the velocity by writing down a differential equation 

$$
m \frac{dv}{dt} = -k v.
$$

This is a first-order linear differential equation and a separable equation as well. Therefore its solution is given by 

$$
v = v_0 \exp\left(-\frac{k}{m}t\right).
$$

Since 

$$
\frac{ds}{dt} = v(t).
$$

We can integrate this equation to find the general solution for $s(t)$

$$
s(t) = \int v_0 e^{-k\,t/m} dt = -\frac{m v_0}{k} e^{-k\, t/m} + C.
$$

By assuming an initial condition $s(0) = 0$, the constant $C$ is determined 

$$
C = \frac{m v_0}{k}.
$$

Thus the particular solution $s(t)$ is 

$$
s(t) = \frac{m v_0}{k}\left(1 - e^{-k t/m}\right).
$$

To find how far the body will coast, we find the limit of $s(t)$ as $t\to \infty$, which is 

$$
\text{Distance coasted} = \frac{m v_0}{k}.
$$

This will be an upper bound. But in real cases, after a short while we will see the object can coast a distance that is very close to the upper bound, thanks to the rapidly decreases of $e^{-k t/m}$.

### Example 1. A Coasting Ice Skater

For a $192$-$\text{lb}$ ice skater, the $k$ is about $1/3$ $\text{slug}/\text{sec}$ and $m=192/32 = 6 \text{ slugs}.$ 

1. How long will it take the skater to coast from $11\text{ ft/sec}$ to $1\text{ ft/sec}$ ?  
2. How far did the skater coast when the speed is $1\text{ ft/sec}$ ?
3. How far will the skater coast before coming to a complete stop? 

# Example. Modeling Population Growth

We have modeled population growth with the law of exponential change in section 7.5 

$$
\frac{dP}{dt} = k P,\quad P(0) = P_0,
$$

where $P$ is the population at time $t$, $k>0$ is a constant growth rate, and $P_0$ is the size of the population at time $t=0$. 

This equation is referring to the case when the **relative growth rate $\frac{dP}{dt}/ P = k$ is a constant.** However, it is not usually the case, especially for recent decades. In practice, the coefficient $k$ is usually a dependent variable of time $t$ or population size $P$. 

## The Population Size for China in Recent Decades

For example, according to the queries from `WolframAlpha`, the population size for China in recent 40 years is give by the following chart 

![(Population size in the unit of billions)](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled.png)

(Population size in the unit of billions)

If we take the increment $dt = 1 \text{ year}$ , $dP/dt \approx \Delta P$  be the population difference in consecutive years, then the relative growth rate $k$ changes across year is given by the following chart  

![Relative growth rate change across years](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%201.png)

Relative growth rate change across years

## The Logistic Model

To build a better model that can predict the population growth, we assume the relative growth rate as a linear function of population $P$, that is 

$$
k = {dP/dt \over P}  := r(M-P) = r M - rP.
$$

In this expression, $r$ is the slope, $r M$  is the interception. Then we obtained the **Logistic Growth Model**  

$$
\frac{dP}{dt} = r(M-P) P,
$$

where $M$ is called the **limiting  (maximum) population**, or **carrying capacity**. 

### Data Fitting for China’s Carrying Capacity

To find the carrying capacity for China, we first represent the relative growth rate as relating with population size, as shown in the following chart.

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%202.png)

As shown in the chart, it is not quite linear! But if we consider data for the recent twenty years (from 1.2 billion to 1.45 billion), that portion of the chart is relatively linear. So by using linear fitting tools in Mathematica, we have found a linear relation according to the data, shown as the chart follows. 

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%203.png)

The straight line corresponds to a linear function 

$$
0.035282 - 0.0217709 P = 0.0217709\cdot (1.62061-P) = r(M-P).
$$

Which means the carrying capacity will be roughly $1.62061 \text{ billion people}$. 

## Solve the Logistic Model

The Logistic Model fitting the population growth for China is given by 

$$
\frac{dP}{dt} = r(M-P)P, \quad P(0) = 1.2,
$$

where $r=0.0217709$, $M=1.62061$. 

### Slope field

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%204.png)

### Graphical Solution

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%205.png)

### Numerical Solution

Euler’s method for predicting the Population. 

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%206.png)

### Analytic Solution

$$
P = \dfrac{M}{1+A e^{-r M t}}
$$

# Example. Orthogonal Trajectories

An **orthogonal trajectory** of a family of curves is a curve that intersects each curve of the family at right angles, or *orthogonally.* 

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%207.png)

## Example 3. Finding Orthogonal Trajectories

Find the orthogonal trajectories of the family of curves $xy = a$, where $a\neq 0$ is an arbitrary constant.

![Untitled](W10-S2%20Applications%20of%20First-Order%20Differential%20Eq%2083c371114ce147a49cc5b526b1ad5112/Untitled%208.png)


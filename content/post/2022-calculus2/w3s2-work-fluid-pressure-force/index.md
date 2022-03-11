---
title: "W3-S2 Work, Fluid Pressure and Forces"
date: 2022-03-11T13:24:26+08:00
draft: false
tags: ["lecture", "calculus", "work", "pressure", "forces"]
---

周次: 3
日期: March 11, 2022
节次: 2

In this lecture, we’ll give a brief introduction to the concepts of works and fluid pressures. Many examples will be presented. This lecture covers §6.6 and §6.7.

# Outline

# Work

Work refers specifically to a force acting on a body and the body’s subsequent displacement. 

## Basic Principle: Work Done by a Constant Force

If the force $F$ is a constant in magnitude along the direction of motion, then

$$
W = F\cdot d.
$$

The unit of work is a newton-meter ($N\cdot m$), or **joule ($J$).**

## Work Done by a Variable Force Along a Line

Suppose that the force acts along a line in $x$-axis, and the magnitude $F$ is a continuous function depending on the position. We want to find the work done over the interval from $x=a$ to $x=b$.

1. Partition $[a,b]$ in the usual way and choose an arbitrary point $c_k$ in each subinterval $[x_{k-1},x_k]$.
2. Think $F$ as a constant force $F(c_k)$ during $[x_{k-1},x_k]$, then the work is $F(c_k)\Delta x_k$
3. The total work is approximately 

$$
\text{Work} \approx \sum_{k=1}^n F(c_k) \Delta x_k.
$$

1. As $||P||\to 0$, the Riemann sum converges definite integral 

$$
W = \int_a^ b F(x) dx.
$$

> **Definition (Work)**
> 

The **work** done by a variable force $F(x)$ directed along the $x$-axis from $x=a$ to $x=b$ is 

$$
W = \int_a^b F(x)dx.
$$

The units of the integral are joules if $F$ is in **newtons** and $x$ is in **meters,** and **foot-pounds** if $F$ is in **pounds** and $x$ in **feet.**

## Hooke’s Law for Springs: $F=kx$

**Hooke’s Law** says that the force it takes to stretch or compress a spring $x$ length units from its natural (unstressed) length is proportional to $x$. 

$$
F=kx.
$$

The constant $k$ is called the **force constant (or spring constant).**

### Example 2. Compressing a Spring

Find the work required to compress a spring from its natural length of $1$ ft to a length of $0.75$ ft if the force constant is  $k=16$ lb/ft.

![Untitled](W3-S2%20Work%20cc685/Untitled.png)

**`Solution.` (0.5 ft-lb)**

### Example 3. Stretching a Spring

A spring has a natural length of $1$ m. A force of $24$ N stretches the spring to a length of $1.8$ m.

1. Find the force constant $k$.
2. How much work will it take to stretch the spring $2$ m beyond its natural length?
3. How far will a $45$-N force stretch the spring?

![Untitled](W3-S2%20Work%20cc685/Untitled%201.png)

**`Solution`**

### Example 4. Lifting a Rope and Bucket

A $5$-lb bucket is lifted from the ground into the air by pulling in $20$ ft of rope at a constant speed. The rope weighs $0.08$ lb/ft.  How much work was spent lifting the bucket and rope?

![Untitled](W3-S2%20Work%20cc685/Untitled%202.png)

**`Solution` (116 ft-lb)**

## Pumping Liquids from Containers

How much work does it take to pump all or part of the liquid from a container? We imagine lifting the liquid out one thin horizontal slab at a time and applying the equation $W=Fd$ to each slab. 

### Example 5. Pumping Oil from a Conical Tank

The conical tank is filled to within $2$ ft of the top with olive oil weighing $57\text{ lb/ft}^3$. How much work does it take to pump the oil to the rim of the tank?

![Untitled](W3-S2%20Work%20cc685/Untitled%203.png)

**`Solution`**

### Example 6. Pumping water from a Glory Hole

A glory hole is a vertical drain pipe that keeps the water behind a dam from getting too high. The top of the glory hole for a dam is $14$ ft below the top of the dam and $375$ ft above the bottom. The hole needs to be pumped out from time to time to permit the removal of seasonal debris.

The glory hole is a funnel-shaped drain. The throat of the funnel is $20$ ft wide and the head is $120$ ft across. The outside boundary of the head cross-section are quarter circles formed with $50$-ft radii. 

We calculate the work required to pump water from 

1. the throat of the hole
2. the funnel portion.

![Untitled](W3-S2%20Work%20cc685/Untitled%204.png)

![Untitled](W3-S2%20Work%20cc685/Untitled%205.png)

**`Solution`**

# Fluid Pressures and Forces

Fluid pressure depends only on how far below the surface the point is and not on how much the surface of the dam happens to be tilted at that point.

## **Basic Fact 1 (The pressure-Depth Equation)**

In a fluid that is standing still, the pressure $p$ at depth $h$ is the fluid’s weight-density $w$ times $h$: 

$$
p = w\cdot h = \rho \cdot g\cdot h
$$

We use the formula to derive a formula for the total force exerted by a fluid against all or part of a vertical or horizontal containing wall.

## **Basic Fact 2 (The Pressure and the Force)**

For plate being exerting a constant pressure everywhere, the force exerted on the plate is equal to the pressure times area for the plate. 

$$
F = p\cdot A
$$

## Basic Fact 3 (The Fluid Pressure)

Under the surface of the fluid, at the same depth, the pressure is identical on each direction.

We use these facts, to calculate fluid force on a horizontal or vertical wall submerged into the fluid. For a flat plate submerged horizontally, like the bottom of the swimming pool, the downward force acting on its upper face is given by $F = p A = \rho ghA.$ Let’s discuss the case of a vertical wall. The pressure will be different at each depth. 

## The Variable-Depth Formula

Suppose we want to know the force exerted by a fluid against *one side* of a vertical plate submerged in a fluid of weight-density $w$.

![Untitled](W3-S2%20Work%20cc685/Untitled%206.png)

We model the plate as a region extending from $y=a$ to $y=b$ in the $xy$-plane. We partition $[a,b]$ in the usual way and imagine the region to be cut into thin horizontal strips. The typical strip  at depth $y$ is assumed to be $L(y)$ units long and $\Delta y$ units wide.

Then the force exerted on the strip is 

$$
\Delta F_k = w \cdot y_k\cdot L(y_k)\cdot \Delta y_k
$$

So the total force is approximately 

$$
F\approx \sum_{k=1}^n w y_k L(y_k)\Delta y_k
$$

Passing to the limit, the force will become an integral 

$$
F = \int_a^b w y L(y) dy.
$$

### Example 1. Applying the Integral for Fluid Force

A flat isosceles right triangular plate with base $6$ ft and height $3$ ft is submerged vertically, base up, $2$ ft below the surface of a swimming pool. Find the force exerted by the water against one side of the plate.

![Untitled](W3-S2%20Work%20cc685/Untitled%207.png)

**`Solution`**

## Fluid Forces and Controids

![Untitled](W3-S2%20Work%20cc685/Untitled%208.png)

If we know the depth of the centroid for the flat plate submerged vertically, we can take a shortcut to find the force against one side of the plate. 

Suppose a plate is submerged into the fluid, extending from $y=a$ to $y=b$. Establish the coordinate system with $y$-axis pointing downward, we see 

$$
F = \int_a^b w\, y\, L(y)\, dy\\ = w \int_a^b y\, L(y)\, dy \\ = w \cdot \bar{h}\cdot \int_a^b L(y) \,dy\\ = w \cdot \bar{h} \cdot A  
$$

> **Fluid Forces and Centroids**
> 

The force of a fluid of wight-density $w$ against one side of a submerged flat vertical plate is the product of $w$, the distance $\bar{h}$ from the plate’s centroid to th fluid surface, and the plate’s area: 

$$
F = w \, \bar{h}\, A.
$$

### Example 2. Finding Fluid Force Using Centroid

Use centroid to find the force in the previous example.
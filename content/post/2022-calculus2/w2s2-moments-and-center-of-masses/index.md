---
title: "W2-S2 Moments and Center of Masses"
date: 2022-03-04T13:33:29+08:00
draft: false
tags: ["moment","center of mass", "math", "lecture", "calculus"]
---

周次: 2
日期: March 4, 2022
节次: 2

# Outline

In this lecture, we discuss *moments* ( 质量矩）and *centers of mass.* Two concepts are related.  In this lecture, we only deal with one- and two-dimensional problems (Essentially all the problems been dealt with are in one-dimension). 



# Basic Principle for Center of Mass and Moment

> **Definition. (Center of Mass)**
> 

For a system of  point masses (质点系统), the **center of mass** is a weighted average of coordinates of  all the points, where each weight is the ratio of individual mass over the total mass. 

$$
\overline{x} = \sum_{i=1}^n \frac{m_i}{M}x_i, \quad \text{where}\quad M=\sum_{i=1}^n m_i. 
$$

![Red arrow indicates the coordinate for center of mass. Different dots’ sizes indicate different masses.](W2-S2%20Mome%209cfeb/w2s2-com1.gif)

Red arrow indicates the coordinate for center of mass. Different dots’ sizes indicate different masses.

`**Remark**`

This principle is easily applicable to higher dimensions. For two-dimensional center of mass, simply change $x_i$ and $\overline{x}$ to two-dimensional vectors $\mathbf{x}_i$ and $\overline{\mathbf{x}}$, then the formula reads

$$
\overline{\mathbf{x}} = \sum_{i}\frac{m_i}{M} \mathbf{x}_i.
$$

![Red cross indicates the position for center of mass. Different dots with different sizes indicate the different masses.](W2-S2%20Mome%209cfeb/w2s2com2.gif)

Red cross indicates the position for center of mass. Different dots with different sizes indicate the different masses.

> **Definition. (Moment (质量矩) of the system)**
> 
- For a point mass object, the moment of the object (about the origin) is its mass times coordinate.
- For a system of point masses, the moment of the system (about the origin) is the sum of the moments $m_i x_i$ of the individual masses.

$$
M_0 = \text{Moment of system about origin} = \sum_{i} m_i x_k.
$$

`**Remark**`

The relation between center of mass and moment is obvious: $\overline{x} = M_0 / M$.

## Alternative Approach to Understand the Principle

> **Definition (Torque (扭矩) About a Point)**
> 

![Untitled](W2-S2%20Mome%209cfeb/Untitled.png)

![Untitled](W2-S2%20Mome%209cfeb/Untitled%201.png)

Suppose a point mass $m$ is located at coordinate $x$ on the $x$-axis. The torque of $m$ about a point $x_0$ on the $x$-axis is defined by 

$$
\text{Torque of }m\text{ about }x_0 = (x-x_0)m g
$$

where $g$ is the *acceleration of  gravity*.

> **Definition (System Torque)**
> 

The **system torque (about point $x_0$)** is the sum of all the torques (about the same point $x_0$). 

$$
\text{System torque} = \sum_i (x_i-x_0)m_i g.
$$

The sum of the torques (about the point $x_0$) measures the tendency of a system to rotate about the given point $x_0$. The system will balance about the fulcrum if and only if its total torque is zero.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%202.png)

Imagine masses $m_1$, $m_2$
, $\cdots,m_n$
 on a rigid $x$
-axis supported by a fulcrum at the point $x_0$
. We usually want to know where $x_0$
 is, to make the system balance.

![w2s2fulcrum.gif](W2-S2%20Mome%209cfeb/w2s2fulcrum.gif)

The total torque about $x_0$
  is given by 

$$
\text{Total Torque}=\sum_{i} m_i g (x_i - x_0) = g\sum_{i}m_i x_i - g x_0\sum_i m_i
$$

If the system is balanced at $x_0$, the total torque will be zero, which gives $x_0$ 

$$
x_0 = \frac{\sum_{i}m_i x_i}{\sum_i m_i}.
$$

Thus, the fulcrum is supported at the center of masses.

# One-dimensional Applications

## Wires and Thin Rods

In many applications, we want to know the center of mass of a rod or a thin strip of metal. In this case the distribution of mass is a continuous function. The summation signs become integrals in the following manner.

- Imaging a long, thin strip lying along the $x$-axis from $x=a$ to $x=b$. We partition the strip into small pieces, with length $\Delta x_i$ for each piece.

$$
P: a=x_0<x_1<\cdots<x_n=b.
$$

The mass for the $k$th small piece is denoted by $\Delta m_k$. Choose $c_k \in[x_{k-1},x_k]$ to be any point in the $k$th subinterval. 

![Untitled](W2-S2%20Mome%209cfeb/Untitled%203.png)

- Think of each piece as a **point mass,**  then the system moment (about origin) is roughly

$$
\text{System moment} \approx \sum_k c_k \Delta m_k
$$

 And the center of mass is located at 

$$
\text{Center of mass} = \overline{x} \approx \dfrac{\sum_k c_k \Delta m_k}{\sum_k \Delta m_k}.
$$

- Furthermore, suppose the thin strip has density $\delta$  as a function of $x$ (Assume $\delta(x)$ is a continuous function of $x$), the mass $\Delta m_k$ for the $k$th piece is approximately

$$
\Delta m_k \approx \delta(c_k)\Delta x_k
$$

- Combining these observations gives

$$
\overline{x} \approx \dfrac{\sum_k c_k \delta(c_k)\Delta x_k}{\sum_k \delta(c_k)\Delta x_k}.
$$

- The sums in the last numerator and denominator are Riemann sums. We expect the approximation to improve as $||P||\to 0$. This leads to the equation

$$
\overline{x} = \dfrac{\int_a^b x\delta(x) dx}{\int_a^b \delta(x) dx}
$$

## Summary: Moment, Mass, and Center of Mass of a Strip Along the $x$-Axis with Density Function

$$
\text{Moment about the origin:}\quad M_0 = \int_a^b x\delta(x) dx.
$$

$$
\text{Mass:}\quad M = \int_a^b \delta(x) dx.
$$

$$
\text{Center of mass:}\quad \overline{x} = \dfrac{M_0}{M}.
$$

## Example 1. Strips and Rods of Constant Density

For a straight, thin strip of uniform density, the center of mass lies halfway between its two ends.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%204.png)

`**Solution**`

## Example 2. Variable-Density Rod

The $10$-m-long rod thickens from left to right so that its density $\delta(x) = 1+x/10$ kg-per-m. Find the rod’s center of mass.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%205.png)

`**Solution**`

# Two Dimensional Center of Mass

Suppose we have a finite collection of masses located in the plane, with mass $m_k$ at the point $\mathbf{x}_k = (x_k,y_k)$
. The mass of the system is 

![Untitled](W2-S2%20Mome%209cfeb/Untitled%206.png)

$$
\text{System of mass:}\\ \quad M = \sum m_k
$$

Decomposing the two-dimensional problem into two one-dimensional problems, we find that the moments of the entire system about the two axes are 

![Untitled](W2-S2%20Mome%209cfeb/Untitled%207.png)

$$
\text{Moment about }x\text{ axis:}\quad M_x = \sum m_k y_k  
$$

$$
\text{Moment about }y\text{ axis:}\quad M_y = \sum m_k x_k  
$$

So the $x$
- and $y$-coordinate of the system’s center of mass is defined to be 

$$
\overline{x} = \dfrac{M_y}{M} = \dfrac{\sum m_k x_k}{\sum m_k},\quad \overline{y}=\dfrac{M_x}{M} = \dfrac{\sum m_k y_k}{\sum m_k}.
$$

## Real World Applications

![Fosbury Flop Technique ](W2-S2%20Mome%209cfeb/Untitled%208.png)

Fosbury Flop Technique 

![Untitled](W2-S2%20Mome%209cfeb/Untitled%209.png)

## Thin, Flat Plates

In many applications, we need to find the center of mass of a thin, flat plate. In such cases, the formulas we use to calculate $\overline{x}$
  and $\overline{y}$ contain integrals instead of finite sums.

Imagine the plate occupying a region in the $xy$
-plane, cut into thin strips parallel to one of the axes. The center of mass of a typical strip is $(\tilde{x},\tilde{y})$
. The strip’s mass $\Delta m$ is thought of concentrated at $(\tilde{x},\tilde{y})$. 

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2010.png)

Then the moment of  about $x$- and $y$-axis are $\tilde{y} \Delta m$
 and $\tilde{x}\Delta m$, respectively. Then the center of mass are 

$$
\overline{x} \approx \dfrac{\sum \tilde{x} \Delta m}{\sum \Delta m}, \quad \overline{y} \approx \dfrac{\sum \tilde{y} \Delta m}{\sum \Delta m}.
$$

By taking the limits, the center of masses are symbolically written as 

$$
\overline{x} = \dfrac{\int x dm}{\int dm},\quad \overline{y} = \dfrac{\int y dm}{\int dm}.
$$

Here $dm$ is an abbreviation of density multiplies by the tiny area, which can be written clearly for each specified examples.

## Summary: Moments, Mass, and Center of Mass of a Thin Plate Covering a Region in the $xy$-Plane

$$
\text{Moment about the }x\text{-axis}:\quad M_x = \int y dm\\ \text{Moment about the }y\text{-axis}:\quad M_y = \int x dm
$$

$$
\text{Mass:}\quad M = \int dm.
$$

$$
\text{Center of mass:}\quad \overline{x} = \frac{M_y}{M},\quad \overline{y} = \frac{M_x}{M}.
$$

## Example 3. Constant-Density Plate

The triangular plate shown has a constant density $\delta=3$. Find 

1. The plate’s mass;
2. The plate’s center of mass in $x$
-direction.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2011.png)

`**Solution**`

## Example 4. Constant-Density Plate

Find the center of mass of a thin plate of constant density $\delta$ covering the region bounded above by the parabola $y=4-x^2$ and below by the $x$-axis.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2012.png)

`**Solution**`

## Example 5. Variable-Density Plate

Find the center of mass of the plate in Example 4 if the density at the point $(x,y)$ is $\delta = 2x^2$.

`**Solution**`

## Example 6. Constant-Density Wire

Find the center of mass of a wire of constant density $\delta$ shaped like a semicircle of radius $a$.

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2013.png)

**`Solution`**

# Centroid （质心）

When the density is constant, where the center of mass is located is called **centroid (of the object | shape).** It’s a feature of the geometry of the object and not the material from which it is made. 

---

# Section 6.5 Areas of Surfaces of Revolution

Revolving a curve about one axis results a surface in the space, which is called a *surface of revolution.* The “area” of this surface depends on the length for each portion of the curve and the distance for each portion to the axis of revolution.  We discuss the surface area for  revolution of plane curves in this section. The case of revolution of space curves has to be treated in multi-variable calculus.

## Basic Principle for the Surface Area

### Case 1. Cylindrical surface

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2014.png)

The lateral (侧) surface area of cylindrical surface is defined as 

$$
\text{Lateral Surface Area:}\quad A=2\pi y \Delta x
$$

### Case 2. Frustum of a cone

![Untitled](W2-S2%20Mome%209cfeb/Untitled%2015.png)

The lateral surface area of a frustum of a cone is defined as 

$$
\text{Lateral Surface Area:}\quad A = 2\pi y^* \Delta s = \frac12(2\pi y_1 + 2\pi y_2)\Delta s
$$
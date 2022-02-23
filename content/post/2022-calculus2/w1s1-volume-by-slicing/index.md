---
title: "W1s1 Volume by Slicing"
date: 2022-02-23T12:36:54+08:00
draft: false
tags: ["calculus2", "teach","volume", "demos"]
---

# W1-S1 Volumes by Slicing and Rotation About an Axis

周次: 1
日期: February 23, 2022
节次: 1

In this semester, we will be beginning with the applications of definite integrals. Today’s course is the contents in section 6.1 (Volumes by Slicing and Rotation About an Axis).

# Outline

# Review: Riemann sums & Definite Integral

Definite integral is dealing with summations of infinite many tiny quantities. For example, to calculate the area of region under the curve $y= f(x)$
. 

![Untitled](W1-S1%20Volu%20246ad/Untitled.png)

The approximate “area” is given by Riemann sums associating with a partition $P$ of the finite closed interval $[a,b]$
.

$$
S_P = \sum_{i=1}^n f(x_i) \Delta x_i
$$

This is a finite sum, and each term has a finite (not infinitely small) area. 

![Untitled](W1-S1%20Volu%20246ad/Untitled%201.png)

To define the “area” precisely, we take the limit of $S_P$
 as the norm of the partition $||P||$ approaches zero. The number we get is the following, called the definite integral of $f(x)$.

$$
\int_a^b f(x)dx.
$$

![RiemannIntegralShow.gif](W1-S1%20Volu%20246ad/RiemannIntegralShow.gif)

To evaluate this integral, we have to find the anti-derivative of $f(x)$, i.e. $F(x)$ with $F'(x)\equiv f(x)$. Then the fundamental theorem of calculus shows 

$$
\int_a^b f(x)dx = F(b)-F(a).
$$

# Volumes by Slicing

In this section, we will apply this idea to the calculation of volumes. We can show that for certain regular solid ( shape), we can calculate the volume if the area for cross-sections can be known in prior.

**`Basic Knowledge` For any cylindrical solid, if the base area is $A$ and height is $h$
, the volume is** 

$$
\text{Volume} = A \times h
$$

![Untitled](W1-S1%20Volu%20246ad/Untitled%202.png)

For solids  that are not in cylindrical shape, the volume can be found by the ***method of slicing***.

> **Definition (Cross-section)**
>

A **cross-section** of a solid $S$ is the plane region formed by intersecting $S$ with a plane. E.g. the following graph shows a solid $S$ has a cross-section with plane $P:\{ x=x_0 \}$

![Untitled](W1-S1%20Volu%20246ad/Untitled%203.png)

## Method of Finding the Volumes by Slicing

Suppose a solid $S$ can be positioned between two parallel planes $x=a$ and $x=b$. 

![generalSolidShow.png](W1-S1%20Volu%20246ad/generalSolidShow.png)

To find the volume $V$ of $S$, **assuming** we know the area for any cross-section of $S$ with any plane $P$ perpendicular to the $x$
-axis and positioned at $x$. The area for the cross-section will be denoted by $A(x)$. 

![generalCrossSection.gif](W1-S1%20Volu%20246ad/generalCrossSection.gif)

Then to find the approximation for volume $V$, we will go through the following steps.

1. Partition $[a,b]$ into subintervals, i.e. 

$$
P: a = x_0 < x_1 < \cdots< x_n = b
$$

1. The planes $P_{x_i}$ at $x=x_i$ slice $S$ into thin “slabs”. 
  
    ![generalSolidSlice.gif](W1-S1%20Volu%20246ad/generalSolidSlice.gif)
    

These slabs are approximated by cylindrical solid with base area $A(x_k)$ (How to estimate the inaccuracy ?), and thickness $\Delta x_k.$ The volume for this slab is approximately the same as the volume of cylindrical solid 

$$
\text{Volume of the }k\text{-th slab} \approx V_k = A(x_k)\Delta x_k 
$$

1. The volume $V$ of the entire solid $S$ is approximated by the sum of cylindrical volumes 

$$
V\approx \sum_{k=1}^n V_k = \sum_{k=1}^n A(x_k)\Delta x_k
$$

This is a Riemann sum for the function $A(x)$ on $[a,b]$. **Assuming $A(x)$ is a continuous function on $[a,b]$,** then we can expect the approximation to **improve** as the norm $||P||\to 0$. (❓Which means the approximation is approaching the real value, why.)

![generalSolidApprox.gif](W1-S1%20Volu%20246ad/generalSolidApprox.gif)

Then the volume is defined by 

$$
V = \int_a^b A(x) dx.
$$

> **Definition. (Volume)**
>

The volume of a solid with known integral equation cross-section area $A(x)$ from $x=a$ to $x=b$ is given by the integral

$$
V = \int_a^b A(x) dx.
$$

## Calculating the Volume of a Solid

1. Sketch the solid and a typical cross-section
2. Find the formula of the area $A(x)$
 for general cross-section 
3. Find the upper and lower limits of integration
4. Calculate the definite integral using the Fundamental Theorem.

> **Example 1**. **Volume of a Pyramid**
>

A pyramid $3$
  meter high has a square base that is $3$ meter on a side.

![pyramid.gif](W1-S1%20Volu%20246ad/pyramid.gif)

$$
V = \int_0^3 A(x)dx = \int_0^3 x^2 dx = \left.\frac{x^3}{3}\right]_{0}^3 = 9.
$$

> **Example 2. Volume of a Wedge**
>

A curved wedge is cut from a cylinder of radius 3 by two planes. The first plane is perpendicular to the axis of the cylinder. The second one crosses the first one at a  $45^\circ$
 angle at the center of the  of the cylinder. What is the volume $V$
 for the wedge ?  

- What is the area of the cross section $A(x)=?$

![wedge.gif](W1-S1%20Volu%20246ad/wedge.gif)

> **Example 3. Volume of a Cone (why $1/3$ that of the cylinder?)**
>

A cone is $h$ in height, and $R$
 in radius for the base.

## Cavalieri’s Principle (**祖暅**原理)

Two solids with equal altitudes and identical **cross-sectional areas** at each height have the same volume. (Why?)

![cavalieri.png](W1-S1%20Volu%20246ad/cavalieri.png)

> **Example 4. The hemi*sphere* and the *cylinder with a cone been removed***
>

A hemisphere with $R$
 in radius, the cylinder has radius $R$
 and height $R$
, the cone is described as in Example 3, but with $h=R$.  What is the relation for the volume of  the two solids?

![cavShow.png](W1-S1%20Volu%20246ad/cavShow.png)

![cavAni.gif](W1-S1%20Volu%20246ad/cavAni.gif)

## Solids of Revolution

> The solid generated by rotating a plane region about an axis in its plane is called a **solid of revolution.**
>

In this case, the area of cross-section is usually easy to find. There are a lot of examples.

## Solids of Revolution: The Disk Method ( Disks as Slabs)

> **Example 5. A Solid of Revolution (About the $x$-axis)**
>

The region between the curve $y=\sqrt{x}$, $0\le x\le 4$ about the $x$-axis.

![revSolidAni1.gif](W1-S1%20Volu%20246ad/revSolidAni1.gif)

![revSolidSliceAni1.gif](W1-S1%20Volu%20246ad/revSolidSliceAni1.gif)

> **Example 6. Volume of a sphere (omitted)**
>

A sphere with radius $R$. 

> **Example 7. Rotation about a line $y=1$**
>

A solid is generated by revolving the region bounded by $y=\sqrt{x}$
 and the lines $y=1,$
 $x=4$
 about the line $y=1.$

![revSolidAni2.gif](W1-S1%20Volu%20246ad/revSolidAni2.gif)

> **Example 8. Rotation about the $y$-axis**
>

Find the volume by revolving the region between the $y$
-axis and the curve $x=2/y$
, $1\le y\le 4$
, about the $y$-axis.

![revSolidAni3.gif](W1-S1%20Volu%20246ad/revSolidAni3.gif)

> **Example 9. Rotation about a vertical axis**
>

Find the volume of the solid generated by revolving the region between the parabola $x=y^2+1$
 and the line $x=3$
 about the line $x=3.$

![revSolidAni4.gif](W1-S1%20Volu%20246ad/revSolidAni4.gif)

## Solids of Revolution: The Washer Method (Washers as Slabs)

> **Example 10. A Washer Cross-Section (Rotation about the $x$-axis)**
>

The region bounded by the curve $y=x^2+1$ and the line $y=-x+3$ is revolved about the $x$-axis to generate a solid. 

![revSolidAni6.gif](W1-S1%20Volu%20246ad/revSolidAni6.gif)

> **Example 11. A Washer Cross-Section ( Rotation about the $y$-axis)**
>

 The region bounded by the parabola $y=x^2$
 and the line $y=2x$
 in the first quadrant is revolved about the $y$-axis to generate a solid. (Omitted)

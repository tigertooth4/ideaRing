---
title: "W2-S1 Lengths of Plane Curves"
date: 2022-03-01T15:33:34+08:00
draft: false
tags: ["calculus","teach","Length","curves","math","demos"]
---

周次: 2
备注: Attendance check
日期: March 2, 2022
节次: 1

# Outline

We knew what is meant by the length of a straight line segment, but without calculus, we have no precise notion of the length of a general winding curve. The idea of approximating the length of a curve has no difference with the idea of approximating an area or approximating a volume. By subdividing the curve into many pieces and joining successive points of division by straight line segments, we can then pass through a limit process to find the “real” length of a curve. In this lecture, we show this process and discuss some examples and consequences. 

# Parametric Plane Curves

Let $C$ be a curve given parametrically by the equation 

$$
x =f(t),\quad \text{and}\quad y = g(t),\quad a\le t\le b. 
$$

> **Definition. (Smooth  (Plane) Curve)**
>

If the functions $f$  and $g$ have **continuous derivatives**  on $[a,b]$ ( that is,  $f'(t)$  and $g'(t)$ are both continuous functions, such functions are called **continuously differentiable**) and $f'$ and $g'$ are not simultaneously zero. Then the curve $C$ is called  a **smooth curve**.

**`Remark`**

It is helpful to imagine the curve as the path of a particle moving from point $A = (f(a),g(a))$ at time $t=a$ to point $B=(f(b),g(b))$.

![generalCurve.gif](W2-S1%20Leng%20114cd/generalCurve.gif)

### **Example. (Why $f'$ and $g'$ cannot be simultaneously zero?)**

A plane curve $x=t^2$ and $y=t^3$ ($t\in[-1,1]$) are defined by functions with continuous derivatives. However, the plot shows there is a cusp when $t=0$, the reason being $f'(0)= g'(0)=0$.

![nonSmooth.gif](W2-S1%20Leng%20114cd/nonSmooth.gif)

# Length of a Parametrically Defined Curve

For a plane curve $C: (x=f(t), y=g(t))$ , ($a\le t\le b$). Suppose $f$ and $g$ are continuously differentiable. Set points $A = (f(a),g(a))$ and $B = (f(b),g(b))$. In sequel, *we always assume the path from $A$ to $B$ is traversed exactly once as $t$ increases from $t=a$ to $t=b$.* 

### 1. Partition

We subdivide the closed interval $[a,b]$ into $n$ pieces   

$$
P: a=t_0 < t_1 < \cdots < t_n = b.
$$

The partition $P$ induces a partition on the curve, as 

$$
A = P_0, P_1, \cdots, P_n = B,\quad \text{where}\quad P_k = (f(t_k),g(t_k))
$$

![Untitled](W2-S1%20Leng%20114cd/Untitled.png)

### 2. Length for the straight line segments

Each straight line segment joining the successive points of the partition has length

$$
L_k = \sqrt{(\Delta x_k)^2 + (\Delta y_k)^2} \\ = \sqrt{[f(t_k)-f(t_{k-1}]^2 + [g(t_k) - g(t_{k-1})]^2}
$$

![Untitled](W2-S1%20Leng%20114cd/Untitled%201.png)

### 3. Approximating the curve length

The summation of all the lengths for straight line segment is assumed to be a good approximation for the length of the curve. 

$$
\text{Length of the curve }C\approx \sum_{k=1}^n L_k
$$

By the **Lagrange Mean Value Theorem** , there are numbers $t_k^*$ and $t_k^{**}$ $\in[t_{k-1},t_k]$ such that 

$$
\Delta x_k = f(t_k)-f(t_{k-1}) = f'(t_k^*)\, \Delta t_k,\\ \Delta y_k = g(t_k)- g(t_{k-1}) = g'(t_k^{**}) \, \Delta t_k.
$$

Then 

$$
\sum_{k=1}^n L_k = \sum_{k=1}^n \sqrt{(\Delta x_k)^2 + (\Delta y_k)^2}\\ = \sum_{k=1}^n \sqrt{[f'(t_k^*)]^2 + [g'(t_k^{**})]^2}\,\Delta t_k\\=\sum_{k=1}^n \sqrt{[f'(t_k^*)]^2 + [g'(t_k^{*})]^2}\,\Delta t_k + \text{error}
$$

### 4. Pass through the limit

The above summation is not exactly a Riemann sum (It is a Riemann summation up to an “error term”). However, a theorem in Advanced Calculus shows the error approaches $0$ as $||P||\to 0$. Therefore by passing through the limit process as $||P||\to 0$, we obtain the following  formula for the length of the curve $C$.

![limit.gif](W2-S1%20Leng%20114cd/limit.gif)

> **Definition. (Length of a Parametric Curve)**
>

If a curve is defined parametrically by $x=f(t)$ and $y=g(t)$, $a\le t\le b$, where $f'$ and $g'$are continuous on $[a,b]$, and $C$ is traversed exactly once as $t$ increases from $t=a$ to $t=b$, then **the length of $C$** is the definite integral 

$$
L = \int_a^b \sqrt{[f'(t)]^2 + [g'(t)]^2} dt
$$

**`Remark`**

The different choices for the parametrization of the curve $C$ doesn’t affect the value $L$ at all. As long as the parametrization meets the conditions stated in the definition of the length of $C$.

![circPara.gif](W2-S1%20Leng%20114cd/circPara.gif)

### **Example 1. The Circumference of a Circle**

A circle with radius $r$ can be defined parametrically by  

$$
x=r\cos(t),\quad\text{and}\quad y=r\sin(t),\quad 0\le t\le 2\pi.
$$

Therefore by using the definite integral we can see the length is $L=2\pi r$.

### **Example 2. The length of an astroid**

An astroid is defined by $x=\cos^3(t)$ and $y=\sin^3(t)$, with $0\le t\le 2\pi.$

![Untitled](W2-S1%20Leng%20114cd/Untitled%202.png)

The length of the curve in the first-quadrant is  $L=\dfrac32.$

![astroid.gif](W2-S1%20Leng%20114cd/astroid.gif)

# Special Case: The Length of a Curve $y=f(x)$

Given a continuously differentiable function $y=f(x)$, $a\le x\le b$, we can assign $x=t$ as a parameter. The graph of the function $f$ is then the curve $C$ defined parametrically by 

$$
x=t,\quad \text{and} \quad y=f(t),\quad a\le t\le b.
$$

Then as a special case of parametric curve, the length of the graph $C$ is defined by 

> **Definition. The length of curve $y=f(x)$**
>

If $f$ is continuously differentiable on the closed interval $[a,b]$, then the length of the curve $y=f(x)$ from $x=a$ to $x=b$ is 

$$
L = \int_a^b \sqrt{1+\left(\frac{dy}{dx}\right)^2}dx = \int_a^b \sqrt{1+[f'(x)]^2} dx.
$$

### Example 3. The arc-length of a graph

A graph defined by 

$$
y=\frac{4\sqrt2}{3}x^{3/2} -1,\quad 0\le x\le 1.
$$

is  $L = \dfrac{13}{6}.$

### Example 4. The length of a catenary

![Untitled](W2-S1%20Leng%20114cd/Untitled%203.png)

A catenary is typically expressed as 

$$
y = c \cosh(x/c),\quad \text a\le x \le b.
$$

![catenary.gif](W2-S1%20Leng%20114cd/catenary.gif)

## Dealing with Discontinuities in $dy/dx$

As a case when $dy/dx$ fails to exist, $dx/dy$ may exist. Therefore, we may be able to find the curve length by expressing $x$ as a function of $y$ instead. 

### Example 5. Inverse the expression $y=f(x)$ to $x=g(y)$

Find the length of the curve $y=(x/2)^{2/3}$ from $x=0$ to $x=2.$ By express $x$ as a function of $y$ we find the length is approximately $L\approx 2.27.$

![Untitled](W2-S1%20Leng%20114cd/Untitled%204.png)

# Refined Differential Formula for Length

The length is frequently written in terms of differentials in place of derivatives. Recall that for function $x=f(t)$, the differential $dx$ is defined as 

$$
dx = df = f'(t) dt = \frac{d x}{dt} dt
$$

So the equation for length is written by 

$$
L = \int_a^b \sqrt{(dx)^2+(dy)^2}.
$$

It is customary to eliminate the parentheses in $(dx)^2$ and write $dx^2$ instead. So 

$$
L = \int_a^b \sqrt{dx^2+dy^2}
$$

This is a unified formula for length. For different cases, one must express $x$ and $y$ in suitable parametrization and restore the formula $L = \int_a^b \sqrt{dx^2+dy^2} = \int_a^b \sqrt{g'(t)^2+g'(t)^2}dt$ to compute. 

A useful way is to write 

$$
ds = \sqrt{dx^2+dy^2}
$$

and treat $ds$ as the **differential of arc-length (弧长微元)**, which can be integrated between appropriate limits to give the total length of a curve. The geometric meaning of $ds$ is shown below, as an approximation of length for tiny arc-segment. Then to memorize, first recall the shortest expression 

$$
L = \int ds
$$

Then recall $ds = \sqrt{dx^2+dy^2}$, finally choose appropriate parametrization to expand $dx^2+dy^2$, as well as specify the the integral limits $a$ and $b$.

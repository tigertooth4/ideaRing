# /W4-S2 Transcendental Functions (2)

周次: 4
备注: Attendance check
日期: March 18, 2022
节次: 2

In this lecture, we continue on the discussion of  logarithmic and exponential functions. The simplest differential equation is discussed, there are a lot of real applications even for such simple equations. And the definitions of growth rates are given in terms of the notation “big-oh” and “little-oh”. The other main topic is the inverse trigonometric functions, and their basic properties.  

# Outline

# § 7.3 The Exponential Function

This section was largely discussed in the last semester. We only note one thing: By using the chain rule, we have the following general power rule.

> **Power Rule (General Form)**
> 

For any $x>0$ and any **real number** $r$ as $x^r:=e^{r\ln x}.$ The derivative 

$$
\frac{d}{dx}x^r = r x^{r-1}.
$$

Thus, for any positive differentiable function $u$ of $x$ and $r$ is any real number, then $u^r$ is differentiable and 

$$
\frac{d}{dx}u^r = r u^{r-1}\frac{du}{dx}.
$$

### Examples

- $\frac{d}{dx}x^{\sqrt{2}} = \sqrt{2} x^{\sqrt2-1}$.
- $\frac{d}{dx}(2+\sin 3x)^\pi = 3\pi (2+\sin 3x)^{\pi-1}(\cos 3x).$

# § 7.4 $a^x$ and $\log_a x$

This part is left as a self-learning task.

# § 7.5 Exponential Growth and Decay

## The Law of Exponential Change

A quantity $y$ increases or decreases at a rate proportional to its size at a given time $t$. Such quantities change according to the *law of exponential change.*

If the amount present at time $t=0$ is called $y_0$, then we can find $y$ as a function of $t$ by solving the following initial value problem: 

$$
\text{Differential equation:} \quad \frac{dy}{dt} = k\cdot y\\ \text{Initial condition:}\quad y=y_0 \quad \text{when} \quad t=0.
$$

Any differentiable function $y$ of $x$ satisfies these conditions is called a solution to the differential equation. 

The equation describes a quantity $y$ grows at a rate proportional to what has already been accumulated. If $k$ is positive, and the initial value $y_0$ is positive, then the change rate of $y$ stays positive. Otherwise, if $k$ is negative and $y_0$ is positive, then the change rate of $y$ stays negative. If $y_0=0$, we see that the constant function $y=0$ is a solution. To find general solution, we utilize the method called “***separation of variables***”.  

$$
\frac{1}{y}\cdot \frac{dy}{dt} = k
$$

  Integrate with respect to $t$, we get 

$$
\ln|y| = k\, t + C
$$

Therefore $y = \pm e^{C} \exp(k\, t)$, or simply $y= A \exp(k\, t)$, where $A$ is any real number. To incorporate  the initial condition, the coefficient $A$ can be fixed.  

$$
y_0 = A \exp(k\, 0) = A.
$$

So there is only one solution $y=y_0 \exp(k \, t)$ satisfies the differential equation with the particular initial condition.

The solution is describing a quantity changing in the way of **exponential growth** (if $k>0$), and **exponential decay** if $k<0$. 

> **The Law of Exponential Change**
> 

$$
y=y_0 \exp(k\, t)\\ \text{Growth if } k>0,\quad \text{Decay if } k<0
$$

The number $k$ is the **rate constant** of the equation.

The applications of exponential change ranges from population growth to Newton’s law of cooling. We’ll list some of the applications in the following.

## Example: Population Growth or Decay

Suppose the proportion of reproducing individuals remains constant and assume a constant fertility, then at any instant $t$ the birth rate is proportional to the number $y(t)$ of individuals present. Assuming the death rate of the population is stable and proportional to $y(t)$. Neglecting the departures and arrivals, we have 

$$
\frac{dy}{dt} = (\text{birth rate} - \text{death rate})\, y(t) := k\cdot y
$$

So the population at any given instant $t$ equals to $y_0 \exp(k t)$ where $y_0$ is the initial population.

> **Reducing the Cases of an Infectious Disease**
> 

Assume the number of infection is defined as $y(t)$, at given year $t$. Suppose the number of a disease is reduced by 20% each year. If there are $10k$ cases today, how many years will it take to reduce the number to $1k$?

## Example: Radioactivity (Omitted)

Some atoms are unstable and can spontaneously emit mass or radiation. The process is called **radioactive decay**, and an element whose atoms go spontaneously through this process is called **radioactive.** 

Experiments shows at any given time the rate at which a radioactive element decays is approximately proportional to the number of radioactive nuclei present.  Thus the decay of a radioactive element is described by the equation $dy/dt = -k\, y$, $k>0$. If $y_0$ is the number of radioactive nuclei present at time zero, then the number still present at any later time $t$ will be 

$$
y=y_0 \exp(-kt),\quad k>0
$$

> **Half-Life of a Radioactive Element**
> 

The **half-life** of a radioactive element is the time required for half of the radioactive nuclei present in a sample to decay. Half-life is a constant that does not depend on the number of radioactive nuclei initially present in the sample, but only on the radioactive substance.

$$
y_0 e^{-k t} = \frac12 y_0,\quad\implies \quad t = \frac{\ln 2}{k}.
$$

> **Carbon-14 Dating**
> 

The decay of radioactive elements can sometimes be used to date events from the Earth’s past. In a living organism, the ratio of radioactive carbon, carbon-14, to ordinary carbon stays fairly constant during the lifetime of the organism. After the organism’s death, no new carbon is ingested, and the proportion of carbon-14 in the organism’s remains decreases as the carbon-14 decays. Scientists who do carbon-14 dating use a figure of 5700 years fro its half-life.

## Example: Heat Transfer (Newton’s Law of Cooling)

Hot soup left in a tin cup cools to the temperature of the surrounding air. A hot silver ingot immersed in a large tub of water cools to the temperature of the surrounding water. 

An object’s temperature is changing at any given time is roughly proportional to the difference between its temperature and the temperature of the surrounding medium. This observation is called *Newton’s law of cooling.*

If $H$ is the temperature of the object at time $t$ and $H_s$ is the constant surrounding temperature, then 

$$
\frac{dH}{dt} = -k (H-H_s).
$$

Then let $y=H-H_s$, we obtain 

$$
\frac{dy}{dt} = -k\, y,\quad \implies \quad y = H-H_s = (H_0-H_s) e^{-k t}.
$$

> **Cooling a Hard-Boiled Egg**
> 

A hard-boiled egg at $98^\circ \text{C}$ is put in a sink of $18^\circ\text{C}$ water. After $5$ min, the egg’s temperature is $38^\circ\text{C}$. Assuming that the water has not warmed appreciably, how much longer will it take the egg to reach $20^\circ\text{C}$ ?  (13 min)

# § 7.6 Relative Rates of Growth

It is important to compare the rates at which functions of $x$ grow as $x$ becomes large. Exponential functions are important in these comparisons because of their very fast growth, and logarithmic functions because of their very slow growth. In this section we introduce the *little-oh* and *big-oh* notation used in these comparison. We restrict our attention to functions whose values eventually become and remain positive as $x\to \infty.$

![Untitled](W4-S2%20Tran%20ace19/Untitled.png)

To get a feeling for how rapidly the value of $y=e^x$ grows, think of the $x$-axis scaled in centimeters. At $x=1\text{cm}$, the graph is about $3\text{cm}$ above the $x$-axis. At $x=10\text{cm}$, the graph is about $220$ meters high. At $x=24\text{cm}$, the graph is more than halfway to the moon! At $x=43\text{cm}$, the graph is about $5$-light-years! 

![Untitled](W4-S2%20Tran%20ace19/Untitled%201.png)

In contrast, logarithmic function $y=\ln x$ grow more slowly as $x\to\infty$. You have to go nearly $5$ light-years out on the $x$-axis to find a point where the graph is at $y=43\text{cm}$ high.

> **Definition. Rates of Growth as $x\to\infty$**
> 

 Let $f(x)$ and $g(x)$ be positive for $x$ sufficiently large.

1. $**f$ grows faster than $g$ as $x\to \infty$, if** 

$$
\lim_{x\to\infty} \frac{f(x)}{g(x)} = \infty,\quad \text{or, equivalently, if} \quad \lim_{x\to\infty}\frac{g(x)}{f(x)} = 0.
$$

We also say that $**g$ grows slower that $f$ as $x\to\infty$.**

1. $**f$ and $g$ grow at the same rate as $x\to\infty$ if** 

$$
\lim_{x\to\infty}\frac{f(x)}{g(x)} = L
$$

where $L$ is finite and positive. 

`**Remark` $y=2x$** does not grow faster than $y=x$. 

### Example 1. Several Useful Comparisons of Growth Rates

1. $e^x$ grows faster than $x^2$ as $x\to\infty$
2. $3^x$ grows faster than $2^x$ as $x\to\infty$
3. $x^2$ grows faster than $x$ as $x\to \infty$
4. $\ln x$ grows slower than $x$ as $x\to \infty$
5. $a^x$ and $b^x$ grow at different rate if $a\neq b$
6. $\log_a x$ and $\log_b x$ grow at the same rate 

If $f$ and $g$ grow at the same rate, and $g$ and $h$ grow at the same rate, then $f$ grows at the same rate as $h$.

### Example 2.

Show that $\sqrt{x^2+5}$ and $(2\sqrt{x}-1)^2$ grow at the same rate as $x\to\infty.$ 

## Order and Oh-Notation

> **Definition. Little-oh**
> 

A function $f$ is **of smaller order than $g$ as $x\to\infty$** if $\lim_{x\to\infty}\frac{f(x)}{g(x)} = 0$. We indicate this by writting $f = o(g)$ (”$f$ is little-oh of $g$”).

### Example 3. Using Little-oh Notation

1. $\ln(x) = o(x)$ as $x\to\infty$
2. $x^2=o(x^3+1)$ as $x\to \infty$

> **Definition. Big-oh**
> 

Let $f(x)$ and $g(x)$ be positive for $x$ sufficiently large. Then $f$ is **of at most the order of $g$ as $x\to\infty$** if there is a positive integer $M$ for which 

$$
\frac{f(x)}{g(x)}\le M
$$

for $x$ sufficiently large. We indicate this by writing $f = O(g)$ (”$f$ is big-oh of $g$”).

### Example 4. Using Big-oh Notation

1. $x+\sin x = O(x)$ as $x\to\infty$
2. $e^x+x^2 = O(e^x)$ as $x\to\infty$
3. $x = O(e^x)$ as $x\to\infty$

`**Note`** $f=o(g)$ implies $f=O(g)$ for functions that are positive for $x$ sufficiently large. If $f$ and $g$ grow at the same rate, then $f=O(g)$ and $g = O(f)$.

# § 7.7 Inverse Trigonometric Functions

The six basic trigonometric functions are not one-to-one. However, we can restrict their domain to intervals on which they are one-to-one. The sine function increases from $-1$ at $x=-\pi/2$ to $1$ when $x=\pi/2$. By restricting its domain to the interval $[-\pi/2,\pi/2]$ we make it one-to-one, so it has an inverse $\sin^{-1}(x)$.

![Untitled](W4-S2%20Tran%20ace19/Untitled%202.png)

The cosine function is one-to-one on $[0,\pi]$.

![Untitled](W4-S2%20Tran%20ace19/Untitled%203.png)

The tangent function is one-to-one on $(-\pi/2,\pi/2)$.

![Untitled](W4-S2%20Tran%20ace19/Untitled%204.png)

The cotangent function is  one-to-one on $(0,\pi)$.

![Untitled](W4-S2%20Tran%20ace19/Untitled%205.png)

The secant function is one-to-one on $[0,\pi/2)\cup (\pi/2,\pi]$.

![Untitled](W4-S2%20Tran%20ace19/Untitled%206.png)

The cosecant function is one-to-one on $[-\pi/2,0)\cup(0,\pi/2].$

![Untitled](W4-S2%20Tran%20ace19/Untitled%207.png)

Those restricted trigonometric functions have inverses, denoted by (arc). So we have $\arcsin(x)$, $\arccos(x)$, $\arctan(x)$, $\mathrm{arccot}(x)$, $\mathrm{arcsec}(x)$ and $\mathrm{arccsc}(x)$. 

## The Arcsine and Arccosine Functions

> **Definition.**  **Arcsine and Arccosine Functions**
> 
- $y=\sin^{-1}(x)=\arcsin(x)$ is the angle in $[-\pi/2,\pi/2]$ whose sine is $x$.
- $y=\cos^{-1}(x) = \arccos(x)$ is the angle in $[0,\pi]$ whose cosine is $x$.

![Sine (blue) and arcsine (yellow) functions ](W4-S2%20Tran%20ace19/Untitled%208.png)

Sine (blue) and arcsine (yellow) functions 

The graph of $y=\arcsin(x)$ is symmetric about the origin, therefore an odd function. 

$$
\arcsin(-x) = -\arcsin(x).
$$

![Cosine (blue) and arccosine (yellow) functions](W4-S2%20Tran%20ace19/Untitled%209.png)

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

![The graph of arctan(x)](W4-S2%20Tran%20ace19/Untitled%2010.png)

The graph of arctan(x)

The graph of $\arctan(x)$ is symmetric with respect to the origin. Namely, And $\mathrm{arccot}(x)$ has no such symmetries.

$$
\tan(-x) = - \tan(x).
$$

![The graph of arccot(x)](W4-S2%20Tran%20ace19/Untitled%2011.png)

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

![Untitled](W4-S2%20Tran%20ace19/Untitled%2012.png)

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
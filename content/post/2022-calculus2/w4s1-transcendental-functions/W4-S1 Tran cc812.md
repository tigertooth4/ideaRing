# W4-S1 Transcendental Functions

周次: 4
日期: March 16, 2022
节次: 1

In this and next lectures, we will quickly go through the contents in chapter 7. Since a lot of the contents have been taught last semester or have known in high school age. 

# Outline

# § 7.1 Inverse Functions and Their Derivatives

We have learned inverse functions, their domain and range, their graph, etc. In particular, we have the following fact for the derivative for inverse functions.

> **Theorem.**
> 

Suppose $y=f(x)$ is a differentiable function and $f'(x_0)$ is not zero. Then $f^{-1}(y)$ is differentiable at $f(x_0)$, and $\frac{d}{dy}\big|_{y=f(x_0)}f^{-1}(y) = \frac{1}{f'(x_0)}$.

 

> **Use**
> 

In practice, the inverse function is usually written as a function of $x$, therefore the derivative is often written as  

$$
\frac{d}{dx}f^{-1}(x) = \frac{1}{f'(f^{-1}(x))}.
$$

# § 7.2 Natural Logarithms

We have been quite familiar with the definition and basic properties for the natural logarithm $f(x) = \ln (x)$. So in this section, we only focus on the derivative and anti-derivatives for the natural logarithms.

## The derivative for natural logarithms

For the derivative of natural logarithm $y=\ln(x)$, we actually have at least two ways to calculate it. 

> **Two Approaches for $\frac{d}{dx}\ln(x)$.**
> 
- As an inverse of exponential function $y=\exp(x)$
- As a consequence of important limit $\lim_{x\to\pm\infty}(1+\frac1x)^x = e$

## An important note

Look at a slightly general version of natural logarithm $y=\ln|x|$. The domain is $\mathbb{R}\smallsetminus\{0\}$. The derivative for $y=\ln|x|$ is actually everywhere defined on its domain. An important note is the following. 

> **Proposition.**
> 

$$
\frac{d}{dx}\ln|x| = \frac1{x}.
$$

Then by using the chain rule, we know that  for differentiable function $f(x)$, 

$$
\frac{d}{dx}\ln|f(x)| = \frac{f'(x)}{f(x)}
$$

## The anti-derivative

Due to the previous proposition, the anti-derivative for $1/x$, if not specified, will be $\ln|x| + C$., namely,

$$
\int\frac{1}{x}dx = \int\frac{dx}{x} = \ln|x| + C.
$$

Moreover, 

$$
\int \frac{f'(x)}{f(x)}dx = \ln|f(x)| + C.
$$

### Examples (Applying the anti-derivatives to definite integrals)

1. $\int_0^2 \frac{2x}{x^2-5}dx$
2. $\int_{-\pi/2}^{\pi/2}\frac{4\cos\theta}{3+2\sin\theta}d\theta$

## The integrals of $\tan(x)$ and $\cot(x)$

We have 

$$
\int\tan(x)dx = \ln|\sec(x)|+C,\quad \int\cot(x)dx = -\ln|\csc(x)|+C.
$$

### Example

- $\int_0^{\pi/6}\tan 2x dx$

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

![Untitled](W4-S1%20Tran%20cc812/Untitled.png)

To get a feeling for how rapidly the value of $y=e^x$ grows, think of the $x$-axis scaled in centimeters. At $x=1\text{cm}$, the graph is about $3\text{cm}$ above the $x$-axis. At $x=10\text{cm}$, the graph is about $220$ meters high. At $x=24\text{cm}$, the graph is more than halfway to the moon! At $x=43\text{cm}$, the graph is about $5$-light-years! 

![Untitled](W4-S1%20Tran%20cc812/Untitled%201.png)

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
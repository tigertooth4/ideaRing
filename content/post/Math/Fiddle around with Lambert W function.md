---
title: "Fiddle around with Lambert W function"
date: "2012-04-07 17:29:45"
draft: false
Tags: ["Math", "Geometry"]
author: "tt4"
---

Title:

Date:

[mathjax]

These days I was fiddling around with one particular parameterization for Lambert curve. Although it was not that hard, I was happy that finally I made it clear.

The problem is like this: a _Lambert curve_ is a curve given by \[C = \{(z,w) \; | \; z = w e^w \} \subset \mathbb{C}^* \times \mathbb{C}^*.\] Note that the above equation defines \(w\) as an implicit function of \(z\). Such functions are not unique, we call them the [Lambert W function](http://en.wikipedia.org/wiki/Lambert\_W\_function "Lambert W function") .

more

By inverse function theorem, \(w\) can be written locally as a function of \(z\). Note that there are two branches, the branches we care about is called \(w_0\). From wikipedia, one could find the asymptotic expansion of \(w_0\) w.r.t. \(z\), which is \[w_0(z) = \sum_{k\ge 1}\frac{(-k)^{k-1}}{k!}x^k.\] Now if we redefine the Lambert curve to be \(x = y e^{-y}\), and define \[t = 1 + \sum_{k=1}^\infty \frac{k^k}{k!}x^k,\] how the expression \(x=y e^{-y}\) may be changed when we substitute \(y\) by \(t\)?

Notice that the Taylor expansions of \(w_0(z)\) and \(t(x)\) are alike, it is not so hard to establish a functional relationship between the two. So lets start by finding a Taylor series of \(y\) w.r.t. \(x\). It is easy to see two definitions of Lambert curves are identified if we introduce the transform \(y(x) = -w_0(x)\). So \(y\) can be expand to a Taylor series: \[y(x)=\sum_{k\ge 1}\frac{k^{k-1}}{k!}x^k.\] By term-by-term differentiation, we know \(x y'(x) = t-1\). But from another point of view, by implicit differentiation, we find \(1 = xy'(y^{-1} - 1)\). So \(y = 1-t^{-1}\). And, if written in the new parameter \(t\), Lambert curve can be formatted as \[x = (1-t^{-1}) e^{-(1-t^{-1})}.\]

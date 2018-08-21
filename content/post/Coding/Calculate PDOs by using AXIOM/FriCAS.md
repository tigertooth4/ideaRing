+++
  title = "Calculate PDOs using AXIOM / FriCAS"
  date = "2012-05-03 00:46:30"
  tags = ["FriCAS", "PDO", "Coding", "Math"]
  author = "tt4"
+++

For years, the computation of Lax equations is a tedious and time-consuming task. For example, KdV equation has the following type of Lax equation:
\`\`\`mathjax
L\_t = [A, L],
\`\`\`
where \`\`\`mathjax L=\partial^2+u(x,t)\`\`\`, \(A=\partial^3+4u(x,t)\partial+2u\_x\). Having been a graduate student majoring in _integrable systems_ for years, I always had to work on such kind of computations. It was frustrating. At that time, I was thinking of a way to speed up the computation with the power of computers. After a long time searching, I realized there was no software with built in support for such computations.  Although many people might have their own tricks to do such computation with the aid of symbolic software, for example _Mathematics_, _Maple_, I think it was not the most efficient way.

After graduate, I found a paper dealing with the computation of PDOs. This paper was written by _W. Seiler_, who wrote an _AXIOM_ package to calculate pseudo-differential operators. However, his package was so old to work properly under AXIOM. But his idea was great: Using _stream_ to store the coefficients of each PDO, which may contain an infinite number of elements, and using two indices to maintain the leading and last orders for this PDO. The arithmetic operations of PDOs was realized by adding up or multiplying the corresponding elements of streams. Note that when doing such kinds of computations, a internal mechanism  of AXIOM would ensure the adding or multiplying to be _lazy_. Namely, the computation was done when it was necessary.

I had noticed this package also contains type coerce functions which can convert a differential operator in PDO to a _Linear Ordinary Differential Operator_ (LODO in short). And, for ordinary differential operators, the addition and multiplication are identical with the PDO case. Curiously, I decided to check the source code of LODO, see how the LODO functions. To my surprise, the LODO can be defined in a very general manner. In the source code, I found the LODO was a very special case of a more general domain: _skew-polynomial_.

What is a skew-polynomial? Well, simply speaking, skew-polynomial is a polynomial, for example \(\sum\_{0\le i\le n} a\_i x^i\), except that the coefficient does not commute with indeterminate \(x\). In general, supposing \(a\_i\) are elements of some Ring (do not need to be commutative), say \(R\). Let \(\sigma: R\longrightarrow R\) be an automorphism of \(R\), and \(\delta:R\longrightarrow R\) be a \(\sigma\)-derivative, which is to say [\delta(ab) = \sigma(a)\delta(b)+\delta(a)b.] Then the multiplication of \(x\) and \(a\in R\) is defined by [x\cdot a = \sigma(a) x + \delta(a).]

Such skew-polynomial have many special cases. Many of them have very broad uses.

Suppose Ring \(R\) to be the ring of smooth functions of single variable. And Suppose indeterminate \(x\) to be noted by \(\partial\). If we set the automorphism \(\sigma\) be identity map, while the \(\delta\)-derivative be the usual derivative for single variable function, then the product of \(f\) and \(\partial\) is [\partial f = f \partial + f',] which is exactly the basic product law for pseudo-differential operators.

If the Ring \(R\) is set to be the ring of functions with a discrete variable \(n\), the indeterminate \(x\) be the _shift operator_ \(\Lambda\), the automorphism \(\sigma\) be the mapping maps \(f(n)\to f(n+1)\), the \(\delta\)-derivative be the vanishing map, then the product is [\Lambda f(n)= f(n+1) \Lambda,] which defines the basic product law for shift operators.

If the Ring \(R\) is still the ring of functions with a discrete variable \(n\), the indeterminate \(x\) be the _difference operator_ \(\Delta\), the automorphism \(\sigma\) be the mapping maps \(f(n)\to f(n+1)\), the \(\delta\)-derivative be the difference operation, which maps \(f(n)\) to \(\Delta(f(n))=f(n+1)-f(n)\), then the product is [\Delta f(n)= f(n+1) \Delta + \Delta(f(n)),] which defines the basic product law for difference operators.

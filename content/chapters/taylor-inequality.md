+++
title="8. Taylor series and approximation"
date=2023-07-12
+++

In this section, we start with primitive methods of approximating functions with polynomials. We develop a systematic method of approximation and extend this idea to an infinite number of terms.

## Polynomial interpolation

_Given a set of $n$ data points, how can we find a smooth curve passing through all of them?_

We may always find a polynomial of degree \\(n-1\\) capable of passing through \\(n\\) data points. The **Newton polynomial** is one algorithm for finding the coefficients.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Newton interpolation polynomial") %}
Given $k$ points $(x_i,y_i)$ where no two $x_i$ are the same, the Newton interpolation polynomial is given by the equation

$$N(x)=\sum^N_k \left( [y_o,\ldots,y_k] \prod^{k-1}_{i=0}(x-x_i)\right )$$

For the special case where the points are equidistant in the $x$-axis by $h$ from each other, we may reduce the divided difference $[y_o,\ldots,y_k]$ to:

$$N(x)=\sum^N_k \left( \frac{\Delta^n y_0}{n!\,h^n} \prod^{k-1}_{i=0}(x-x_i)\right )$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Lagrange interpolating polynomial") %}
Given $n$ points $(x_i,y_i),\,i\in\mathbb{N}$, the Lagrange interpolating polynomial fitting all of them is:

$$L(x)=\sum^n_{k=0}\left ( y_k \prod^n_{j=0,j\ne k} \frac{x-x_j}{x_k-x_j} \right )$$
{% end %}

## Taylor polynomial

We develop the idea of Taylor polynomials from linear approximations.
For any continuous curve, we may approximate its values around a central point $x_0$ by

1. Finding the tangent line to the curve at $x_0$ as a function of $x$
2. Evaluating the tangent line's value at points next to $x_0$

Therefore, $f(x)\approx f(x_0) + f'(x_0)(x-x_0)$ as a linear approximation.

Could we do this with a quadratic function? Yes. Choose two points around $x_0$ with equal $\Delta x$ away from $x_0$ and take the limit as it approaches zero. The resulting function of $x$ is the quadratic approximation:

$$f(x)\approx f(x_0) + f'(x_0)(x-x_0) + \frac{1}{2}f''(x_0)(x-x_0)^2$$

We find that this approximation will always be more accurate than the linear approximation. For example, for the function $\sin(x)$:

{% graph(ref="Sine function approximated", x_label="x", y_label="y", caption="Approximations of the sine function centred at $x=0$") %}
{ fn: 'sin(x)' },
{ fn: 'x' },
{ fn: 'x-0.5x^2'}
{% end %}

In this pattern, we extend to an approximation using a polynomial with $n$ terms. We call an approximation of this form a _Taylor polynomial_.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Taylor Polynomial") %}
Given a function $f$ continuous around a point $x_0$, the Taylor polynomial approximation $P_{n,x_0}$ centered at $x_0$ consisting of $n$ terms is:

$$P_{n,x_0}=\sum^n_{k=0}{1\over{k!}}f^{(k)}(x_0)(x-x_0)^k$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Maclaurin's Theorem (1742)") %}
If $P(x)=a_0+a_1(x-x_0)+\ldots+a_n(x-x_0)^n$, and 

$$P^{(k)}(x_0)=f^{(k)}(x_0)\\,\forall k\in\set{0,1,2,\ldots,n}$$

then $P(x)$ is equivalent to the defined $n$th term Taylor polynomial for $f$.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

## Manipulating Taylor polynomials

There are many "shortcuts" to construct Taylor polynomials from known polynomials.
They may be proved using [Maclaurin's Theorem](./#maclaurin-s-theorem-1742)

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Addition of Taylor polynomials") %}
Given $h(x)=f(x)+g(x)$, the Taylor $n$th term polynomial for $h(x)$ is equal to the addition of the $n$th term Taylor polynomials of $f$ and $g$.

$$H_{P(n,x_0)}(x)=F_{P(n,x_0)}(x)+G_{P(n,x_0)}(x)$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Composition of Taylor polynomials") %}
Given $h(x)=f(g(x))$, the Taylor $n$th term polynomial for $h(x)$ is equal to composition of the $n$th term Taylor polynomial for $f$ and $g(x)$.
$$H_{P(n,x_0)}(x)=F_{P(n,x_0)}(g(x))$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Derivative of Taylor polynomials") %}
Given $h(x)=f'(x)$, the Taylor $n$th term polynomial for $h(x)$ is equal to the derivative of the Taylor $n+1$th polynomial for $f(x)$.

$$H_{P(n,x_0)}(x)=\frac{d}{dx}F_{P(n+1,x_0)}(x)$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Integral of Taylor polynomials") %}
Given $h(x)=\int f(x)\\,dx$, the Taylor $n$th term polynomial for $h(x)$ is equal to the integral of the $n-1$th term Taylor polynomial for $f$.

$$H_{P(n,x_0)}(x)=\int F_{P(n-1,x_0)}(x)\\,dx + C$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

## Taylor remainder

We know Taylor polynomials are only approximations of continuous functions.
That means the exact value of a function is equal to the Taylor polynomial _plus_ a remainder term.
This remainder term is called the _Taylor remainder_.

$$f(x)=T_{f,n,x_0}(x) + R_{f,n,x_0}(x)$$

There are many expressions for the Taylor remainder.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Lagrange Remainder (1797)") %}
Let $f:\mathbb{R}\to\mathbb{R}$ be $k+1$ times differentiable on the open interval with $f^{(k)}$ continuous on the closed interval between $a$ and $x$. Then

$$R_k(x)=\frac{f^{(k+1)}(\xi_L)}{(k+1)!}(x-a)^{k+1}$$

for some real number $\xi_L$ between $a$ and $x$.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Cauchy Remainder (1823)") %}
Let $f:\mathbb{R}\to\mathbb{R}$ be $k+1$ times differentiable on the open interval with $f^{(k)}$ continuous on the closed interval between $a$ and $x$. Then

$$R_k(x)=\frac{f^{(k+1)}(\xi_C)}{k!}(x-\xi_C)^k(x-a)$$

for some real number $\xi_C$ between $a$ and $x$.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

## Taylor series

The _Taylor series_ is a Taylor polynomial with $n\to\infty$.
It is an infinite power series that converges to a continuous function, and is of the form:

$$\sum^\infty_{n=0} \frac{f^{(n)}(x_0)}{n!} (x-x_0)^n$$

> We take the order-zero derivative of $f$ to be $f$ itself. $(x-a)^0$ and $0!$ are defined to be 1.

## Common infinite series

{% theorem(ref="p-Series") %}
The $p$-Series is an infinite series of the form:

$$\sum^\infty_{n=1}\frac{1}{n^p}$$
{% end %}

## Tests of convergence

What are the steps:

1. Check the necessary condition of convergence $\lim_{n\to\infty} a_n=0$.
2. Consider a sequence of partial sums and what happens when its $\lim_{n\to\infty} S_n$.
3. Choose and apply a convergence test if 1. and 2. yield inconclusive results (not diverging).

The necessary condition for convergence is that

$$\lim_{n\to\infty} a_n=0$$

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Ratio test") %}
Consider a series $\sum a_n$, $a_n>0$. Let $\lim_{n\to\infty}\frac{a_{n+1}}{a_n}=L$. Then:

- If $L < 1$, the series converges.
- If $L > 1$, the series diverges.
- If $L=1$, the test is inconclusive.

{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- EXAMPLE ------------------------------------------------------------->
{% example(ref="Proof of the ratio test") %}
Consider the limit $\lim_{n\to\infty} \frac{a_{n+1}}{a_n}=L$.

Then $L < 1\implies \exists r < 1, \exists n_o: \forall n > n_o$:

$$a_{n_o+1}\le r a_{n_o}$$

$$a_{n_o+2}\le r a_{n_o+1} \le r^2a_{n_o}$$

and so on.

Then we find that:

$$\sum^\infty_{n=n_o}a_n \le a_{n_o}\sum^\infty_{k=0}r^k < \infty$$

In a similar way, the series diverges if $L > 1$ 

{% end %}
<!-- END EXAMPLE --------------------------------------------------------->

<!-- EXAMPLE ------------------------------------------------------------->
{% example(ref="Harmonic series ratio test") %}
Does the harmonic series, $\sum^\infty_{n=1}\frac{1}{n}$ converge?

We see that the general terms $a_n=\frac{1}{n}$ and $a_{n+1}=\frac{1}{n+1}$.
Constructing a ratio, we get:

$$
\begin{align*}
&\quad\quad\quad\frac{a_{n+1}}{a_n}=\frac{n}{n+1}\\\\
&\implies \lim_{n\to\infty}\frac{a_{n+1}}{a_n}=1
\end{align*}
$$

Therefore we do not know whether the series converges using the ratio test.
{% end %}
<!-- END EXAMPLE --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Root test") %}
Consider a series $\sum a_n$, $a_n>0$. Let $\lim_{n\to\infty}\sqrt[n]{a_n} = L$.
Then:

- If $L < 1$, the series converges.
- If $L > 1$, the series diverges.
- If $L=1$, the test is inconclusive.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

## See also

1. Wikipedia. (2023). *Taylor series*. https://en.wikipedia.org/wiki/Taylor_series
2. Weisstein, Eric W. (2023). *Maclaurin Series.* Wolfram Web MathWorld. https://mathworld.wolfram.com/MaclaurinSeries.html


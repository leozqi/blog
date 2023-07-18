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



> an infinite series that converges to any selected, continuous function within a range.

A Taylor series is a [[Power series|power series]] that takes on the form:
?
$$\sum^\infty_{n=0} \frac{f^{(n)}(a)}{n!} (x-a)^n$$
<!--SR:!2024-03-20,267,290-->

The Taylor series approximates the output value of a function $f$ with inputs $x$ 1) **at** and 2) **within an interval** centered at $x = a$ for the form above.
We calculate the Taylor series by expanding it for values of $n = \{0, 1, 2, \ldots \}$ and it gets greater precision as more terms are added.
We may choose an $a$ value closest to the input value of the function we wish to approximate, although as $n$ becomes larger the interval that is approximated accurately also becomes larger.

> [!info]
> The derivative of order zero of $f$ is defined to be $f$ itself.
> $(x - a)^0$ and $0!$ are both defined to be 1.

Partial sums of a Taylor series are called **Taylor polynomials** and give an increasingly better approximation of the original function for greater $n$.
For example, the Taylor series expansion centered at $a = 0$ that approximates $f(x) = \frac{3}{10 - x}$ is:

$$\sum^\infty_{n=0} \frac{f^{(n)}(a)}{n!} (x-a)^n = \frac{3}{10} + \frac{3x}{100} + \frac{3x^2}{1000} + \frac{3x^3}{10000} + \ldots$$

The calculation steps are, for each term:

1. Find the $n$-th order derivative for $f$.
2. Sub in the $a$-value in place of the $x$.
3. Divide this term by $n!$.
4. Multiply to this the term $(x-a)^n$.

$\frac{3}{10} + \frac{3x}{100} + \frac{3x^2}{1000}$ would be a **Taylor polynomial** approximation of $f$ to $n=2$.

> [!Maclaurin series]
> A Taylor series that is centred at $x=a=0$. This is a common special case of the Taylor series with the form:
>
> $$\sum^\infty_{n=0} \frac{f(0)^{(n)}}{n!} x^n$$
>
> [defn::maclaurin-series]
> ^maclaurin-series

> [!Taylor's inequality]
> Suppose $\lvert f^{(n+1)}(z)\rvert\le K$ for all $z\in[x_0, x]$. That is, $K$ is the upper bound of $\lvert f(z)\rvert$ for any $z$. Then
>
> $$\lvert R_n(x)\rvert \leq K\frac{\lvert x-x_0\rvert^{n+1}}{(n+1)!}$$
>
> $K$ is the upper bound for $\lvert f^{(n+1})(z)\rvert$, not necessarily the maximum, and follows from the Lagrange form of the Taylor remainder.
>
> [defn::taylor-inequality]
> ^taylor-inequality

> [!Example]
> > Estimate the accuracy of the Maclaurin approximation
> >
> > $$e^x \approx 1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\frac{x^4}{4!}$$
>>
>> at $x=1$.
>
> Note that the remainder, or error of the approximation is given using our theorem as:
>
> $$\begin{align}& \lvert R_4(x)\rvert\leq \text{max}_{x\in[0,1]}\left\lvert f^{(5)}(x)\right\rvert \frac{\lvert x\rvert^5}{5!}\\ \text{where} &\ f^{(5)}(x)=e^x\\ &\implies \text{max}_{x\in[0,1]} \lvert f^{(5)}(x)\rvert <3\\ &\implies K=3\\ &\implies \lvert R_4(x)\rvert\leq \frac{3\lvert x\rvert^5}{5!} \end{align}$$
>
> For $x=1$, our error is less than $\frac{3}{5!}=0.025$. This is less than $10^{-1}$. This means that the approximation is good up to the first decimal place.
>
> Further, we see that
> 
> $$R_n(x)\leq \frac{3\lvert x\rvert^{n+1}}{(n+1)!}\to 0\ \text{when}\ n\to\infty\,\forall x$$
>
>This means that given more terms in our series, our approximation will only become better.

## References

1. Wikipedia. (2023). *Taylor series*. https://en.wikipedia.org/wiki/Taylor_series
2. Weisstein, Eric W. (2023). *Maclaurin Series.* Wolfram Web MathWorld. https://mathworld.wolfram.com/MaclaurinSeries.html

{% theorem(ref="Taylor's inequality") %}
Suppose \(\lvert f^{(n+1)}(z)\rvert\le K\,\forall z\in[x_0,x]\). That is, \(K\) is the upper bound of \(f(z)\,\forall z\). Then:

\[\lvert R_n(x)\rvert\leq K\frac{\lvert x-x_0\rvert^{n+1}}{(n+1)!}\]
{% end %}

{% example(ref="Error of natural logarithm") %}
Approximate the function \(f(x)=\ln{(1+x^2)}\) with a Taylor polynomial of order 2, and estimate the maximum error when approximating \(f(x)\) by \(P_{2,0}(x)\) on the interval \(\left [0,\frac{1}{2}\right]\).

<br><br>The first derivative is:

\[ f'(x)=\frac{2x}{1+x^2} \]

The second derivative is:

\[ f''(x)=\frac{2(1-x^2)}{(1+x^2)^2} \]

Since we are approximating on an interval very close to zero, we centre our polynomial at \(x=0\).

\[ \begin{align}P_{2,0}(x)&=f(0) + f'(0)x + \frac{f''(0)}{2!}x^2\\ &= x^2 \end{align}\]

Therefore our approximations can be made with the above polynomial. Now find the error by first calculating the third derivative:

\[ f^{(3)}(x) = \frac{4x(x^2-3)}{(1+x^2)^3} \]

We want to bound this interval on \(x\in\left[0,\frac{1}2\right]\). Find the maximum value of the third derivative for all \(x\) on our interval.

<br><br>By inspection, \(f^{(3)}(x)\) is monotonically increasing. Thus its maximum value will be at \(x=\frac{1}{2}\), and we evaluate it:

\[ \begin{align}f^{(3)}\left(\frac{1}{2}\right) &\leq \left\lvert\frac{4\left(\frac{1}{2}\right)(\left(\frac{1}{2}\right)^2-3)}{(1+\left(\frac{1}{2}\right)^2)^3}\right\rvert \\&\leq \frac{11}{2} \end{align} \]
We take this as \(K\). The maximum distance from our centred point, \(\lvert x-x_0\rvert=\frac{1}{2}\). We also take that in our error bound calculation.

\[ \begin{align}\lvert R_n(x)\rvert &= K\frac{\lvert x-x_0\rvert^{n+1}}{(n+1)!}\\ &= \left(\frac{11}{2}\right)\frac{\left(\frac{1}{2}\right)^3}{3!} &= \frac{11}{96}\end{align} \]


{% end %}

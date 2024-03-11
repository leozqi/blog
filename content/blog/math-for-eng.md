+++
title="Mathematics for computer engineering"
date=2024-03-03
[taxonomies]
tags=["uwaterloo-2a"]
+++

> Mathematics is an experimental science, and definitions do not come first, but later on.
> They make themselves, when the nature of the subject has developed itself.
>
> - Oliver Heaviside

Topics to be covered:

- Calculus up to differential equations
- Signal theory
- Linear algebra
- Complex analysis, residue theorem (Needham)
- Eigenvectors, Gram-Schmidt on inner product spaces, Hilbert spaces
- Functional analysis (Kreyszig)
- Dynamics (Strogatz, Hale & Kocak)
- Statistics, and stochastic processes
- Calculus of variations and lagrange multipliers
- Perturbation theory
- Dominant balance and saddle-point/steepest descent (analytic approximation)
- Wavelets (signal processing)
- Information and coding theory (McKay, Princeton Companion to Applied Mathematics)
- Analytic approximation (Bender, orszag)


# Engineering units

{% definition(ref="Radian") %}
A unit of angle measure, defined such that one radian is the angle subtended at the centre of a circle by an arc equal in length to the radius.
{% end %}

_Dimensional analysis_ is the analysis of relationships between different physical quantities by identifying their base quantities and the units of measurement, and tracking these dimensions as calculations are performed.


# Formal power series

{% definition(ref="Formal power series") %}
A infinite sum considered independently from any notion of convergence, and that can be manipulated with the usual algebraic operations on series:

- addition
- subtraction
- multiplication
- division
- partial sums

And has terms of the form:

$$a_n x^n$$
{% end %}

_Formal power series_ can be viewed as a generalization of polynomials such that the number of terms can be infinite and with no requirement of convergence.

{% definition(ref="Generating function") %}
A representation of an infinite sequence of numbers as the coefficients of a _formal power series_.

> A generating function is a device somewhat similar to a bag.
> Instead of carrying many little objects detachedly, which could be embarrasing, we put them all in a bag, and then we have only one object to carry, the bag.
>
> George Pólya [^Pólya]
{% end %}


{% definition(ref="Improper integral") %}
A limit of a definite integral, which is written as

$$\int_a^\infty f(t)\\, dt$$

And which is equivalent to the evaluation of

$$\lim_{A\to\infty} \int_a^A f(t)\\, dt$$

given a positive real number $A$.
{% end %}

> If the integral from $a$ to $A$ exists for each $A > a$, and if the limit as $A\to\infty$ exists, then the improper integral is said to _converge_ to the limiting value.
Otherwise, the integral is said to _diverge_, or fail to exist. [^BoyceDiprima]

{% example(ref="Convergence of the improper integral") %}
Let $f(t) = e^{ct}, t\ge 0$, where $c$ is a real non-zero constant. Then

$$\begin{align*} \int_0^\infty e^{ct}\\, dt &= \lim_{A\to\infty} \int_0^A e^{ct}\\, dt = \lim_{A\to\infty} \frac{e^{ct}}c \lvert_0^A \\\\ &= \lim_{A\to\infty} \frac{1}c(e^{cA} - 1) \end{align*}$$

This integral converges to the value $\frac{-1}c$ if $c < 0$, and diverges if $c > 0$.
If $c=0$, the integrand $f(t)$ is the constant function with value 1. In this case

$$\lim_{A\to\infty} \int_0^A 1\\, dt = \lim_{A\to\infty} (A - 0) = \infty$$
{% end %}

{% definition(ref="Piecewise continuous function") %}
A function $f$, which for an interval $I\in [\alpha, \beta]$ can be partitioned by a finite number of points enclosed in $I$ such that

1. $f$ is continuous on each open subinterval
2. $f$ approaches a **finite limit** as the endpoints of each subinterval are approached from within the subinterval.

That is, if $f$ is continuous everywhere on $I$ except for a finite number of jump discontinuities.[^BoyceDiprima]
{% end %}

The integral of a _piecewise continuous function_ as defined is equal to the **sum of the integrals on the continuous subintervals**.


# The integral transform

{% definition(ref="Integral transform") %}
A relation of the form

$$F(s) = \int_\alpha^\beta K(s, t)\\, f(t)\\, dt$$

where $K(s, t)$ is the _kernel_ of the transformation, and the limits of integration $\alpha$ and $\beta$ may be infinite but must satisfy $\alpha < \beta$.
{% end %}

An integral transform takes a function of _time_ and makes it a function of another variable.

$$f(t): [0, \infty) \mapsto g(\tau): [a, \infty)$$

> An integral transform **maps** an equation from its original _function space_ ("domain") to a different space.

This is useful when the the new function is easily manipulated in terms of $\tau$ rather than $t$. 
The solution can be mapped back to the time domain using the transform's _inverse_.

A list of useful transforms:

- _Fourier transform_: given a signal, the transform maps it into the function describing the frequencies present in the signal.
- _Hilbert transform_: component of the analytic representation of a real-valued signal $u(t)$
- _Laplace transform_: converts $f(t)$ to a function of a complex variable $s$: converts differentiation and integration in the time domain into multiplication and division in the Laplace domain.
- _Poisson kernel_: solves the two-dimensional Laplace equation.
- _Weierstrass transform_: the smoothed version of $f(t)$ obtained by averaging its values, weighted with a Gaussian function centered at $t$.

Every integral transform is a _linear operator_ because the integration operation is linear.
If the kernel is allowed to be a generalized function, thena ll linear operators are integral transforms (Schwartz kernel theorem).

> To put the method of Laplace transforms into proper perspective, we consider the following hypothetical situation.
> Suppose that we want to multiply the numbers 3.163 and 16.38 together, but that we have forgotten completely how to multiply.
> We only remember how to add.
> Being good mathematicians, we ask ourselves the following question.
>
> _Question_: Is it possible to reduce the problem of multiplying the two numbers 3.163 and 16.38 together to the simpler problem of adding two numbers together?
>
> The answer to this question, of course, is yes, and is obtained as follows.
> First, we consult our logarithm tables and find that $\ln{3.163} = 1.15152094$, and $\ln{16.38} = 2.79606108$. Then, we add these two numbers together to yield $3.94758202$. Finally, we consult our anti-logarithm tables and find that $3.94758202=\ln{51.80994}$.
> Hence, we conclude that $3.163\times16.38 = 51.80994$ ...
>
> The key point in this analysis is that the operation of multiplication is replaced by the simpler operation of addition when we work with the logarithms of numbers, rather than the numbers themselves.[^Braun]


## Laplace transform

{% definition(ref="Exponential order") %}
A function $f: [0, \infty)\mapsto\mathbb{R}$ is of _exponential order_ if there are constants $k, M, a\in\mathbb{R}$, $k,M > 0$, such that

$$\lvert f(t)\rvert < ke^{at} \forall t \ge M$$

Equivalently, $f$ is of _exponential order_ if its growth may be bounded by any exponential function:

$$f\le\mathcal{O}(e^{at})$$
{% end %}

{% definition(ref="Laplace transform") %}
Let $f(t): [0, \infty) \mapsto\mathbb{R}$.
If:

1. $f$ is _piecewise continuous_ on the interval $0\le t\le A$ for any positive $A$
2. $f$ is of _exponential order_

Then the _Laplace transform_ of $f$, denoted $\mathcal{L}\\{f(t)\\}$, is given by

$$\mathcal{L}\\{f(t)\\}(s) := F(s) = \int_0^\infty e^{-st} f(t)\\, dt$$

and exists for $\text{Re}(s) > a$.
{% end %}

> $\text{Re}(s)$ is the "real part" of $s$ and form the exponential "bounds" that keep the envelope of the Laplace transform from "blowing up"

In effect, the Laplace transform maps functions in the $t$-domain to functions in the $s$-domain.
This is useful because of the additional property that

$$f'(t) = sF(s) - f(0)$$

The operation of differentiation w.r.t $t$ becomes the operation of multiplication w.r.t. $s$.
Since the solutions of linear differential equations with constant coefficients are based on the exponential function, the Laplace transform is particularly useful for such equations.

The steps are:

1. Transform an IVP for $f$ in the $t$-domain to the equivalent in the $s$-domain.
2. Solve this problem algebraically to find $\mathcal{L}\\{f\\}$.
3. Recover the desired function $f$ from its transform by "inverting the transform"


{% theorem(ref="Linearity of the Laplace transform") %}
Given $f_1, f_2$ functions defined with respect to $t$ and $F_1, F_2$ be their Laplace transforms.
Then $\forall s$ where $F_1, F_2$ defined:

$$\mathcal{L}\\{c_1f_1 + c_2f_2\\}(s) = c_1F_1(s) + c_2F_2(s)$$

for any two constants $c_1, c_2\in\mathbb{C}$.
{% end %}

{% example(ref="Deriving the Laplace transform for sine") %}
We start with Euler's identity

$$e^{iat} = \cos{at} + i\sin{at}$$

Note that we know what the Laplace transform of $e^{at}$ is:

$$\begin{align*}\mathcal{L}\\{e^{iat}\\}(s) &= \frac{1}{s-ia} \\\\ &= \mathcal{L}\\{\cos{at}\\} + i\mathcal{L}\\{\sin{at}\\} & \text{by linearity of } \mathcal{L} \end{align*}$$

Multiply $\frac{1}{s-ia}$ by the complex conjugate $s+ia$:

$$\begin{align*}\frac{1}{s-ia} &= \frac{s + ia}{(s-ia)(s+ia)} \\\\ &= \frac{s}{s^2+a^2} + i\frac{a}{s^2 + a^2}\end{align*}$$

By comparison of real and imaginary parts

$$\mathcal{L}\\{\cos{at}\\} = \frac{s}{s^2+a^2}$$

$$\mathcal{L}\\{\sin{at}\\} = \frac{a}{s^2+a^2}$$
{% end %}

How are $\mathcal{L}\\{tf(t)\\}$ and $\mathcal{L}\\{f(t)\\}$ related?

$$\begin{align*}\mathcal{L}\\{tf(t)\\} &= \int_0^\infty e^{-st} tf(t)\\, dt\\\\ &= \int_0^\infty -\frac{d}{ds}\left [ e^{-st} f(t) \right ]\\, dt\\\\ &= -\frac{d}{ds} \int_0^\infty e^{-st} f(t)\\, dt \\\\ &= -\frac{d}{ds} F(s)\end{align*}$$

More generally:

$$\mathcal{L}\\{t^n f(t)\\} = (-1)^n \frac{d^n}{ds^n} F(s)$$

Such that $$F^{(n)}(s) = \mathcal{L}\\{(-1)^n t^n f(t)\\}$$

## Table: Elementary Laplace transforms

|$f(t)$|$F(s)$|Condition|
|---|---|---|
|$1$|$\frac{1}s$|$s > 0$|
|$e^{at}$|$\frac{1}{s-a}$|$s > a$|
|$t^n, n\in\mathbb{Z}^+$|$\frac{n!}{s^{n+1}}$|$s > 0$|
|$\sin{at}$|$\frac{a}{s^2+a^2}$|$s > 0$|
|$\cos{at}$|$\frac{s}{s^2 + a^2}$|$s > 0$|
|$\sinh{at}$|$\frac{a}{s^2-a^2}$|$s>\lvert a\rvert$|
|$\cosh{at}$|$\frac{s}{s^2-a^2}$|$s>\lvert a\rvert$|


# Numerical stability

{% example(ref="Subtractive cancellation") %}
Let us compare the functions $f$ and $g$ which are equivalent.

$$f(x) = x(\sqrt{x+1} - \sqrt{x})$$

$$g(x) = \frac{x}{\sqrt{x+1} + \sqrt{x}}$$

If all our calculations have up to two decimal points, then:

$$f(500) = 500(\sqrt{501}-\sqrt{500}) = 500(22.38 - 22.36) = 500(0.02) = 10$$

$$g(500) = \frac{500}{\sqrt{501}+\sqrt{500}} = \frac{500}{22.38+22.36} = 11.17$$

The desired value was $f(500)=g(500)=11.174755\ldots$.

We see that subtractive cancellation means that $f$ is ill-conditioned while $g$ is well-conditioned.
{% end %}


# Analytic functions

Engineers focus on differential equations of physical laws.

- _Differential equation_: unknown function and its derivatives
- _Integral equation_: unknown function and its integrals
- _integro-differential_: unknown function, integrals, and its derivatives.

Our techniques involve taking $d/dx$ of integrals such that we are always solving differential equations.


# References

[^BoyceDiprima]: William E. Boyce, Richard C. DiPrima, _Elementary Differential Equations and their Applications_, 10th ed, Published 2012, [Book]

[^Braun]: Martin Braun, _Differential Equations and Their Applications_, 4th ed, Published 1993, [[Online]](https://link.springer.com/book/10.1007/978-1-4612-4360-1)

[^Pólya]: George Pólya, _Mathematics and plausible reasoning_, Published 1954, [Book]

[^Hamming]: R. W. Hamming, _Numerical Methods for Scientists and Engineers_

[^IsaacsonKeller]: Isaacson, Keller, _Analysis of Numerical Methods_

[^CheneyKincaid]: E. Ward Cheney, David R. Kincaid, _Numerical Mathematics and Computing_

[^BurdenFaires]: Burden, Faires, _Numerical Analysis_

[^AtkinsonHan]: K. Atkinson, W. Han, _Theoretical Numerical Analysis_

[^Sternberg]: Shlomo Sternberg, _Lecture 1 Newton's method_, Accessed 2024-02-13, [[Online]](https://math.harvard.edu/library/sternberg/slides/lec1.pdf)



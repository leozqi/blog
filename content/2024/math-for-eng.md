+++
title="Mathematics for computer engineering"
date=2024-03-03
[taxonomies]
tags=["the-page", "uwaterloo-2a", "featured"]
+++

> Mathematics is an experimental science, and definitions do not come first, but later on.
> They make themselves, when the nature of the subject has developed itself.
>
> - Oliver Heaviside

Engineers use math to **solve problems for people**.
This means that the engineer will often use the following steps:

1. Use _engineering units_  to encode physical information, like time,
   temperature, mass, and voltage.
2. Use _functions_ to describe the relationships and form a _model_ of a _system_.
3. Encode the information using _vectors_ and _matrices_ to solve the problem efficiently using computation.

Topics to learn:

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


# The time-varying relationship

A common model is the _time-varying_ relationship.
We relate one or many physical quantities in a system to the passing of time.

For example: the amount of water in a tank given that I am letting it out would be a time-varying relationship: the amount of water depends on the time passed from the start.

_Calculus_ and the concept of a _function_ gives us the tools to deal with such relationships.

{% definition(ref="Function") %}
A _function_, $f: A\mapsto B$, establishes a relationship between **two sets of objects**, $A$ and $B$.

Given an item $a$ that is contained in $A$, the function tells us either what the corresponding item is in $B$ or if there is no corresponding item.
{% end %}

This is the most useful definition of a function.
For the time-varying relationship, our functions look like this:

{% definition(ref="Time-varying function") %}
A time varying function, $f(t, x, y, \ldots)$ establishes a relationship between a **time** and other **varying parameters** with an set of outputs.

$$f: \begin{bmatrix} t \\\\ x \\\\ \ldots \end{bmatrix}\mapsto B$$
{% end %}

{% definition(ref="Piecewise continuous function") %}
A function $f$, which for an interval $I\in [\alpha, \beta]$ can be partitioned by a finite number of points enclosed in $I$ such that

1. $f$ is continuous on each open subinterval
2. $f$ approaches a **finite limit** as the endpoints of each subinterval are approached from within the subinterval.

That is, if $f$ is continuous everywhere on $I$ except for a finite number of jump discontinuities.[^BoyceDiprima]
{% end %}


## Heaviside step function

A _step function_ is a piecewise constant function with finitely many pieces.
Graphically, it looks like many horizontal lines covering different intervals.

{% definition(ref="Heaviside step function") %}
The _Heaviside step function_ or _unit step function_ is the piecewise function

$$u_c(t) := \left\\{ \begin{matrix} 0,\quad t < c \\\\ 1,\quad t \ge c \end{matrix} \right .$$
{% end %}

Note that any piecewise continuous function may be expressed as the sum of Heaviside step functions.
This makes it very useful for modelling time-varying relationships that may not be continuous everywhere.
The function was developed by Oliver Heaviside to represent a signal that switches on at certain time $t=c$ and stays on indefinitely.

{% example(ref="Piecewise function as the sum of Heaviside functions") %}
Woohoo
{% end %}


The Heaviside step function is used in integration to integrate piecewise continuous functions.
The Laplace transform allows the modelling of piecewise continuous functions using the Heaviside step function in the $s$-domain.


## The integral transform

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


{% theorem(ref="Nth derivative in the Laplace domain") %}
Given a function of time $f: [0, A]\mapsto\mathbb{R}$ and its derivatives
$f^{(1)}, f^{(2)}, \ldots, f^{(n-1)}$ with well-defined Laplace transforms.

Then $\mathcal{L}\\{f^{(n)}(t)\\}$ exists for $s > a$ and is given by

$$\begin{align*}\mathcal{L}\\{f^{(n)}\\}(s) = s^n\mathcal{L}\\{f(t)\\} &- s^{n-1} f(0)\\\\ &- \ldots - sf^{(n-2)}(0) \\\\ &- f^{(n-1)}(0)\end{align*}$$
{% end %}


## Impulse and the Dirac delta function

In many applications we deal with _impulsive nature_: for example, voltages or forces may act over a very short time and are very large in magnitude.
It is often enough to approximate such functions using the _Dirac delta function_.

These problems are often represented by the _homogenous differential equation_

$$ay^{(2)} + by^{(1)} + cy = g(t)$$

where the forcing function $g$ is large during a short interval of time and is otherwise zero.

The integral $I(\tau)$

$$I(\tau) = \int_{t_0-\tau}^{t_0+\tau} g(t)\\,dt$$

Equivalently for $g=0$ outside of the interval

$$I(\tau) = \int_{-\infty}^\infty g(t)\\,dt$$

Is a measure of the strength of the forcing function.
For mechanical systems this is known as the **impulse**.

Limits may be used to define the idealized unit impulse function $\delta$, which imparts an impulse one at $t=0$ but is zero for all values of $t$ other than zero.

$$\left \\{ \begin{matrix}\delta(t) = 0,\quad t\ne 0 \\\\ \\\\ \int_{-\infty}^\infty \delta(t)\\, dt = 1\end{matrix} \right .$$


{% definition(ref="Dirac delta function") %}
The _Dirac delta function_, _unit impulse_, or _$\delta$ distribution_, is a generalized function on the real numbers whose value is zero everywhere except zero and whose integral over the entire real line is equal to one.
{% end %}

The function is often manipulated as a _weak limit_ of a sequence of functions, each with a tall spike at the origin.


## Ordinary differential equations

{% definition(ref="Ordinary differential equation (ODE)") %}
Any equation expressing a relationship between time $t$, an unknown function $f(t)$, and any of $f$'s derivatives $f^{(n)}(t)$.
{% end %}

{% definition(ref="Order of an ODE") %}
The highest derivative of the function $f$ present in an ODE.
{% end %}


## Systems of ODEs

A system of ODEs is where there are $n$ equations in $t$, $n$ unknown functions $y_1(t)$ to $y_n(t)$, and at least one derivative of each of $y_k$.


# Proof by induction

> Mathematical induction proves that we can climb as high as we like on a ladder, by proving that we can climb onto the bottom rung (the **basis**) and that from each rung we can climb up to the next one (the **step**)
>
> - _Concrete Mathematics_, quoted from Wikipedia


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
The integral of a _piecewise continuous function_ as defined is equal to the **sum of the integrals on the continuous subintervals**.


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


# Numerical analysis

The study of algorithms that approximate solutions to equations within defined _error bounds_.
Contrast with _symbolic analysis_.

Seven tool model:

- Weighted averages
- Iteration
- Linear algebra
- Interpolation
- Taylor series
- Bracketing
- Intermediate-value Theorem

Approximate solutions to four categories of problems:

- Approximate derivative or integral of discrete signal
- Approximate solutions to systems of equations
- Solutions to initial-, boundary-value problems
- Unconstrained optimization problems in one or more variables


## Analytic functions

{% definition(ref="Analytic function") %}
_Analytic functions_ are functions of the form

$$\vec f: \mathbb{R}^n \mapsto \mathbb{R}^m$$

that are continuous and infinitely differentiable.

Formally, we state that $\vec f$ is _real analytic_ on the set of points $D\in\mathbb{R}^n$ if the Taylor series at any point $\vec x_0\in D$

$$\vec T(\vec x) = \sum^\infty_{n=0} \frac{f^{(n)}(\vec x_0)}{n!}(\vec x - \vec x_0)^n$$

converges pointwise to $\vec f$.
(This guarantees the above informal properties)
{% end %}

These properties are great for numerical methods of solving problems, many of which depend on the existence of the arbitrary $n$th derivative.

For physical problems, engineers often solve systems of _differential equations_.
Numerical analysis techniques almost always take the derivative of integrals to solve only differential equations.
By taking derivatives, integral and integro-differential equations are converted to pure differential equations.

We approximate a continuous and differentiable function $y$ by evaluating an approximation at specific points and interpolating values in between.
Every one of our techniques will use a step size $h$ for the density of evaluated points.

These sections above may be useful:

- [#Ordinary differential equations](#ordinary-differential-equations)

The book _Geometry for Programmers_ has a different perspective based on graphics:

> The smoothness ofa  function is a number saying how many of its derivatives are still continuous. A $C^1$ function has its first derivative continuous, a $C^2$ the second derivative, and so on.
>
> The C^1 derivative is closely related to the smoothness of a parameteric curve.
> THe C^2 smoothness is associated with its curvature.

Further, you may build piecewise curves smooth and continuous by making sure the values and derivatives of every two pieces put together coincide in the joint points.

As we will see later on, this is the intuition behind natural cubic spline interpolation


{% definition(ref="Implicit function theorem") %}
Any equation of the form

$$F(x_0, x_1, \ldots, x_n) = 0$$

can usually be written locally in the form $x_0 = f(x_1, \ldots, x_n)$.
{% end %}

The solution to a $n$th order differential equation requires $n$ constraints.
Each anti-derivative introduces one more unknown constant.

We may either describe the state of the system perfectly at one moment in time.
This may be called the initial condition as it gives the state of the system at time $t_0$.

Another approach is to describe the value fo the function at different positions.
These are called _boundary conditions_.

The give the state of the system at the boundary of $[a, b]$.

Approximate solutions to initial-value problems.


### Splines

{% definition(ref="Spline") %}
A function defined _piecewise_ using polynomials.
{% end %}

In interpolating problems, spline interpolation is often preferred.
It yields results with acceptable error bounds even with low degree polynomials, and avoids _Runge's phenomenon_ for higher degrees.

- Step function
- Linear spline: closed linear spline is a polygon
- Natural cubic spline: degree 3 with continuity $C^2$ (values and first and second derivatives are continuous) 

$$S^{(2)}(a) = S^{(2)}(b) = 0$$

for $[a, b]$.

$$S_j(x) = a_j + b_j(x - x_j) + c_j(x-x_j)^2 + d_j(x - x_j)^3$$


## Polynomial approximation

Evaluating a polynomial only requires additions.
And multiplications, which can be reduced to addition.
One of the most fundamental techniques of numerical analysis is **reducing complex functions** into polynomial functions with tolerable error.


### Vandermonde interpolation

To compute the coefficients of an interpolating polynomial for $n$ points, we may use the method of least squares.
The $n-1$ degree polynomial passing through all $n$ points is given by the matrix

Given $n$ points of form $(x_k, y_k)$, there is a polynomial of degree $n-1$ that passes through all of them as long as all $x_k$ are unique.

The coefficients of the polynomial can be found by solving a system of linear equations.
The coefficient matrix of this operation is known as the _Vandermonde matrix_ and raises the inputted $x$ coordinates to the 0th - $n-1$th powers.

$$V(x_1, x_2, \ldots, x_n) = \begin{bmatrix} x_1^{n-1} & x_1^{n-2} & \ldots & x_1 & 1 \\\\ x_2^{n-1} & x_2^{n-2} & \ldots & x_2 & 1 \\\\ \vdots & \vdots & \ddots & \vdots & \vdots \\\\ x_{n-1}^{n-1} & x_{n-1}^{n-2} & \ldots & x_{n-1} & 1 \\\\ x_n^{n-1} & x_n^{n-2} & \ldots & x_n & 1\end{bmatrix}$$

The coefficients are found by solving the below system: 

$$\begin{bmatrix}a_{n-1} \\\\ a_{n-2} \\\\ \vdots \\\\ a_1 \\\\ a_0 \end{bmatrix} V = \begin{bmatrix} y_1 \\\\ y_2 \\\\ \vdots \\\\ y_{n-1} \\\\ y_n \end{bmatrix}$$

This makes sense because the interpolating polynomial for the $n=3$ (three-point) case must pass through each of the three, such that:

- $y_1 = ax_1^2 + bx_1 + c$
- $y_2 = ax_2^2 + bx_2 + c$
- $y_3 = ax_3^2 + bx_3 + c$

{% theorem(ref="Existence and uniqueness of interpolation polynomials") %}
Given $n+1$ points $(x_i, y_i)^n_{i=0}$ with distinct $x$ values.
Then there is one and only one polynomial $p_n(x)\in\mathbb{P}_n$ satisfying the condition [^Kvaerno]

$$p_n(x_i) = y_i,\quad i\in\\{0,\ldots,n\\}$$
{% end %}

Using partial pivoting, we avoid adding a large multiple of one equation onto another.
Doing so would lose information about the second row.

Drawbacks of this approach: a polynomial of $M$ degree may have up to $M$ roots.
Every time a derivative of a function has a root, the function itself reaches an extremum point.
Therefore, the interpolating polynomial has up to $N-2$ bumps if it is $N$th order.[^Kaleniuk].
As we start to add more points, the function begins to wave more, especially towards the ends of the interpolation interval, in a phenomenon known as _Runge's phenomenon_.

{% theorem(ref="Runge's phenomenon") %}
A problem of oscillation at the edges of an interval that occurs when using polynomial (Vandermonde) interpolation with polynomials of high degree.
{% end %}

This restricts the applicability of the Vandermonde method in real-world applications.

### Horner's method

Horner's method is a numerically stable method of evaluating a polynomial.
In short, it transforms a polynomial from

$$P(x) = a_{n} x^n + a_{n-1} x^{n-1} + \ldots + a_1 x + a_0$$

to the form

$$P(x) = a_0 + x(a_1 + x(a_2 + x(a_3)))$$

(the above is for a cubic)

The method reduces the number of multiplications.



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


# Appendix A: Engineering units

{% definition(ref="Radian") %}
A unit of angle measure, defined such that one radian is the angle subtended at the centre of a circle by an arc equal in length to the radius.
{% end %}

_Dimensional analysis_ is the analysis of relationships between different physical quantities by identifying their base quantities and the units of measurement, and tracking these dimensions as calculations are performed.


# References

[^AtkinsonHan]: Atkinson, K., and Han, W. _Theoretical Numerical Analysis_, [Print]

[^CheneyKincaid]: Cheney, E. Ward, and Kincaid, David R. _Numerical Mathematics and Computing_, 7th ed., [Print]

[^BoyceDiprima]: Boyce, William E., and DiPrima, Richard C. _Elementary Differential Equations and their Applications_, 10th ed, Published 2012, [Print]

[^Braun]: Braun, Martin. _Differential Equations and Their Applications_, 4th ed, Published 1993, [[Online]](https://link.springer.com/Print/10.1007/978-1-4612-4360-1)

[^BurdenFaires]: Burden, Faires, _Numerical Analysis_

[^Hamming]: Hamming, Richard W. _Numerical Methods for Scientists and Engineers_, Published 1962, [Print]

[^IsaacsonKeller]: Isaacson, Keller, _Analysis of Numerical Methods_

[^Kaleniuk]: Kaleniuk, Oleksandr. _Geometry for Programmers_, Published 2023, [[Online]](https://www.manning.com/books/geometry-for-programmers)

[^Kvaerno]: Anne Kværnø, _Lecture notes for TMA4320 Introduction to Scientific Computation_, "Polynomial interpolation", Published 2022-02-11, [[PDF]](https://www.math.ntnu.no/emner/TMA4320/2022v/pdf/PolynomialInterpolation.pdf)

[^Pólya]: Pólya, George. _Mathematics and plausible reasoning_, Published 1954, [Print]

[^Sternberg]: Sternberg, Shlomo. _Lecture 1 Newton's method_, Accessed 2024-02-13, [[Online]](https://math.harvard.edu/library/sternberg/slides/lec1.pdf)



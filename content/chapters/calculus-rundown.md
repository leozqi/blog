+++
title="Calculus rundown"
date=2023-02-25
draft=true
+++

**tl;dr:**

> polynomial, exponential, logarithmic, trigonometric functions; inverse
> functions; limits and continuity; derivatives and rules of
> differentiation; max-min problems and mean value theorem;
> antiderivatives; Reimann definite integral; fundamental theorems of
> calculus; methods of integration; improper integrals; approximation
> using interpolation, Taylor polynomials and remainder, Newton's
> method, Landau order symbol; infinite, geometric, power series;
> multivariate functions; partial derivatives; linear approximation and
> differential; gradient and directional derivative; optimization and
> Lagrange multiplies; vector-valued functions; parametric curve,
> tangent, vector representations; line integrals and applications.

<!-- more -->

## Functions

Calculus deals with *functions*.
A function is a set of rules that assign outputs to inputs.
Every possible input must have a single defined output.
Inputs can be restricted.
The collection of possible and allowed inputs is the function's *domain*.
The collection of possible outputs is the function's *range*.

We use letters to identify functions, inputs, and outputs.
To specify a function's output for a particular input, we write the
function letter to the left of parentheses enclosing the letter
representing the input.
Letters are also used to identify *variables*, or names for values used
throughout calculation.

For example, the output of a function \\(f\\) given an arbitrary input value
named \\(x\\) would be written as:

$$f(x)$$

This could then be assigned to a variable named \\(i\\):

$$i = f(x)$$

## Limits

Functions with numerical inputs and outputs often have patterns.
A limit is what a function's output *should* be for a specific input,
based on those patterns.
What does the function output for inputs around the input value we are
testing?

* Start with an input **greater** than the value. What is the output?
* Start with an input **less** than the value. What is the output?

When inputs gets closer to the target value, do outputs approach the same value?
If they do, that is the limit of the function.
If they do not, there is **no** limit.
The limit of a function does not have to be the actual output.

Notation: suppose we define a function \\(f\\) defined in terms of \\(x\\).
The limit, \\(L\\) of \\(f\\) as inputs \\(x\\) approach \\(p\\) is written as:

$$\lim_{x \to p} f(x) = L$$

Suppose \\(L\\) is the limit of \\(f\\) at \\(p\\).
Then we can test inputs \\(x\\), each an arbitrary distance away from \\(p\\).
Each of these inputs will produce an output an *error distance* from \\(L\\).
If we can find a \\(x\\) for any error value away from \\(L\\), then
\\(L\\) must be the limit.

This is the delta-epsilon limit definition introduced by Bernard Bolzano.
Epsilon, \\(\epsilon\\), represents the error.
Delta, \\(\delta\\), represents distance.
Mathematically, we write:

$$
(\forall\epsilon > 0)
(\exists\delta > 0)
(\forall x \in \Bbb R)
(0 < \lvert x - p \rvert < \delta \implies \lvert f(x) - L \rvert < \epsilon)
$$

## Continuity

A function is *continuous* if its outputs are "connected" for ordered inputs.
Graphically, a function is continuous if its plot is an unbroken line.
A function can also be *continuous* for only parts of its domain.

Mathematically, a function is continuous for a range of inputs if:

1. The function is *defined* for each input.
2. The function has a limit that exists for each input.
3. The limit of the function is equal to the output of the function for each
   input.

## Derivatives

A derivative measures the *rate of change* of a function.
It is itself a function.
Its inputs are the same inputs of the original function.
Its outputs are the rates of change of the outputs of the original function at
each input.

Derivatives were the first branch of calculus because they modelled nature.
The input values could be the time passed.
The original function could measure distance travelled or water in a tank.
The derivative would output the speed at a certain time or water flow.
Those values are *rates of change*.
Graphically, derivatives form tangent lines to the slopes of plotted functions.

We use mathematical expressions to modify inputs of functions to get outputs.
We find the output of the derivative for a function by evaluating:

$$
L = \lim_{h \to 0} \frac{f(a + h) - f(a)}{h}
$$

\\(L\\) is the output of the derivative for the original function input \\(a\\).

We use the rules of differentiation to create equations for derivative functions
rather than evaluating them individiually.



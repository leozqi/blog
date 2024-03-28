+++
title="Numerical analysis in engineering"
date=2024-02-12
draft=true
+++

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

[^Hamming]: R. W. Hamming, _Numerical Methods for Scientists and Engineers_

[^IsaacsonKeller]: Isaacson, Keller, _Analysis of Numerical Methods_

[^CheneyKincaid]: E. Ward Cheney, David R. Kincaid, _Numerical Mathematics and Computing_

[^BurdenFaires]: Burden, Faires, _Numerical Analysis_

[^AtkinsonHan]: K. Atkinson, W. Han, _Theoretical Numerical Analysis_

[^Sternberg]: Shlomo Sternberg, _Lecture 1 Newton's method_, Accessed 2024-02-13, [[Online]](https://math.harvard.edu/library/sternberg/slides/lec1.pdf)

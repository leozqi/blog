+++
title="Big-O notation"
date=2024-02-20
draft=false
+++

Big-O notation is a symbolism used in _complexity theory_, _computer science_, and mathematics.
It describes how fast a function grows or declines.
Formally, it describes the asymptotic behaviour of functions.

> Big-O notation is also called _Landau's symbol_, from the German theoretician Edmund Landau.
> The letter $\mathcal{O}$ stands for "order," which means the rate of growth of a function.

For example, an algorithm to compute a problem of size $n$ might take $T(n)$ steps to complete.
This function might be $T(n) = 4n^2 - 2n + 2$.
However, for $n\to\infty$ note that the behaviour of $T$ is only affected by the $4n^2$ term.
Not even the coefficient has any behavioural change.
Therefore we could say that $T(n)$ grows at the _order_ of $n^2$, or

$$T(n) = \mathcal{O}(n^2)$$

# References

[^Mit16.070]: Kristina Lundqvist, _16.070 Introduction to Computers & Programming_, Published 2003, [[Online]](https://web.mit.edu/16.070/www/lecture/big_o.pdf)

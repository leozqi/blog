+++
title="7. Combinatorics"
date=2023-07-18
+++

<!-- EXAMPLE ------------------------------------------------------------->
{% example(ref="A dice-sum problem with set theory") %}
_How many ways can you roll 3 D10s to get a sum of 25?_

Let $S$ be the set of all solutions to $y_1+y_2+y_3=22$ with no restriction and for any given $i$ define $S_i$ to be the set of all solutions to $y_1+y_2+y_3=22$ such that $y_i\ge 10$.

Using the over-counting method along with the method of inclusion-exclusion, we have:

$$
\begin{align*}
N &= \lvert S\rvert - \lvert S_1\cup S_2\cup S_3\rvert \\\\
  &= \left (\binom{3}{22}\right ) - \left (\sum^3_{i=1}\lvert S_i\rvert - \sum_{i\ne j}\lvert S_i\cap S_j\rvert + \lvert S_1 \cap S_2 \cap S_3\rvert \right ) \\\\
  &= \left (\binom{3}{22}\right ) - \left ({3\choose 1}\left (\binom{3}{22-10}\right ) - {3\choose 2}\left (\binom{3}{22-2\cdot 10}\right ) + 0 \right ) \\\\
  &= 21
\end{align*}
$$
{% end %}
<!-- END EXAMPLE --------------------------------------------------------->

<!-- EXAMPLE ------------------------------------------------------------->
{% example(ref="A recursive solution to the dice-sum problem") %}
_Define a function to solve the dice-sum problem for $n$ D$N$s and a sum of $S$._

$$F(n, S, N)=\left\\{ \begin{align*} &\sum^{N}_{i=1} F(n-1,S-1, N) && n\ge 2\\\\ &1 && n=1 \land (1 \le S \le 10)\\\\ &0 && \text{else} \end{align*}\right .$$

{% end %}
<!-- END EXAMPLE --------------------------------------------------------->

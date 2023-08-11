+++
title="108.7 · Combinatorics"
date=2023-07-18
+++

## Fundamental combinatorics theorems

<!-- Counting theorem ------------------------------------------------------->
{% theorem(ref="Counting theorem") %}
The number of ways to pick a single element from each of $n$ distinct sets $A_1$,
$A_2, \ldots A_n$ is equal to

$$\lvert A_1\rvert\cdot\lvert A_2\rvert\cdot\ldots\cdot\lvert A_n\rvert$$
{% end %}
<!-- End counting theorem --------------------------------------------------->

<!-- Pigeonhole principle --------------------------------------------------->
{% theorem(ref="Pigeonhole principle") %}
Let us be given $N\in\mathbb{N}$ abstract containers and $n\in\mathbb{N}$ objects that may be contained in those containers.

Now suppose that the $n$ objects are distributed in any way among the $N$ containers.
If $n>N$, there exists at least one container with more than one object inside.
{% end %}
<!-- End pigeonhole principle ----------------------------------------------->

<!-- Factorial -------------------------------------------------------------->
{% definition(ref="Factorial function") %}
We define $n!$ recursively to be the function:

$$n! =
\begin{cases}
  1 & n=1\quad \forall n\in\mathbb{W}\\\\
  (n-1)!\\,(n) & n\ge 2
\end{cases}$$
{% end %}
<!-- End factorial ---------------------------------------------------------->

Finally, we reintroduce the principle of inclusion/exclusion for a set-based method of dealing with _overcounting_.

{% theorem(ref="Method of inclusion/exclusion") %}
Given the sets $A$ and $B$ of finite cardinality:

$$\lvert A\cup B\rvert = \lvert A\rvert + \lvert B\rvert - \lvert A\cap B\rvert$$

In general, given $n$ sets $S_1, \ldots, S_n$:

$$
\begin{align*}
\left\lvert {\Large\cup}^n_{i=1}S_i\right\rvert &= \sum^n_{i=1}\lvert S_i\rvert - \sum^n_{i\ne j}\lvert S_i\cap S_j\rvert\\\\ &+ \sum^n_{i\ne j, i\ne k, j\ne k}\lvert S_i\cap S_j \cap S_k\rvert + \ldots \\\\&+ (-1)^{n+1}\lvert S_1 \cap S_2 \cap \ldots \cap S_n \rvert\end{align*}$$ 
{% end %}

{% theorem(ref="Complementary counting") %}
For sets $A, B$, $B\subseteq A$, $\lvert B\rvert=\lvert A\rvert -\lvert\overline{B}\rvert$.
{% end %}

The counting theorem, pigeonhole principle, and factorial function allow us to develop ways to solve _ordered with replacement_, _ordered without replacement_, and _unordered without replacement_ problems. The _method of inclusion/exclusion

## Permutations

A fundamental counting problem is "how many ways can we rearrange $n$ items that are lined up in order?"
We call this type of problem an "ordered without replacement" problem.
The number of ways to rearrange $n$ items is called the number of _permutations_ of the set of the items.
We find that if we have exactly $n$ items to arrange in order, the number of ways we can do so is $n!$ ways.

Why?
Let us model this problem as if we have $n$ different-coloured marbles in a bag and must place them in order.
Well, the first marble we pick could be any one of the $n$ marbles.
But once we place it, we have only $n-1$ options to pick the second marble.
The next choice we make will only be out of $n-2$ and so on.
If we multiply each of these individual attempts to get the total number of ways we could place the marbles using the [counting theorem](./#counting-theorem), we get the definition of the factorial function!

$$n! = n(n-1)(n-2)\cdots 1$$

{% definition(ref="Permutation") %}
Given $n,m\ge 0$, $m\le n$, the $m$ out of $n$ permutation is an arrangement of exactly $m$ of the $n$ items.
The number of such arrangements is given by the equation $P$ defined as:

$$P(n,m)=\frac{n!}{(n-m)!}$$
{% end %}

Notice that in the above theorem, we generalized the permutation to: how many ways can we rearrange $m$ **out of the** $n$ items we have in order. Proof TBD.

Let us generalize the permutation concept to duplicate elements.

{% definition(ref="Generalized permutation") %}
For $i\in\set{1,2,\ldots,k}$, if there are $n_i$ indistinguishable items of type $i$, and $\sum_{i=1}^k n_i=n$, then there are:

$$\binom{n}{n_1,n_2,\ldots,n_k} = \frac{n!}{n_1! n_2! \cdots n_k!}$$

ways to rearrange them.
{% end %}

## Combinations

{% definition(ref="Combination") %}
For $n,m\ge 0$, $m\le n$, we define:

$$\binom{n}{m}=\frac{n!}{(n-m)!\\, m!} = \binom{n}{n-m,m}$$

to be the combination of $n$ and $m$, or "$n$ choose $m$."

For the cases $m\ge n$ or $m<0$, we define $\binom{n}{m}=0$.
{% end %}

## Solutions to a system of equations

{% definition(ref="Multichoose") %}
The $k$-out-of-$n$ multichoose, $\left(\\!\\!{n\choose k}\\!\\!\right)$, is defined as:

$$
\left(\\!\\!{n\choose k}\\!\\!\right) = \binom{n+k-1}{k}
$$
{% end %}

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

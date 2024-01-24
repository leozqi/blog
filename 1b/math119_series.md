+++
title="7. Sequences and series"
date=2023-08-01
+++

## Sequence

A sequence is an ordered list of numbers.

$$\set{a_n}^\infty_{n=1} = a_1, a_2, a_3, \ldots, a_n, a_{n+1}, \ldots$$

We can represent a sequence using a function with natural number inputs.
Given $f:\mathbb{N}\to\mathbb{Q}$, we have:

$$a_n = f(n)$$

We may even plot the resulting graph using ordered pairs $(n,f(n))$.

An _infinite sequence_ is a list of numbers following a certain pattern that never ends.
We may ask: "what value does this sequence get closer and closer towards, if it never ends?"
If the sequence gets closer and closer to a certain value $K$ as we get closer and closer to the infinity-ith term, we say it _converges_ and write:

$$\lim_{n\to\infty} a_n=K$$

It is often the case that a sequence gets larger and larger or smaller and smaller and does not converge to any $K$. If it increases forever, we may write

$$\lim_{n\to\infty}a_n=\infty$$

as a working value of the limit, and if it decreases forever, we may write

$$\lim_{n\to\infty}a_n=-\infty$$

To evaluate whether or not a sequence converges, it is sufficient to take the function we defined earlier, $f$, and evaluate its limit.

$$K=\lim_{n\to\infty} f(n)$$

We find that the Squeeze theorem thus also applies.

<!-- BEGIN SQUEEZE THEOREM --------------------------------------------------->
{% theorem(ref="Squeeze Theorem") %}
Given three sequences $\set{a_n}$, $\set{b_n}$, and $\set{c_n}$, if $a_n\le c_n\le b_n\forall n>N$ for some arbitrary $N\in\mathbb{N}$, then:

$$\lim_{n\to\infty} a_n = \lim_{n\to\infty} b_n = L \implies \lim_{c\to\infty} c_n = L$$

_Corollary:_ If $\lim_{n\to\infty}a_{2n}=L$ and $\lim_{n\to\infty}a_{2n+1}=L$, then:

$$\lim_{n\to\infty} a_n = L$$
{% end %}
<!-- END THEOREM ------------------------------------------------------------->

### Increasing, decreasing, monotonic, and bounded

{% definition(ref="Monotonic sequence") %}
Given any sequence $\set{a_n}$:

1. If $a_n < a_{n+1}\\, \forall n$, the sequence is _monotonically increasing_
2. If $a_n > a_{n+1}\\, \forall n$, the sequence is _monotonically decreasing_
{% end %}

{% definition(ref="Bounded sequence") %}
Given any sequence $\set{a_n}$:

1. If $\exists\\, m, m\le a_n\\, \forall n$, we say the sequence is _bounded below_ by $m$.
2. If $\exists\\, M, a_n\le M\\, \forall n$, we say the sequence is _bounded above_ by $M$.
3. If both $m$ and $M$ exist, we say the sequence is _bounded_ within $m$ and $M$.
{% end %}

These characteristics are useful for determining the convergence of sequences.

{% theorem(ref="Convergence of a bounded sequence") %}
If $\set{a_n}$ is both bounded and monotonic, it necessarily converges.
{% end %}

## Series

Now we develop the idea of adding up all of the terms of a sequence.
Often, such a sum is infinitely large, because many sequences represent numerical patterns and are infinitely long.
However, some infinitely long sequences _do_ have a sum.
We find this sum using the concept of _partial sums_.

For any sequence $\set{a_n}$, we may define another sequence formed from its incremental sums.
We call such a sequence the _sequence of partial sums_ of $\set{a_n}$.

{% definition(ref="Partial sum") %}
Any sequence $\set{a_n}$ has a defined sequence of partial sums $\set{s_n}$, where

$$s_n = \sum^n_{i=1} a_i = a_1+a_2+\ldots+a_n$$
{% end %}

By this definition, we have transformed the problem of finding the sum of an infinite sequence into _finding the limit_ of the sequence of partial sums as it approaches infinity:

$$\sum a_n = \lim_{n\to\infty} s_n$$

We call the sum of a sequence's terms a _series_ and the value of the summation above the value of the series, commonly denoted as $S$.
A sequence with infinite terms has an _infinite series_. 
Of course, a finite series will always converge.
Whether or not an infinite series converges depends on if the sequence of partial sums converges or not.

{% definition(ref="Infinite Series") %}
The sum of the infinite sequence $\set{a_n}$ is the _infinite series_

$$\sum^\infty_{i=k} a_i = \lim_{n\to\infty} s_n$$

that converges to $\lim_{n\to\infty} s_n$, the $n$th partial sum of $\set{a_n}$.
In the case the limit does not exist, we say that the infinite series _diverges_.

Note: $i$ is the _index of summation_ of the infinite series.
{% end %}

### Series addition and scalar multiplication




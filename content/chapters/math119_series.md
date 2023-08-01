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

An infinite sequence is a list of numbers following a certain pattern that never ends.
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



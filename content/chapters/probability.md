+++
title="8. Discrete probability"
date=2023-07-18
+++

An **experiment** is something we conduct that has one or more outcomes.

The set containing all outcomes of an experiment is called the **sample space**.

A problem is **discrete** if the sample space is _countable_.

An **event** is any subset of the sample space.

A set containing a single element of the sample space is called an **elementary event**. The sample space is called the **certain event**.

Two events $A$ and $B$ are mutually exclusive if $A\cap B=\emptyset$.

The empty set is called the **null event**.

A collection of events $\set{A_i\mid i\in I}$ is **pairwise mutually exclusive** if $\forall i\ne j, A_i\cap A_j\ne\emptyset$.

The probability that an event $E$ happens is the likelihood of $E$.

A fair $Dn$ is a die with $n$ sides labelled $1-n$ such that each side is equally likely to appear.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Kolmogorov axioms") %}
A discrete _probability mass function_ (PMF), $Pr$, is a function from the powerset of a countable sample space $S$ to the real numbers

$$Pr:\mathcal{P}(S)\to\mathbb{R}$$

such that the following probability axioms hold:

1. $\forall A\subset S, Pr\\{A\\} \ge 0$
2. $Pr\\{S\\}=1$
3. For all pairwise mutually-exclusive events $A_1,A_2,\ldots,A_n$:
$$Pr\\{A_1\cup A_2\cup\ldots\cup A_n\\}= Pr\\{A_1\\}+Pr\\{A_2\\}+\ldots + Pr\\{A_n\\}$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->



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
{% theorem(ref="Kolmogorov axioms (1933)") %}
A discrete _probability mass function_ (PMF), $Pr$, is a function from the powerset of a countable sample space $S$ to the real numbers

$$Pr:\mathcal{P}(S)\to\mathbb{R}$$

such that the following probability axioms hold:

1. $\forall A\subset S, Pr\\{A\\} \ge 0$
2. $Pr\\{S\\}=1$
3. For all pairwise mutually-exclusive events $A_1,A_2,\ldots,A_n$:
$$Pr\\{A_1\cup A_2\cup\ldots\cup A_n\\}= Pr\\{A_1\\}+Pr\\{A_2\\}+\ldots + Pr\\{A_n\\}$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

Note that we use $Pr\\{A\\}$ and not $Pr(A)$ because $Pr$ is formally a distribution, not a function.

Axiom 3 is often replaced with a version with a countably infinite set, which requires the convergence of series to one.

## Deriving properties of probability mass functions

{% theorem(ref="Probability based on elementary probabilities") %}
If $Pr$ is a probability mass function over any _finite_ sample space $S$, then for any $A\subseteq S$,

$$Pr\\{A\\}=\sum_{e\in A}Pr\\{\set{e}\\}$$
{% end %}

{% example(ref="Proof of probability based on elementary probabilities") %}
Let $Pr$ be a probability mass function defined on some finite sample space $S$, and let $A\subseteq S$ be given. Since $S$ is finite, $A$ is as well.

Since elementary events are mutually exclusive, $\set{e_i}\cap\set{e_j}=\emptyset\\,\forall i\ne j$.
Axiom 3 of [Kolmogorov's axioms](./#kolmogorov-axioms-1933) gives us that:

$$
\begin{align*}
Pr\set{A} &= Pr\set{\cup_{e\in A}\set{e}} && \text{by defn. of}\\ A\\\\
&= \sum_{e\in A}Pr\set{e} && \text{by Axiom 3} && \blacksquare
\end{align*}
$$
{% end %}

{% theorem(ref="Probability of nothing happening is zero") %}
If $Pr$ is a probability mass function over some sample space $S$, then $Pr\\{\emptyset\\}=0$.
{% end %}

{% example(ref="Proof of PNHWSHZ") %}
Let $S$ be some sample space and let $Pr$ be a probability mass function defined on $S$. Assume for the sake of contradiction that $Pr\\{\emptyset\\}\ge 0$. Trivially, $\emptyset\cap S=\emptyset$ and thus $S$ and $\emptyset$ are mutually exclusive. Thus:

$$
\begin{align*}
Pr\\{S\\} &= Pr\\{\emptyset\cup S\\}\\\\
&= Pr\\{\emptyset\\} + Pr\\{S\\} && \text{by Axiom 3.}\\\\
&= Pr\\{\emptyset\\} + 1 && \text{by Axiom 2.}
\end{align*}
$$

Since by assumption $Pr\\{\emptyset\\}>0$, this implies

$$1 < Pr\\{\emptyset\\} + 1$$

where $Pr\\{\emptyset\\}+1=Pr\\{S\\}$. This contradicts axiom 2.
Therefore the theorem is true.
{% end %}

{% theorem(ref="Probability of complement") %}
If $Pr$ is a probability mass function over some sample space $S$, and if $A\subseteq S$, then $Pr\set{\overline{A}}=1-Pr\set{A}$.
{% end %}

{% theorem(ref="Probability of subsets") %}
If $Pr$ is a probability mass function over some sample space $S$ and if $A,B\subseteq S$ with $A\subseteq B$, then $Pr\set{A}\le Pr\set{B}$.
{% end %}

{% theorem(ref="Restricted range of the PMF") %}
For any sample space $S$, any subset $A$ of $S$ and any PMF $Pr:\mathcal{P}\to\mathbb{R}$,

$$0\le Pr\set{A} \le 1$$

such that $\text{range}(Pr)\subseteq [0,1]$.
{% end %}

{% theorem(ref="Probability of two simultaneous events") %}
For any sample space $S$, any subsets $A$ and $B$ of $S$, and any PMF $Pr:\mathcal{P(S)}\to\mathbb{R}$

$$Pr\set{A\cup B}=Pr\set{A}+Pr\set{B}-Pr\set{A\cap B}$$
{% end %}

Triangle inequality happens for any metric. This is a metric:

{% theorem(ref="Triangle inequality for PMFs") %}
For any PMF on some finite sample space $S$ and any $A,B\subseteq S$,

$$Pr\set{A\cup B}\le Pr\set{A} + Pr\set{B}$$
{% end %}


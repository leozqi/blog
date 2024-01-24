+++
title="108.6 · Relations"
date=2023-08-02
+++

## Relations

{% definition(ref="Relation") %}
A _relation_ $R$ on the sets $A_1,A_2,\ldots A_n$ is any subset of $A_1\times A_2\times\ldots\times A_n$, $n\ge 2$.
{% end %}

A relation is a set of ordered $n$-tuples that "connects" or "relates" elements between sets.
For example, a binary relation $R\subseteq A\times B$ is a set containing ordered pairs $\langle a,b\rangle$, where each element $a\in A$ and $b\in B$.
The significance of the ordered pair is that it connects $a$ to $b$.

Although they are unintuitive, relations are a very powerful mathematical tool for characterizing relationships between distinct items.
Some relations:

|Relation|Significance|
|---|---|
|$\emptyset$|The null relation|
|$E=\set{\langle a,a\rangle\mid a\in A}$|The equality/identity relation|
|$U=A^2$|The univeral relation (everything is related to everything)|

A common pattern is a relation of a set $A$, $R\subseteq A\times A=A^2$.
This type of relation relates items in one set to other items in the same set, even including the item to itself.

## Matrix representation of relations

We can create a matrix with $I$ rows and $J$ columns to represent the relation between two sets $A$ and $B$, $\lvert A\rvert =I$ and $\lvert B\rvert=J$.

For each element $m_{ij}$ of the matrix, we assign it a one if those two elements $a_i\in A$ and $b_i\in B$ are related.
Otherwise we give it value zero.

$$M = [m_{ij}],\quad m_{ij}=\begin{cases} 1 & \langle a_i,b_i\rangle\in R\\\\ 0 & \text{otherwise} \end{cases}$$

## Reflexitivity

{% definition(ref="Reflexive") %}
A relation $R\subseteq X^2$ is _reflexive_ if:

$$\forall x\in X, \langle x,x\rangle\in R$$

$R$ is _irreflexive_ if:

$$\forall x\in X,\langle x,x\rangle\not\in R$$
{% end %}

## Symmetry

<!-- BEGIN SYMMETRY ASYMMETRY AND ANTISYMMETRY ------------------------------->
{% definition(ref="Symmetry, asymmetry, and antisymmetry") %}
A relation $R\subseteq X^2$ is _symmetric_ if:

$$\forall x,y\in X^2, \langle x,y\rangle\in R\implies \langle y,x\rangle\in R$$

$R$ is _asymmetric_ if:

$$\forall x,y\in X^2, \langle x,y\rangle\in R\implies \langle y,x\rangle\not\in R$$

$R$ is _antisymmetric_ if:

$$\forall x,y\in X^2, \langle x,y\rangle\in R\land \langle y,x\rangle\in R\implies x=y$$
{% end %}
<!-- END SYMMETRY ASYMMETRY AND ANTISYMMETRY --------------------------------->

## Transitivity

<!-- BEGIN TRANSITIVITY ------------------------------------------------------>
{% definition(ref="Transitivity") %}
A relation $R\subseteq X^2$ is _transitive_ if

$$\forall x,y,z\in X^2, \langle x,y\rangle\in R \land \langle y,z\rangle\in R\implies \langle x,z\rangle\in R$$
{% end %}
<!-- END TRANSITIVITY -------------------------------------------------------->

## Equivalence relations

An _equivalence relation_ is a relation that is _reflexive_, _symmetric_, and
_transitive_. The equality relation on the set of real numbers is an example of
an equivalence relation.

- Reflexitivity: $\forall x\in\mathbb{R}, x=x$
- Symmetry: $\forall x,y\in\mathbb{R}, x=y\iff y=x$
- Transitivity: $\forall x,y,z\in\mathbb{R}, (x=y)\land (y=z)\implies x=z$



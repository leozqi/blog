+++
title="108.8 · Discrete probability"
date=2023-07-18
+++

## Basic nomenclature

|Name|Definition|
|---|---|
|Experiment|Process with greater than one defined outcomes|
|Sample space|Set containing all the outcomes of an experiment, $S$|
|Discrete problem|Problem with a _countable_ sample space|
|Event|Any subset of the sample space|
|Null event|The empty set, $\emptyset$|
|Elementary event|An event with cardinality one|
|Certain event|The sample space itself|
|Mutually exclusive|Two events $A,B\in S, A\cap B=\emptyset$|
|Pairwise mutually exclusive|$\set{A_i\mid i\in I}$ given $\forall i\ne j, A_i\cap A_j=\emptyset$.|
|Probability of event $E$|The "likelihood" of $E$ occurring.|
|"Fair" game piece|A playing piece with outcomes all of same probability|

Note: we take $s\in S$ to not be an event, but $\set{s}\in S$ is. 

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

In plain English, the conditions are that:

1. The probability of any event must be greater-than-or-equal to zero.
2. The total probability of a sample space is one.
3. If two events have no sub-events in common, the probability of both happening is the sum of the probability of each.

Note that we use $Pr\\{A\\}$ and not $Pr(A)$ because $Pr$ is formally a distribution, not a function.
Further, Axiom 3 is often replaced with a version with a countably infinite set, which requires the convergence of series to one.

## Deriving properties of probability mass functions

{% theorem(ref="Sum of event subsets") %}
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

{% theorem(ref="Probability of the null event") %}
If $Pr$ is a probability mass function over some sample space $S$, then $Pr\\{\emptyset\\}=0$.
{% end %}

{% example(ref="Proof of the null event theorem") %}
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

## Building probability mass functions

{% theorem(ref="Bernoulli Trial") %}
A _Bernoulli trial_ is an event that has two distinct outcomes, labelled "pass" (P) and "fail" (F). The probability of the elementary event $\set{P}$ happening is normally denoted by $p$, while the probability of the elementary event $\set{F}$ is denoted by $q$.
{% end %}

{% theorem(ref="Bernoulli Distribution") %}
Let $S=\set{P,F}$. If $p$ is the probability that a Bernoulli trial passes and $X:S\to\mathbb{R}$ is an indicator random variable on $S$ defined by $X(\set{F})=0$ and $X(\set{P})=1$, then the Bernoulli distribution on $S$ an be written as:

$$Pr\set{X=x}=p^x(1-p)^{1-x}$$
{% end %}

{% example(ref="Exercise") %}
_There are 8 different CDs and 12 different books. Alice first picks up one CD or book and the Bob picks up one remaining CD and book. What is the number of possible outcomes?_

If Alice chooses a CD first, we have the number of outcomes from this case to be ${8\choose 1}{7\choose 1}{12\choose 1}=12\times 8\times 7$.

If Alice chooses a book first, we have the number of outcomes ot be ${12\choose 1}{11\choose 1}{8\choose 1}=12\times 8\times 11$.

We add the two cases and get an answer of $12\times 8\times 18=1728$.

{% end %}

{% example(ref="Exercise 1") %}
_Suppose $A,B\subseteq S$ are mutually exclusive. Prove $Pr\set{\overline{A}\cup\overline{B}}=1$._

$$
\begin{align*}
A,B\subseteq S &\implies Pr\set{A\cap B}=0\\\\
\text{By DeMorgan's Law}&\\\\
Pr\set{\overline{A}\cup\overline{B}} &= Pr\set{\overline{A\cap B}}\\\\
\text{By Theorem}&\\\\
&= 1 - Pr\set{A\cap B}\\\\
&= 1
\end{align*}
$$
{% end %}

## Practice problems

<!-- EXERCISE 1 -------------------------------------------------------------->
{% exercise() %}
> Let $Pr$ be the probability mass function on the sample space $S$.
> Let $A,B,C\subseteq S$ be events such that $Pr\set{A\mid C}\ge Pr\set{A}$ and $Pr\set{B\mid C}\ge Pr\set{B}$.
> 
> Prove that if $A$, $B$ are disjoint, then 
>
> $$Pr\set{\overline{A}\cap B\mid C}\le Pr\set{\overline{A}\cap B}$$

Using properties of the probability mass function, we find that:

$$
\begin{align*}
Pr\set{\overline{A}\cap B} &= Pr\set{A\cup\overline{B}} && \text{DeMorgan's Law}\\\\
&= Pr\set{A} + Pr\set{\overline{B}} - Pr\set{A\cap B} && \text{Theorem 9.6}\\\\
&= Pr\set{A} + (1-Pr\set{B}) - 0 && \text{Theorem 9.3, 9.2}\\\\
&= 1 + Pr\set{A} - Pr\set{B}
\end{align*}
$$

We have also that:

$$
\begin{align*}
Pr\set{\overline{A}\cap (B\mid C)} &= Pr\set{A\cup\overline{B\mid C}} && \text{DeMorgan's Law}\\\\
&= Pr\set{A} + Pr\set{\overline{B\mid C}} - Pr\set{A \cap (B\mid C)} && \text{Theorem 9.6}\\\\
&= Pr\set{A} + (1 - Pr\set{B\mid C}) - 0 && \text{Theorem 9.3, 9.2}\\\\
&= 1 + Pr\set{A} - Pr\set{B\mid C}
\end{align*}
$$

The equation now becomes:

$$
\begin{align*}
Pr\set{\overline{A}&\cap B\mid C}\le Pr\set{\overline{A}\cap B}\\\\
&\implies 1 + Pr\set{A} - Pr\set{B} \le 1 + Pr\set{A} - Pr\set{B\mid C}\\\\
\end{align*}
$$

Evidently this is true given that $Pr\set{B\mid C}\ge Pr\set{B}$. $\blacksquare$
{% end %}
<!-- END EXERCISE 1 ---------------------------------------------------------->

<!-- EXERCISE 2 -------------------------------------------------------------->
{% exercise() %}
> Prove or disprove: if we roll 2d6 then the event the first dice is odd is independent from the event the sum is 9.

Let the event that the first dice is odd be $A\subseteq S$ and let the event that the sum of the two dice is 9 be $B\subseteq S$, where $S$ is the sample space of the experiment of rolling the two dice. We prove $A$ and $B$ are independent by definition by showing that

$$Pr\set{A\cap B}=Pr\set{A}\cdot Pr\set{B}$$

$Pr\set{A\cap B}$ is the probability that both the first dice is odd and the sum of the two dice are even. There are exactly three ways for the first dice to be odd: the number of pips is 1, 3, or 5. Of these, there are only two ways to get a sum of nine: if the first dice is one, it is impossible. If the first dice is three, we may roll a 6. If the first dice is 5, we may roll a 4. Therefore the probability is:

$$Pr\set{A\cap B}=\frac{2}{6\cdot6}=\frac{1}{18}$$

Where $6\cdot 6$ is the total number of combinations we could roll the two dice by the counting theorem.

Next, we find that $Pr\set{A}=\frac{1}{2}$ of the dice being odd.

Finally, to get a sum of 9, there are four possible ways by inspection:

$$Pr\set{B}=Pr\set{(3,6), (6,3), (4,5), (5,4)}=\frac{4}{6\cdot 6}=\frac{1}{9}$$

Using the definition of independence, we verify that:

$$Pr\set{A\cap B}=Pr\set{A}\cdot Pr\set{B}\\ \because\\ \frac{1}{18}=\frac{1}{2}\cdot\frac{1}{9}$$

And therefore the two events $A$ and $B$ are independent. $\blacksquare$
{% end %}
<!-- END EXERCISE 2 ---------------------------------------------------------->

<!-- EXERCISE 3 -------------------------------------------------------------->
{% exercise() %}
> Given a standard deck of 52 cards, determine the probability that the card we drew was a face card given that we know it was a red card. You can assume the deck of cards is well mixed. 

We assume the PMF of this situation is uniform since the deck of cards is well mixed.

Let $A$ be the event of drawing a face card first try and $B$ be the event of drawing a red card first try.

Then the probability of drawing a face card after drawing a red card must be given as:

$$Pr\set{A\mid B}=\frac{Pr\set{A\cap B}}{Pr\set{B}}$$

Given our first assumption, we may state that $Pr\set{A\cap B}=\frac{6}{52}=\frac{3}{26}$ because there are 6 red face cards and 52 cards in total.

Half of the cards in the deck are red, so $Pr\set{B}=\frac{1}2$.

Calculation gives us:

$$Pr\set{A\mid B}=\frac{Pr\set{A\cap B}}{Pr\set{B}}=\frac{3}{26}\cdot\frac{2}{1}=\frac{3}{13}$$

Therefore the probability of drawing a face card given we know it was a red card is $\frac{3}{13}$
{% end %}
<!-- END EXERCISE 3 ---------------------------------------------------------->

<!-- EXERCISE 4 -------------------------------------------------------------->
{% exercise() %}
> Marmie the cat is playing a dice game with her squirrel friend Sandy. Marmie knows that Sandy cheats by including weighted dice in her dice bag! We know that exactly two of Sandy's ten D10s (sides labeled 1 to 10) are weighted and always roll 10 and that the remaining dice are fair. 
>
> If Sandy picks a random D10 out of her dice bag, rolls it five times and each roll is a 10 then what is the probability that Sandy picked one of the weighted dice? 
>
> You may assume that the dice rolls are independent.
>
> Hint: _Bayes' Theorem._

Let $A, B\subseteq S$ be the events that Sandy picks a weighted dice and the event that a fair dice rolls a 10 five consecutive times.

If Sandy picks random dice, there is a $\frac{2}{10}=\frac{1}{5}$ probability the dice is weighted since there are 10 dice in total and 2 weighted dice.
Therefore $Pr\set{A}=\frac{1}{5}$.

Given a fair D10 dice, $X\set{s}\in\set{1,2,3,\ldots,10}$ and the PMF of each roll is uniform. Therefore the chance of rolling five 10s in a roll is $Pr\set{B\mid \overline{A}}=\left (\frac{1}{10}\right )^5$.

Given an unfair D10 dice, the question states that the probability of rolling 10s is always 1. Therefore, $Pr\set{B\mid A}=1$.

Using Bayes' Theorem, we have that the probability of the dice being weighted (A) _given that_ Sandy rolled a 10 five consecutive times after selecting a dice to be:

$$
\begin{align*}
Pr\set{A\mid B}&=\frac{Pr\set{A}\cdot Pr\set{B\mid A}}{Pr\set{A}\cdot Pr\set{B\mid A} + Pr\set{\overline{A}}\cdot Pr\set{B\mid\overline{A}}}\\\\
&= \frac{0.2(1)}{(0.2)(1) + (1-0.2)(0.1^5)}\\\\
&= 0.999960002
\end{align*}
$$

Therefore the probability that Sandy picked one of the weighted dice is 0.999960002, or $\approx 99.996\\%$.
{% end %}
<!-- END EXERCISE 4 ---------------------------------------------------------->

<!-- EXERCISE 5 -------------------------------------------------------------->
{% exercise() %}
> What is the expected value of the sum of the pips if we roll 4 D6s, 800 D10s and 10 D20s? The dice mentioned about are all fair and each roll is independent.

The expected value of one d6 dice is given as:

$$E[X] = \sum^6_{i=1}\frac{i}{6} = \frac{6(6+1)}{2\cdot 6} = \frac{7}{2}$$

The expected value of a d10 is:

$$E[Y] = \sum^{10}_{i=1}\frac{i}{10} = \frac{10(10+1)}{2\cdot 10} = \frac{11}{2}$$

The expected value of a d20 is:

$$E[Z] = \sum^{20}_{i=1}\frac{i}{20} \frac{20(20+1)}{2\cdot 20} = \frac{21}{2}$$

Note that the expected value functions for random variables are linear. Since we are calculating the expected value of the sum of many dice, we can add the expected value functions we have calculated above.
Given random variables $X, Y, Z$ for the d6, d10, and d20 dice respectively, we have:

$$
\begin{align*}
E[4X + 800Y + 10Z] &= 4E[X] + 800E[Y] + 10E[Z]\\\\
&= 4\frac{7}{2} + 800\frac{11}{2} + 10\frac{21}{2} = 4519 
\end{align*}
$$

Therefore the expected value is 4519.
{% end %}
<!-- END EXERCISE 5 ---------------------------------------------------------->

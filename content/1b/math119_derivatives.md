+++
title="119.1 Derivatives"
date=2023-08-05
+++

## Newton's method

{% theorem(ref="Bolzano's Theorem (1817)") %}
Given function $f:\mathbb{R}\to\mathbb{R}$ continuous in interval $I$; if $\exists\\, a,b\in I$ where $f(a)\ge 0$ and $f(b)\le 0$, then there exists at least one root $x\in I$ such that $f(x)=0$
{% end %}

Newton's method says that given a initial guess close to a root $x_0$, we may estimate the root with the iterative function:

$$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

{% example(ref="Estimating root location with Newton's method") %}
> Given function $f(x)=2^x+x^2+x-3$, show there exists unique $a\in[0,1]$ such that $f(a)=0$.

We may use Bolzano's Theorem to show this since $f$ is continuous in interval $I=[0,1]$. Note that
$f(0)=-2$ and $f(1)=1$. Since there exists values for which $f$ are both negative and positive in $I$, there must exist at least one root of $f$ in $I$.

We may prove this root is unique by showing $f$ is increasing.
The derivative of $f$ is:

$$\frac{df}{dx}=\ln{2}(2^x)+2x+1$$

This is greater than zero $\forall\\, x\in I$ so $f$ is monotonically increasing in $I$.
Therefore $a$ must be the only root of $f$ in the interval.

> Estimate the value of $a$.

We use Newton's method with an initial guess of $x_0=1$.

$$
\begin{align*}
x_1 &= 1-\frac{1}{4.4} \approx 0.7727\\\\
x_2 &\approx 0.7517\\\\
x_3 &\approx 0.7515\\\\
x_4 &\approx 0.7515 && \text{We have reached precision 4 (same digits repeating)}
\end{align*}
$$

Therefore the estimated value of $a$ to four digits precision is 0.7515.

{% end %}

+++
title="5. Magnetostatics"
date=2023-07-17
+++

## Biot-Savart Law

Biot-Savart law relates the movement of charge at **constant velocity** to the generation of magnetic field at a point. For any point $\vec r$, we have:

$$dB = \frac{\mu_0}{4\pi}\frac{I\vec{dl}\times\hat{r}}{r^2}$$

If we substitute $dQ$ for charge and $\vec{v}$ for the charge's velocity, we get:

$$dB = \frac{\mu_0}{4\pi}\frac{dQ\vec{v}\times\hat{r}}{r^2}$$

This makes sense as current is defined as the movement of charge.

Problems making use of Biot-Savart Law often use symmetry to simplify the final integral.

{% example(ref="Spinning ring of charge") %}
_A ring with radius $R$ and uniform distributed total charge $Q$ spins in the $xy$-plane counter-clockwise about its axis of symmetry with angular speed $\omega$. Find the magnetic field on the axis of the ring a distance $z$ away from the ring's centre._

The equation we use is

$$
\begin{align*}
dB &= \frac{\mu_0}{4\pi}\frac{dQ\vec{v}\times\hat{r}}{r^2}\\\\
&= \frac{\mu_0}{4\pi}\frac{Q\vec{dl}}{2\pi R}\frac{\omega R\hat{\phi}\times\hat{r}}{r^2} && \text{Given}\ Q\text{, circumference of circle, and}\ \vec{v}=\omega r\hat{\phi}\\\\
&= \frac{\mu_0 Q \vec{dl} \omega R}{8\pi^2 R (z^2+R^2)} && \text{Given}\ r=\sqrt{z^2+R^2}
\end{align*}
$$

By inspection of components we see that only $dB_z$ remains due to symmetry. At any point in the ring, the $x$ and $y$ components cancel with the opposite point in the ring. Therefore:

$$
\begin{align*}
dB_z &= dB\sin{\theta}\\\\
&= \frac{\mu_0 Q \vec{dl} \omega R}{8\pi^2 R (z^2+R^2)} \sin\theta && \text{where}\ \sin\theta={R\over r}=\frac{R}{\sqrt{z^2+R^2}}\\\\
&= \frac{\mu_0 Q \vec{dl} \omega R}{8\pi^2(z^2+R^2)^{3/2}} && \text{where}\ \vec{dl}=rd\theta\\\\
&= \frac{\mu_0 Q \omega R}{8\pi^2(z^2+R^2)^{3/2}} rd\theta
\end{align*}
$$

Finally, integrate:

$$
\begin{align*}
B &= \int dB_z\\\\
&= \frac{\mu_0 Q \omega R}{8\pi^2(z^2+R^2)^{3/2}} \int_0^{2\pi} rd\theta\\\\
&= \frac{\mu_0 Q \omega R^2}{4\pi(z^2+R^2)^{3/2}}
\end{align*}
$$

{% end %}

{% graph(ref="Symmetry due to ring", x_label="x", y_label="y", caption="The orange $\vec{dB}$ cancels from opposite points.") %}
{vector: [-2, 2], offset: [2, 0], graphType: 'polyline', fnType: 'vector'},
{vector: [-2, 0], offset: [2, 0], graphType: 'polyline', fnType: 'vector'},
{vector: [0, 2], graphType: 'polyline', fnType: 'vector'},
{vector: [1, 1], offset: [0, 2], graphType: 'polyline', fnType: 'vector'}
{% end %}

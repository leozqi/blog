+++
title="5. Magnetostatics"
date=2023-07-17
+++

The **magnetic field** is produced by moving charge. We distinguish two scenarios and focus on the first.

1. Charge movement with constant velocity, producing a magnetic field. **(magnetostatics)**
2. Charge movement with time-varying velocity, producing an electric _and_ magnetic field related by time.

Force due to the magnetic field and electric field together is known as the **Lorentz force**.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Lorentz Law (1895)") %}
Given a charge $q$ travelling at velocity $\vec v$, the instantaneous force acting it due to the sum of electric and sum of magnetic fields at that point is given as:

$$F = q(\vec{E} + \vec{v}\times \vec{B})$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

Force due to the magnetic field is **relativistic**, unlike that of the electric field. It must be calculated using velocity relative to that of the observer.

_Comparison of electrostatic equations and magnetostatic equations:_

|Electrostatics|Magnetostatics|
|---|---|
|Stationary charge|Charge at constant velocity $\vec v$|
|Described in terms of electric field $\vec E$ measured in volt-metres|Described in terms of magnetic field $\vec B$ measured in teslas|
|Coulomb's law: $\vec{F}=q\vec{E}$|Lorentz law: $\vec{F}=q(\vec{v}\times\vec{B})$|

We find that $\vec E \perp \vec{v}\times\vec{B}$.

{% theorem(ref="Gauss's Law for Magnetism") %}

The magnetic field always has divergence equal to zero. Corollary: magnetic monopoles do not exist.

_Differential form:_

$$\nabla\cdot\vec{B}=0$$

_Integral form:_

$$\oiint_S \vec{B}\cdot d\vec{S}=0$$

{% end %}

## Biot-Savart Law

Biot-Savart law relates the movement of charge at **constant velocity** to the generation of magnetic field at a point. For any point $\vec r$, we have:

$$dB = \frac{\mu_0}{4\pi}\frac{I\vec{dl}\times\hat{r}}{r^2}$$

If we substitute $dQ$ for charge and $\vec{v}$ for the charge's velocity, we get:

$$dB = \frac{\mu_0}{4\pi}\frac{dQ\vec{v}\times\hat{r}}{r^2}$$

This makes sense as current is defined as the movement of charge.

Problems making use of Biot-Savart Law often use symmetry to simplify the final integral.

{% theorem(ref="Biot-Savart Law (1820)") %}

The contribution to $\vec B$ from any short segment of wire $\vec{dl}$ can be taken to be a vector perpendicular to the plane containing $\vec{dl}$ and $\vec r$ of the form:

$$d\vec{B} = \frac{\mu_0 I}{4\pi}\frac{d\vec{l}\times\hat{r}}{r^2}$$

Source: Purcell, E. and Morin, D. _Electricity and Magnetism_. (2013).
{% end %}

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

## Faraday's law

Electromagnetic induction is the phenomenon where a changing magnetic field around a closed circuit induces an electric curent in the circuit.
The greater the _rate of change_ in the magnetic field, the greater the electric current and voltage.

Faraday performed three experiments:

3. Moving a current-carrying wire will induce a current in the neighbouring coil.
4. If the stationary circuit had an on/off switch will also induce a current in the adjacent coil circuit.

The common element that induced a current was a changing magnetic field with respect to time.
We quantify this change with respect to _magnetic flux_ and the _electromotive force_.

### Magnetic flux

The magnetic flux quantizes the amount of magnetic field passing through a surface.

$$\Phi_B = \int \vec{B}\cdot d\vec{A}$$

The magnetic flux through a **closed surface** (surface associated with a volume) is equal to zero.
There is no "magnetic charge" or magnetic monopoles.

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Faraday's Law of Induction (1834)") %}
The electromotive force, $\epsilon$, around a closed path is equal to the negative of the time rate of change of the magnetic flux enclosed by the path.

$$\epsilon=V_\text{ind}=\oint\vec{E}\cdot d\vec{l}= -\frac{d\Phi_B}{dt}$$

Conversely, we may relate $\epsilon$ to the electric field:

$$\nabla\times E(r, t)= -\frac{\partial}{\partial t}\vec B(r,t)$$

This result is called the _Maxwell-Faraday law_ and is one of Maxwell's equations for electromagnetism.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Faraday's Law Corollary") %}
Using the fact that the magnetic force component of the [Lorentz force](./#lorentz-law-1895) is given by $\vec F_m=q(\vec v\times\vec B)=q\vec E$, we may write Faraday's Law as:

$$\epsilon=V_\text{ind}=\oint(\vec v\times\vec B)\cdot d\vec{l} = -\frac{d\Phi_B}{dt}$$
{% end %}
<!-- END THEOREM --------------------------------------------------------->

Note that this means induced voltage is related to a _change in flux_, not the flux itself.
The negative sign is from Lenz's law.
It states that the direction of induced current will be opposite to the direction of the change in magnetic flux.
This allows the result to be used immediately in the formulation of Lenz's law.

Note that Faraday's Law has three scenarios:

1. $\vec B$ is time-varying: we have induced voltage. This scenario is called the "transformer electro-motive force."
2. Circuit or $A$ is moving/time-varying: we have induced voltage. This scenario is called "motional electromotive force."
3. 

<!-- THEOREM ------------------------------------------------------------->
{% theorem(ref="Lenz's Law (1834)") %}
The current induced in a circuit due to a change in a magnetic field is directed to oppose the change in flux and to exert a mechanical force which opposes the motion.
{% end %}
<!-- END THEOREM --------------------------------------------------------->

## Self-inductance

The inductance as magnetic flux from the current itself. Induced current from current.



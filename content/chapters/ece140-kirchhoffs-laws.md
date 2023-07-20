+++
title="4. Kirchhoff's laws"
date=2023-07-19
+++

Kirchhoff's circuit laws depend on certain conditions. 
Kirchhoff's voltage law is a simplification of Faraday's law of induction, based on the assumption that there is _no fluctuating magnetic field_ within a closed circuit.
Thus $\frac{d}{dt}\Phi_m$ may be neglected.

> See: [Faraday's law of induction](../magnetostatics#faraday-s-law-of-induction-1834)

## Kirchhoff's voltage law

_Kirchhoff's voltage law_ (KVL) is based on the principle of conservation of energy.
It states that the electromotive force around a loop is equal to the sum of voltage drops in that loop.

{% theorem(ref="Kirchhoff's voltage law (1845)") %}
The algebraic sum of voltages around any closed loop is zero.

$$\sum^n_{k=1} V_i = 0$$
{% end %}

Kirchhoff's voltage law breaks down in the presence of a variable magnetic field.
Such a field could induce electric fields that affect the voltage calculated.

We know that a current $i$ will be creating the variable field and should be linearly proportional to $\Phi_m$.
The proportionality constant we call $L$, such that $\Phi_m=Li$.

Therefore we write the induced electromotive force (additional force) as:

$$V_\text{ind} = -L\frac{di}{dt}$$

The subtraction sign is a manifestation of Lenz's law.

$$L=\frac{\Phi_m}{i}=\frac{\Lambda}{i}$$

where $\Lambda=N\Phi_m$ ($N$) is the number of loops in a solenoid or inductor.



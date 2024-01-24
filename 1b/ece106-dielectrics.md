+++
title="106.8 · Dielectrics"
date=2023-08-12
+++

> ... we study how electric fields affect, and are affected by, matter. We concern ourselves with insulators, or _dielectrics_, characterized by a _dielectric constant_ ... largely the study of _dipoles_.
>
> In some cases the electric field polarizes the molecules ... in other cases a molecule has an inherent dipole moment ... In any case, a material can be described by a polarization density $P$. The electric susceptibility gives (up to a factor of $\epsilon_0) the ratio of $P$ to the electric field.
>
> The effect of the polarization density is to create a surface charge density on a dielectric material. This explains why the capacitance of a capacitor is increased when it is filled with a dielectric; the surface charges on the dielectric partially cancels the free charge on the capacitor plates.

_Insulators_ are materials where electrons are tightly bound to the atom and do not move, even within the presence of an electric field.

No materials insulate perfectly.
Most materials are _dielectrics_: they become _polarized_ when an external electric field is applied.
Although their electrons are bound, they still move over subatomic distances.
We approximate the movement by saying that within a dielectric material, _dipoles_ form.
These are groupings of positive and negative charge forced a tiny distance apart and oriented in a certain direction within the material.

A polarized dielectric will have dipoles throughout its insides.
The _polarization vector_, $\vec P$, characterizes the polarization of a dielectric.

{% definition(ref="Polarization vector") %}
Gives information on the polarization of a dielectric.

$$\vec{P} = \lim_{\Delta v\to 0}\frac{1}{\Delta v} \sum^{n\Delta v}\_{i=0}\vec{p}\_i$$

where $\vec{p}\_i = q\vec{d}$.

We construct a small volume $\Delta v$ around a particular point in the material,
then add all dipole moments vectorially within this tiny volume.
{% end %}

## Induced charges

The main mechanism of a polarized dielectric is that the material, although with a sum neutral charge, will have a charge difference between its surface and volume.

The surface charge of a dielectric is the apparent charge there, due to the polarization of the material.
It is given by

$$\rho_s = \vec{P}\cdot\hat{n}$$

The volume charge of a dielectric is the apparent charge inside and is given by

$$\rho_v = -\nabla \cdot \vec{P}$$

## Displacement vectors

Gauss's law for electric fields is affected by dielectrics, as the local electric dipole moment and polarization will displace the electric field slightly.
We define this field (the electric displacement field) as $\vec D$:

$$\vec{D} = \epsilon_0\vec{E} + \vec{P}$$

We transfer charge density to $\rho = \rho_\text{free} + \rho_v$

{% definition(ref="Permittivity of free space") %}
$\epsilon_0$
{% end %}

{% definition(ref="Relative permittivity") %}
$\epsilon_r$
{% end %}

{% theorem(ref="Gauss's Law for Dielectrics") %}
$$\oint \vec{D}\cdot d\vec{S} = Q_f$$

where $\vec{D}=\epsilon_0\epsilon_r \vec{E} = \epsilon \vec{E}$
{% end %}

Since most dielectrics are highly linear, we can assume $\vec{P}$ is proportional to $\vec{E}$.
The proportionality constant we use to relate the two is $x_e$, the _electric susceptibility factor_.

We may then define the relative permittivity of a material based on this:

$$
\begin{align}
\vec{D} &= \epsilon_0\vec{E}+\vec{P}\\\\
&= \epsilon_0\vec{E} + \epsilon_0\vec{E}x_e && \vec{P}\propto\vec{E}\\\\
&= \epsilon_0(1+x_e)\vec{E}
\end{align}
$$

{% definition(ref="Relative permittivity") %}
$$\epsilon_r = (1+x_e)$$
{% end %}

{% definition(ref="Absolute permittivity") %}
$$\epsilon = \epsilon_0\epsilon_r$$
{% end %}

## Boundary conditions

Tangential condition: $E_{1t} = E_{2t}$

Normal condition: $D_{1n} = D_{2n}$



+++
title="140.5 · AC circuits"
date=2023-08-09
+++

General form of a sinusoid:

$$A\cos{(\omega t+\theta)} \equiv A\phase{\theta}\mid_\omega$$

We may represent the sinusoids in our equation in _phasor form_ as complex
numbers in polar notation.

## Impedances

We replace the concept of _resistance_ with that of _impedance_. For every
element we define its impedance to be its ratio of voltage across to current
through:

$$Z=\frac{V}{I}$$

If voltage and current are sinuosids represented in phasor form, we simply
divide to obtain the element's impedance. Therefore impedance is a complex
number.

_Impedances of common circuit elements_

|Element|Impedance|
|---|---|
|Resistor|$Z_R = R$|
|Capacitor|$Z_C=\frac{1}{j\omega C}$|
|Inductor|$Z_L=j\omega L$|

The RMS value of a sinusoid is equal to:

$$X_\text{rms}=\frac{X_\text{peak}}{\sqrt{2}} = {A\over\sqrt{2}}$$

where $A$ is the amplitude.

## Power

Complex power

$$S = \frac{1}{2}VI^\*=V_\text{rms}I_\text{rms}^\*=P+jQ$$

where $P$ is real power and $Q$ is _reactive power_.

The power factor is the percentage of real power that is from the complex power.

If the power factor is one, then the power only consists of real power.

$$pf=\frac{P}{\lvert S\rvert}=\cos{(\theta_v - \theta_i)}$$

where $\theta_v$ is phase shift of voltage and $\theta_i$ is phase shift of
current

Apparent power is $\lvert S\rvert$


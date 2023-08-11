+++
title="140.3 · First-order RC and RL"
date=2023-08-09
+++

When analyzing first order RC and RL circuits, the first thing to do is to write them in terms of a Thevenin circuit connected to a single capacitor or inductor.

The time-step function for a first order circuit is:

$$x(t)=x(\infty)+(x(t_0)-x(\infty))e^{-\left (\frac{t-t_0}{\tau}\right )}$$

where $\tau=RC$ for an RC circuit and $\tau=\frac{R}{L}$ for an RL circuit,
where $x(\infty)$ is the steady-state voltage or current of the circuit.



+++
title="12. Propogation delays"
date=2023-07-18
+++

### Hazard states

The circuit that generates next-state variables in an asynchronous sequential circuit (ASC) must be hazard free.
A glitch can cause the circuit to enter an incorrect state and possibly become stable in that state.

In a _synchronous sequential circuit_ (SSC) the input signals must be stable within the setup and hold times of the flip-flops used.
Glitches outside those times do not matter.

Depending on the context, we do not need to consider propogation delays for pure combinational circuits without feedback.

In our previous circuit building, we assumed zero propogation delay.
In real life things are never ideal like so.

A _hazard_ is a momentary unwanted switching transient at a circuit's output.
They are also called _glitches_ and occur due to unequal propogation delays along the different paths of a combinational circuit.
Hazards can cause problems in _asynchronous sequential circuits_ (ASC) because momentary logic values that are incorrect can cause the circuit to transition to an incorrect stable state.

Hazards can be static or dynamic.

Static-1 hazard: occurs when output is one and should remain at one, but temporarily switches to zero due to a change in input.

Static-0 hazard: occurs when the output is zero and should remain at zero, but temporarily switches to 1 due to a change in input.

Dynamic hazard: occurs when an input changes and the circuit output should change from 0 to 1 or 1 to zero, but temporarily flips between values.

To avoid hazards, we may add redundant product/sum terms (depending on if it is a SOP or POS). When adjacent minterms (same row, different column; same column, different row) (no diagonal transitions) are not covered by the same product term, then a hazard exists.
We must include extra product terms in the logic expression for the output.





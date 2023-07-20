+++
title="9. State machines"
date=2023-07-17
+++

## Race conditions

A race condition occurs in an asynchronous circuit when two or more state variables change in response to a change in the circuit input value.
Unequal circuit delays may not allow multiple state variables to change simultaneously.

Assume that two state varibles change:

- If the circuit reaches the same final, stable state regardless of the order in which the state variables change, then the race is non-critical.
- If the circuit reaches a final, stable state depending on the order in which the state variables change, then the race is critical.

We must avoid critical races to create predictable circuits.

Race conditions are prevented by limiting our circuit to be a "fundamental circuit."
This condition is when the machine only has one bit change after any changes in inputs or current state varibles.

Example:

|$y_2y_1$|$w=0$|$w=1$|$z$|
|---|---|---|---|
|00|00|11|0|
|01|00|01|0|
|10|00|10|1|
|11|00|11|1|

### Hazard states

In our previous circuit building, we assumed zero propogation delay.
In real life things are never ideal like so.

A _hazard_ is a momentary unwanted switching transient at a circuit's output.
They are also called _glitches_ and occur due to unequal propogation delays along the different paths of a combinational circuit.
Hazards can cause problems in _asynchronous sequential circuits_ (ASC) because momentary logic values that are incorrect can cause the circuit to transition to an incorrect stable state.

Hazards can be static or dynamic.

Static-1 hazard: occurs when output is one and should remain at one, but temporarily switches to zero due to a change in input.

Static-0 hazard: occurs when the output is zero and should remain at zero, but temporarily switches to 1 due to a change in input.

Dynamic hazard: occurs when an input changes and the circuit output should change from 0 to 1 or 1 to zero, but temporarily flips between values.

To avoid hazards, we may add redundant product terms. When adjacent minterms are not covered by the same product term, then a hazard exists.
We must include extra product terms in the logic expression for the output.


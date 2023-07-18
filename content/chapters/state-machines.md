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

### 



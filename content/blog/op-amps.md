+++
title="Op-amps!"
date=2024-01-24
[taxonomies]
tags=["uwaterloo-2a"]
+++

Op-amps have very special properties.
They can be **closed-loop negative feedback**, **closed-loop positive feedback**, or **open-loop** configurations.

## Non-inverting negative feedback

<img src="/images/closed-loop-noninverting-amp.webp" />

## Voltage follower

A voltage follower is an op-amp circuit with a voltage gain of 1.
It is used because the high impedance of the op-amp means that very little current is drawn to produce an equivalent voltage signal as the input voltage.
They act as a "buffer" that isolates the circuit after it and limits the power draw from the input circuit.

This is also important for voltage dividers.

Voltage followers buffer a low-impedance load, such that it receives the correct amount of voltage.

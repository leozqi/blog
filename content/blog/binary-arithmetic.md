+++
title="Binary arithmetic"
date=2024-02-21
draft=true
[taxonomies]
tags=["uwaterloo-2a"]
+++

Unsigned numbers use binary, a positional number system in base-2.

{% definition(ref="Positional number system") %}
Any number system where the digit placement indicates the _weight_ of the digit.
{% end %}

Hexadecimal is another positional number system, this time in base-16.
We represent the 16 digits of hexadecimal with the characters

```
0, 1, 2, 3, 4, 5, 6, 7, 8, 9, a, b, c, d, e, f
```

Where a, b, c, d, e, and f represent the numbers $10 \times 16$, $11\times 16$, and so on.

Hexadecimal is widely used in computing because converting hexadecimal to binary can be done in two steps.

1. Represent each hexadecimal digit as a four-digit binary number.
2. Concatenate each four-digit bitstring in order of hexadecimal position.

This works because base-16 is base $2^4$.
Thus, each digit represents four binary digits but are in the same positional order.


# Terminology

The most significant _bit_ of a representation is referred to as the _msb_.
The most significant _byte_ of a representation is the _MSB_.

Similarly, the least significant bit and byte are the _lsb_ and _LSB_.

For signed integers, the _msb_ indicates the sign.


# Signed integers

There are many ways computers can represent _signed numbers_, or numbers with positive and negative sign.
The most common way is _signed two's complement_ (s2c).
In all cases, since numbers are represented in fixed-size bit representation for computers.
Overflow occurs when representation range is exceeded.

Let $y$ be the $n$-bit s2c of $-x$. Then $y = 2^n - x$ in unsigned representation.
This is equivalent to flipping the bits of $x$ and then adding one.
You could also flip all the bits after the first one from right to left.

To negate a signed number, take the two's complement of that number.

{% theorem(ref="Range of n-bit number representations") %}
Given a number representation of $n$-bits, the range to store unsigned numbers is:

$$I \in [0, 2^n - 1]$$

and the range to store signed numbers is:

$$I \in [-2^{n-1}, 2^{n-1} - 1]$$
{% end %}

# Logical shifts

Given any binary representation of data, the _left logical shift_ shifts every bit of the data to the left $N$ times and pads $N$ zeroes at the lsb.

```
lsl("01101101", 1) = "11011010"

"01101101" << 1 = "11011010"
```

The _right logical shift_ shifts every bit of the data to the right $N$ times and pads $N$ zeroes at the msb.

```
lsr("01101101", 1) = "00110110"
"01101101" >> 1 = "00110110"
```

# Arithmetic shifts

Given a

+++
title="Data structures"
date=2024-01-26
draft=true
[taxonomies]
tags=["uwaterloo-2a", "data-structures"]
+++

> Thinking of data structures using access patterns as a guide.

Selecting a practical data structure for a task always depends on your _access pattern_.
If we suppose a data structure is any generic container with $N$ access slots, then you either want to read:

1. Specific values quantified by their properties (min, max, average, etc)
2. All the values
3. A set of values

Similarily we can distinguish between different writes:

1. To specific values (largest, smallest, specific color)
2. All the values
3. A set of values

If you read/write to specific values, you will find the underlying data structure is most likely composed of linked lists.
The data is arranged such that a head/tail pointer provides easy access to the specific values to be changed.
Modification of the same is accomplished in O(1) time.

If you require random access (all the values) or much modification, then an array will form the backbone of your data structure

Data structures needing few points of access: linked list
Random access: arrays

For example, SQLITE's source B-tree implementation is optimized for bulk read/writes.

# References

{% bib(link="https://www.sqlite.org/arch.html") %}
SQLite, _Architecture of SQLite_, Accessed 2024-01-26.
{% end %}

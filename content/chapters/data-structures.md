+++
title="Data structures"
date=2023-02-26
+++

tl;dr:

> In the context of computer programming, data structures are an organized way
> of storing "stuff" in your program.
> Choosing the right data structure for your data makes your program *much*
> faster.

<!-- more -->

Every programming language has variables, which are constant names
(*identifiers*) for changing *values*.
Each variable can only store a single value of a single type.
This is because the computer sets aside enough space in *memory* to store all
possible values of that type when a variable is created.
For example, an *integer* variable will set aside enough memory to store all
integers (in a certain range).

Data structures use primitive types to store many things at a time.
They are designed with rules on how they store the data.
Using the right data structure leads to an efficiency boost.
There are different types of data structures, but the way they work under the
hood remains the same for all programming languages.

The two most important data structures are **arrays** and **linked lists**.
All other data structures are implemented using these two structures as a base.
That is because they take advantage of how the operating system keeps track of
memory.

## Arrays

When a program wants to store data, the operating system opens a *block* of
memory space and makes it available to the program.
The simplest data structure is an **array**.
An array takes this block of *contiguous*, or connected, space and divides it up
into spaces for many values of the same type.
Since computer memory is *addressed*, the program only needs to keep track of
three things:

1. Where does the block of space start?
2. What *type* of data are we storing in it?
3. How many items of that type do we have space for?

In programming languages like C, we use a *pointer* to store the address of
the first area of the memory block.
Pointers keep track of type.
A separate `int` or `size_t` variable stores the length of the array.
With these three bits of information, we can store *sequences* of data easily.

If we have an ordered list of numbers, we can make an array to store them.
In the C programming language:

```c
/* Get block of memory big enough for eight integers */
size_t size = 3;
int *numbers = malloc(sizeof(int) * size);

*(numbers) = 1
*(numbers + 1) = 2
*(numbers + 2) = 3

/* Print the second number */
printf("%d", *(numbers + 1))
```

Arrays are great for storing sequential, indexed data.
They provide instant lookup retrieval for data under a specific index.
However, resizing them after creating them means recreating a new block of memory
and moving all existing items over due to computer limitations.
That means that for constantly changing, diverse collection sizes, it is better
to use other types of data structures.
Programming languages without manual memory management often do not have arrays,
prefering instead to implement more complex data structures that are easier for
programmers to work with.

## Linked lists

Instead of storing everything in one block of memory, linked lists split up the
data.
Data is grouped into "nodes."
Each node represents one particular item in a sequence and is allocated within
one block of memory.
Each node also stores the memory addresses of other nodes *related* to it.
Usually, this is the next node in the list sequence only.

{% mermaid() %}
classDiagram
direction LR
Node1 --> Node2
class Node1 {
Node* addr
}
class Node2 {
Node* addr
}
{% end %}

Programs keep track of the first node and are thus able to go through the whole
list.


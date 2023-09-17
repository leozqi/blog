+++
title="250.1 · Abstract data types (ADT)"
date=2023-09-15
+++

Everything on a computer is described by a data structure that translates information into arrangements of digital bits.
We create _abstract data types_ (ADTs) by separating the _internal representation_ of a data structure (how it stores data), and what the data structure _does_ (its API and exposed methods).

In this way, ADTs are data types that are defined only by the operations that can be performed on them.
The details on how ADTs store and make data accessible is hidden from code that uses the type.
Code that uses ADTs

## Containers of elements

We may describe data structures that serve as containers of elements using ADTs.
There are a set of common operations that are performed on ADTs.
These operations are: [1]

- Creating a container
- Deleting a container
- Copying (shallow and deep) a container
- Splitting a container
- Taking the union of (merging) containers
- Taking the intersection (identifying common elements) of containers

Common operations on the elements inside a container include: [1]

- Getting the number of elements contained
- Adding a new object into the container
- Determining if an object is in the container (membership)
- Removing an object from the container

For example, a `list` is a common construct in many programming languages.
A list can be wholly described by its methods, the simplest which are:

- Create a list.
- Delete the list.
- Append an item to the end of the list.
- Remove the last item of the list.
- Get the size of the list.

Different implementations of the list will have different internal representations of the data, but all of them will provide the same functionality.

This graph of "the structure of abstract data structures" [1] by Prof. Douglas Harder illustrates the relationships between different ADTs well:

{% mermaid(height="200px") %}
flowchart TD;
	A[Set/Map] -->|Adjacency relation| B[Graph]
	B -->|Equivalence relation| C[Partition]
	B -->|Partial ordering| D[Directed acyclic graph]
	D -->|Hierarchical ordering| E[Tree]
	E -->|Explicit linear ordering| F[List]
	E -->|Implicit linear ordering| G[Sorted list]
	F --> H[String]
	F --> I[Deque]
	G --> J[Priority queue]
	I --> Stack
	I --> Queue
{% end %}


## Implementation

The operating system provides programs with allocated _memory_ we can use to store information.
Each block is a long ordered list of addresses to uniform "segments" of memory.
For example, the operating system may provide a program an $N$-sized "block" of 8-bit sections, each enough to store one character (`char`) type.
This operation is done with `malloc`, an operation provided by the system's standard `libc`, in a process called _dynamic memory allocation_.
The programmer accesses this block with a "pointer": a variable containing the address of the first section of that block.

```c
int *ptr = (int *) malloc(10 * sizeof(int)); /* enough memory for 10 integers */ 
```

This is an "array," or contiguous block of memory.
Code can freely iterate over the block of addresses, making sure to keep track of its size.
If the code attempts to access an address outside of the block, the operating system will prevent it from doing so and trigger an error.
This is why in lower-level languages like C, each array initialized must have both pointer (the array itself) and size kept track of.
"Node-based structures" are an extension of this. The programmer allocates several blocks of memory and must keep track of at least one address.
In tree structures, this will often be the "head" or "root" of the tree.
Then, by accessing the block of data that is the first node, they store the addresses of related nodes in the same block, allowing traversal of the entire data structure.

Of course, most code does not do this very often because it is easy to make mistakes when allocating memory this way.
They rely on automatic memory management using data structures, which abstract away the details and provide a series of methods for the programmer to insert and retrieve data.
The ultimate abstraction is the ADT, where we use a mathematical model to quantify both the abilities a data structure should have and the number of operations required for it to perform each ability.

A data structure might need to store generic objects such that they are ordered relative to one another.
If that is the only requirement, several ADTs could be considered with different pros and cons.
For example, a _linked list_ stores all elements in order.
After the selection of the appropriate data structure, there are also implementation details to consider.
A linked list can be _doubly-linked_ such that it can be traversed in both directions, or _singly-linked_.
It can store the addresses of the first element in memory, or the first and the last.
All of these details should be considered, and have been, by a language's standard library implementation.
C++ provides several implementations of the list in both doubly and singly linked form, but to the programmer, the API looks the same for both.
That is because the ADT describing both implementations is similar or even identical, and the interface for programmers seeks to abstract away implementation details.

## Sets and maps

_Sets_ and _maps_ are ADTs that describe a collection of objects with no relation to one another.

{% mermaid(height="100px") %}
classDiagram
	class A {
		data
	}
	class B {
		data
	}
{% end %}

A set is an ADT representing a collection of _unordered_, _distinct_ items.
That means each item is unique.

A _map_ is an extension of a set where each item is identified by a unique _hash_ or _key_.
The items are still not related to one another, but can be accessed programmatically using their identifiers.

{% mermaid(height="100px") %}
classDiagram
	class key_1 {
		value_1
	}
	class key_2 {
		value_2
	}
{% end %}

## Lists, stacks, and queues

The basis for these three _ordered_ ADTs is the linked list.
We define a "struct" (multiple primitive data types packed together into one sized sector) that has a pointer (or address) of the item next in the list.
By following these "next" addresses, the data structure creates an ordered relationship of consecutive data items.

{% mermaid(height="10vh") %}
flowchart LR
	A[Item 0] -->|Node *next| B[Item 1] -->|Node *next| C[NULL]
{% end %}

{% example(ref="Linked list in C") %}

We create a singly-linked list where the programmer must keep track of the
HEAD or first element of the list, and can add and remove items.

```c
struct Node {
	int data;
	Node *next;
};

Node *create_list() {
	Node *node = (Node *) malloc(sizeof(Node));
	node->next = NULL;
	return node;
}

void push(Node *head, Node *insert) {
	Node *current_item = head;
	while (current_item->next != NULL) {
		current_item = current_item->next;
	}
	current_item->next = insert;
}

void pop(Node *head) {
	Node *current_item = head;
	while (current_item->next != NULL) {
		current_item = current_item->next;
	}
	free(current_item->next); /* deallocates the memory */
	current_item->next = NULL;
}
```
{% end %}

## Trees

## Partial orders

## Partitions

## Graphs

## Vector spaces

## Bibliography

{% bib(link="https://ece.uwaterloo.ca/~dwharder/aads/") %}
D. Harder. (2023). Algorithms and Data Structures [Online].
{% end %}
{% bib(link="https://algs4.cs.princeton.edu/home/") %}
R. Sedgewick, K. Wayne, _Algorithms_, 4th ed. USA: Addison-Wesley, 2011. 
{% end %}
{% bib(link="https://web.mit.edu/6.031/www/fa17/classes/10-abstract-data-types/") %}
MIT. (2017). 6.031 — Software Construction, "Reading 10: Abstract Data Types." [Online].
{% end %}

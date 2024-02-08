+++
title="Keeping in mind data"
date=2024-01-19
draft=true
[taxonomies]
tags=["data"]
+++

From a high level, what is data?
Data refers to the **information you care about** when designing any project.
This could be profile pics, accounting figures, or experiment results.
Projects that accomplish anything will **collect**, **store**, **analyze**, and **generate** data.






Programmers represent data as patterns of "bits."
If you go deep enough down, you'll find that these patterns are arbitrary.
A specification or practice says that a particular arrangement represents _something_.

<img src="https://what-if.xkcd.com/imgs/a/34/twitter_screenshot.png" />

[_What if?_](https://what-if.xkcd.com/34/)

For example, the Unicode `utf-8` standard governs the patterns of bits to represent most (if not all) texts in the world.
Each "character" is represented by a different pattern of 0s and 1s.
A program reads the patterns of 0s and 1s and "renders" their actual representation onto the screen.

What happens when different standards collide? ASCII is another scheme for representing texts.
However, it only covers 128 characters that were all people were expected to type back then.
UTF-8 solves the problem by having the first 128 bit patterns be exactly compatible with the ASCII standard.

## Abstraction

_Abstraction_ is the separation of **interface** with **implementation**.
An **abstract data type** (ADT) is a data type that is characterized by its operations.
These are the actions that can be performed on it.

Each abstract data type has a set of well-defined operations.
These operations are of two types: to _read_ or _write_ data.
The end result is that the internal details on how ADTs store data and make data accessible are hidden from their users.

## Containers all the way down

Fundamentally, every data type is a _container_.

Different containers store different things.
However, there are a few operations we expect most containers to have.
This is the set of common operations that are performed on ADTs:

- _Creating_ a container
- _Deleting_ a container
- _Copying_ a container
- _Splitting_ a container
- _Merging_ containers

We can also perform actions on the items inside a container:

- _Identifying common items_ in two containers
- _Counting_ the number of items
- _Adding_ items
- _Finding_ an item
- _Removing_ an item

For example, a `list` is a common construct in many programming languages.
A list can be wholly described by its methods, the simplest which are:

- Create a list.
- Delete the list.
- Append an item to the end of the list.
- Remove the last item of the list.
- Get the size of the list.

Different implementations of the list will have different internal representations of the data.
However, all of them will provide the same functionality.

## Abstract data type types

ADTs can be grouped based on the types of operations they support.
They will be optimized based on _access pattern_, or how the items they contain are most often written to and read from.

This graph of "the structure of abstract data structures" [1] describes the relationships between different ADTs well:

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

## Analysis

ADTs are designed to offer performance guarantees based on the number of elements stored.
This is based on the access patterns that it was designed to support.
As a general rule of thumb, ADTs chosen to be close to a program's access patterns will perform well.

The guarantees for efficiency are expressed in **big-O notation**, which offers a worst-case guarantee of performance based on varying the number of items stored in a container.

In a basic analogy, if a container has $n$ items, big-O notation of the form $\mathcal{O}(n)$ means that operations will perform in linear time: an increase of items $C$ items will increase running time by a proportion of $C$.


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

## Queues

A _queue_ is a base data type that is a First-in First-out sequence of items.

Its primary functions are _enqueing_ items and _dequeing_ items.

Enqueueing items means placing items at the back of the line.

Dequeueing items means taking the first item at the front of the line out.

A description of the queue abstract data type:

```cpp
template <typename T>
class Queue {
public:
  void enqueue(const T & item);
  T dequeue(); //might choose to return void instead
  T & peek();
  const T & peek() const;
  int numItems() const;
};
```

## Trees

## Partial orders

## Partitions

## Graphs

## Vector spaces

* * *

[^huang]: Patrick Huang, _ECE 250 Lecture Notes_, "Abstract Data Types", Accessed 2024-01-19, [Online](https://uwaterloo.ca/scholar/z399huan/home)

{% bib(link="https://ece.uwaterloo.ca/~dwharder/aads/") %}
D. Harder. (2023). Algorithms and Data Structures [Online].
{% end %}
{% bib(link="https://algs4.cs.princeton.edu/home/") %}
R. Sedgewick, K. Wayne, _Algorithms_, 4th ed. USA: Addison-Wesley, 2011. 
{% end %}
{% bib(link="https://web.mit.edu/6.031/www/fa17/classes/10-abstract-data-types/") %}
MIT. (2017). 6.031 — Software Construction, "Reading 10: Abstract Data Types." [Online].
{% end %}
{% bib(link="https://uwaterloo.ca/scholar/z399huan/home") %}
Patrick Huang, _Abstract Data Types_, Accessed 2024-01-19.
{% end %}

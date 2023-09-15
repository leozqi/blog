+++
title="250.1 · Abstract data types (ADT)"
date=2023-09-15
+++

An "abstract data type" (ADT) is a mathematical model describing a data structure,
for which there can be multiple implementations. This note describes:

1. The allocation of memory and the (C and related languages) implementer's perspective.
2. The different ADTs used to describe relationships between objects.
3. A more detailed look on each ADT covered.

## Implementation of data structures

The operating system provides programs with allocated _memory_ we can use to store information.
Everything on a computer is described by a data structure that translates physical information into digital bit-structures.
In this context, _data structures_ describe the implementation of the digital representation of a real-world construct (pictures, the alphabet).
_Abstract data types_ quantify the behaviour of a particular type of data structure based on the relationships that data structure represents.
For the implementor, the quest is to choose a representation in memory that achieves our goals in terms of speed, ease of retrieval, and efficiency of storage.

In C-style languages, the operating system provides a way to allocate memory "blocks."
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

{% mermaid() %}
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

{% mermaid() %}
classDiagram
	class key_1 {
		value_1
	}
	class key_2 {
		value_2
	}
{% end %}

## Lists, stacks, and queues

The basis for these three _ordered_ ADTs is the linked list. We define the 

## Trees

## Partial orders

## Partitions

## Graphs

## Vector spaces

## Bibliography

1. D. Harder. (2023). Algorithms and Data Structures [Online]. Available: <https://ece.uwaterloo.ca/~dwharder/aads/>


## Data

All code should realize a _goal_.
When we store "data" (a vague word) we are representing physical constructs with digital data.
The question is how we choose the data representation in memory that achieves our goals in terms of speed, ease of retrieval, and efficiency of storage.

The computer itself knows only to allocate "blocks" of memory.
To the computer, its memory is a long list of addresses in consecutive order.
When a program runs, a portion of this memory is logically set aside for the application.
The programmer that chooses to allocate this memory may specify how large the block should be, and then is given a _pointer_, or address, to the first position of that block.
This is an "array," or contiguous block of memory.
Code can freely iterate over the block of addresses, making sure to keep track of its size.
If the code attempts to access an address outside of the block, the operating system will prevent it from doing so and trigger an error.
This is why in lower-level languages like C, each array initialized must have both pointer (the array itself) and size kept track of.

"Node-based structures" are an extension of this. The programmer allocates several blocks of memory and must keep track of at least one address.
In tree structures, this will often be the "head" or "root" of the tree.
Then, by accessing the block of data that is the first node, they store the addresses of related nodes in the same block, allowing traversal of the entire data structure.

## Objects

"Objects" and object-oriented programming languages are the natural progression of data structures.
They abstract away the methods of setting and retrieving data stored in any data structure by providing methods that relate to the actual use-case of a data structure.
We want to establish models when writing code in the form of methods that deal with our use cases, and abstract away implementation details.
This way we can develop quickly and upgrade the backend without it affecting other code we write.

## Choice of data structure

Most data structures are already implemented in the standard libraries of any language you would use.
However, in languages like C++ with non-opinionated libraries, you may still choose between data structures like "std::list", "std::vector," and "std::map."
Knowing the underlying difference in implementation of these data structures can aid the programmer in choosing the most efficient for the task, even if their methods are identical.
In the most basic level, there is a difference between _iterative_ (data structures where items have associated order) and _non-iterative_ structures.

The ADT the article mentions is a tool to evaluate the efficiency of data structures based on their method of access.
We may use big-O notation to distinguish speed of methods like insert and remove, or operations based on relationships.
We can calculate the algorithmic cost of doing any one operation and then find the structure that optimizes for our use case.

> Thus, to describe an abstract data structure we must:
>
> - Give the relationship between the objects being stored, and
> - Specify the operations which are to be optimized with respect to time and/or space.

Relationships between objects

- Linear ordering
- Hierarchical ordering
- Partial ordering
- Equivalence relationship
- Adjacency relationship

The Standard Template Library (STL) uses the concept of a strict weak ordering and therefore, this will be discussed as well.
A different relationship which may hold between objects is a metric, that is, two objects are related by the distance between the objects.
This, too, is discussed briefly together with the Abstract Space Partitioning.

In some cases, namely the linear ordering, there will be numerous abstract data structures each which will specialize by emphasizing specific operations. In a sense, these relationships and specializations form a relationship of abstract data types as is shown in Figure 1. In some cases, the abstract data structures provide further required functionality as a result of relationship, and in others, there is a specialization based on a focus on specific operations at the expense of others.

- The operations which can be performed on a container,
- General operations regarding objects stored in the container,
- How relationships may be defined either locally or globally,
- How relationships may be defined either implicitly through a function or explicitly by the programmer,
- The concept of an associate container: a key-object association where the relationship applies to the key,
- The uniqueness of objects within a container, and
- Implementations of abstract data structures in the Standard Template Library.

Operation on Containers

A data structure or container is meant to store data and while there are many operations may be specific to a particular relationship, there are some operations which can be considered to be relevant to any container class.

There are some basic operations which are performed on the containers themselves including:

- Creating a container,
- Destroying a container,
- Making a copy of a container,
- Splitting a container into two or more containers,
- Taking the union of two containers (merging the containers), and
- Taking the intersection of two containers (the common objects).

The first three operations apply to all containers.

Operations on Objects in Containers

Given a container, there are a number of operations which one may wish to perform on that container regardless of any relationship which holds between the objects, including:

- Accessing the number of objects in the container,
- Determining if the container is empty,
- Inserting a new object into the container,
- Determining if an object is in the container (membership),
- Removing an object from the container, and
- Removing all objects from (clearing) the container.

We will see that the most efficient data structure, the hash table, is only applicable only when there is no relationship of interest; however, often the container will store objects which have a relationship which we may also require information.


An implicit relation is one where the relation depends on the objects in question: the integers 3, 5, 9, 13, 27 are implicitly ordered based on their values.
The characters in the string "Hello world" are also ordered; however, their order is explicitly defined by the programmer.
Students may be implicitly partitioned based on their academic program, but an image may be partitioned first on characteristics and then those partitioned may be explicitly merged.


A relationship may be globally defined if there exists a function bool R( x, y ) which returns whether or not the two objects satisfy a relationship.
For example, integers and real numbers have a globally defined relationship.
Other relationships are locally defined in that only a few specific relations are stated and other restrictions must be deduced from those local relationships.
For example, a file system only stores local sub-directories: usr is a sub-directory of the root directory, local is a sub-directory of usr, but the file system does not record that local is a sub-directory of the root—this must be deduced by examining the local relationships.
The same holds true for the hierarchy of subclasses in Java: ThreadDeath is a subclass of Error, Error is a subclass of Throwable, and Throwable is a subclass of Object; however, it must be deduced that, for example, ThreadDeath is a subclass of both Throwable and Object.

- A simple lexical analyzer of C++ may use a stack of characters to match parentheses, brackets, and braces; and
- A string is a container which also stores characters without any association; however,
- Student records may be stored linearly based on a value such as a student identification number; and
- A parser of C++ may store information such as type (int, double, etc) and even value for constant variables in a hash table for fast reference.

As any object container, with very few modifications, can be made into an associative container, this presentation on abstract data types will not differentiate between these. The one common occasion where the name of a the object container has a different name from the corresponding associative container is the case which the objects have no relation: these are referred to as the Set ADT and the Map ADT, respectively.


Whether a container stores unique objects/keys or repeated objects/keys is again an implementation detail. For the most part, such differences do not appear in the names of the abstract data types, the only common exception being containers where the objects have no relation: the unique variants are named Set ADT and Map ADT while the containers allowing repeated objects/keys are named Multiset ADT and Multimap ADT, respectively.

The containers bitset and bit_vector are designed specifically to store bits. The container vector is based on a dynamically resizing two-ended array while list and slist are based on doubly and singly linked lists, respectively.

Note that the STL assumes a weak ordering. This is discussed more thoroughly in the topic on weak ordering together with some examples using the GNU C++ STL.


Mathematical types such as integers, real numbers, vectors, matrices, etc. are not data structures, but rather they should be treated as individual objects: a matrix describes a linear transformation and without all the entries, the matrix would only approximate the linear transformation. A matrix with another zero entry changed to a non-zero entry represents a different linear transformation. For this reason, this author is not including structures such as sparse matrices as abstract data types even though some individuals will disagree. The same data structure which may be used to store a spare matrix efficiently could also be used to store, for example, graphs or directed acyclic graphs efficiently. For more information about the representation of mathematical types, see the link mathematical types.

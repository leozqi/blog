+++
title="Computer system design"
date=2024-03-11
[taxonomies]
tags=["the-page"]
+++

This is a survey of _computer system design_.
It links ideas from "low-level" to "high-level" to show that they are really the same.
It develops a mental model for design.

Advice on developing projects:

> Resist the urge to jump straight into implementation.
> Use the API first.
> Write out a few code snippets that use the API for common use cases.
> How does it feel?
> Can the user express their intent without friction and boilerplate?
>
> Putting user needs first pays off.
>
> - Lea Verou <@leaverou@front-end.social>

> The primary benefit of TDD is not that it produces better implementations, but that it produces better APIs.
> It forces engineers to do just that, since they have to *use* the APIs they are designing to write tests.

# Performance

To evaluate the efficiency of system design we must consider _performance_.

A computer's time performance is determined by three factors:

1. _Instruction count_
2. _Clock cycle time_
3. _Clock cycles per instruction_


# From low to high level

1. Your _compiler_ will produce code eventually into assembly (machine code) interpreted directly by the processor
2. Each machine code executes with a certain _clock cycle per instruction (CPI)_.


## Instruction set architecture

> The RISC philosophy is that instruction sets are really compiler targets.
> ISAs should provide a few simple primitives to generate high-performance code.
> They should rip out complex hardware implementations to make what's left simple, uniform, and fast.[^Arpaci-Dusseau]

A processor's implementation determines the _clock cycle time_ and the number of _clock cycles per instruction (CPI)_ of all programs running on it.

When designing your system, the consideration is therefore:

1. What level of compiler optimization should I perform up to. 

In Patterson's book, LEGv8 serves as ISA.

Every ISA instruction has common steps.
The first two are identical:

1. Send the _program counter (PC)_ to memory containing the program code.
   Fetch the corresponding instruction from memory.
2. Read one or two registers.
   Select which two by using the fields (`Rn` and `Rd`) of the instruction.

The simplicity and regularity of LEGv8 makes the execution of many instruction classes similar.


## Pipelining hazards

{% definition(ref="Load hazard") %}
A special case of data hazard: a dependent instruction following a `ldr` command must stall 1 cycle, even with data forwarding.

(Loads can only forward from the `WB` stage)
{% end %}


## Paging

{% definition(ref="Paging") %}
_Paging_ is a way of partitioning memory blocks to remember **where we stored what**.

1. _Pages_, _page frames_: split up our address space into these fixed-sized units.
2. _Free list_: OS keeps track of which pages are free
3. _Page table_: Per-process data structure that maps _virtual pages_ to _physical pages_.
{% end %}

To translate virtual memory addresses to physical ones:

1. Split the virtual address into _virtual page number_ and _offset_ within the page
2. Index the page table to find which physical page the data resides in.
3. Replace VPN with physical page number and maintain the offset.

Page tables are stored in memory.
Simplest data structure used is an array _linear page table_.
OS indexes array by VPN, and looks up page-table entry at index to find desired _physical page number (PPN)_ aka _physical frame number (PFN)_.

Advantages of paging include: no external fragmentation, flexible.

To speed address translation for paging lookups, use a _translation-lookaside buffer (TLB)_.
A TLB is part of the on-chip _memory-management unit (MMU)_ and is a hardware cache of popular virtual-to-physical translations.

Upon each virtual memory reference, the hardware first checks the TLB to see if the desired translation is there.
If it is, it does it automatically without asking the page table.

```c
vpn = (virtual_address & VPN_MASK) >> SHIFT;
(success, tlb_entry) = tlb_lookup(vpn);

if (success) {
    // Use the TLB
    if (can_access(tlb_entry.protect_bits)) {
        offset = virtual_address & OFFSET_MASK;
        phys_addr = (tlb_entry.pfn << SHIFT) | offset;
        access_memory(phys_addr);
    } else {
        goto FAIL;
    }
} else {
    // Lookup the page table
    pte_addr = ptbr + (vpn * sizeof(pte));
    pte = access_memory(pte_addr);
    if (!pte.valid) {
        goto FAIL;
    } else if (!can_access(pte.protect_bits)) {
        goto FAIL;
    } else {
        tlb_insert(vpn, pte.pfn, pte.protect_bits);
        retry_instruction();
    }
}
```

1. Extract VPN from virtual address.
2. Check if TLB holds translation for VPN
    1. If yes, _TLB hit_.
       Extract PFN from TLB entry and form desired physical address.
    2. If no, _TLB miss_.
       Access page table to find translation and update TLB.
       Then retry the instruction.

The TLB, **like all caches**, is built on the premise that in the common case, translations are found in the cache.
When there is a miss, the high paging cost will lead to a noticeably slower program.
We want to avoid TLB misses as much as possible.

**Takeaways:** Since each page can hold a lot of memory, data structures that rely on the accesses memory locations near each other benefit from a speed increase due to _spatial locality_.
Elements of an array are packed tightly into pages and thus only the first access leads to TLB misses.
_Temporal locality_ refers to the quick re-referencing of memory items in time, which also leads to TLB hit rates.

> Any cache seeks to take advantage of _spatial_ and _temporal locality_ for success.
> When programs are designed to exhibit locality, TLB hit rate will be very high and efficient.

A TLB miss is handled by software most of the time:

1. Hardware raises exception for TLB miss
2. Privilege level raised to kernel mode, jumps to trap handler
3. Trap handler looks up page table translation and updates TLB

> Return-from-trap instruction for TLB misses must resume execution at instruction causing the trap (run instruction again for TLB hit)

> OS must be extra careful not to cause infinite chain of TLB misses.
> Could keep unmapped TLB miss handlers in physical memory.


## Abstract data types

When creating a model

### Map

### Directional acyclic graph

### Priority queue

### Deque

### Table

_Tables_ such as those used in database programs or implemented themselves are another data storage method.

# Design takeaways

## Make the common case fast


### Caching

Caching is used again and again to **make the common case fast**.

Hardware caches take advantage of locality in instruction and data references.
There are two types of locality:

- _temporal locality_ (close in time).
  A recently accessed instruction is likely be re-accessed soon in the future.
- _spatial locality_ (close in space).
  If a program accesses memory at $x$, it will likely soon access addresses near $x$.

Caches take advantage of locality by keeping copies of memory on small, fast on-chip memory.
Fast memory can repeatedely serve local requests.


## Abstract!

{% definition(ref="Clean architecture") %}
What I will use to describe well-abstracted systems (cf. Robert Martin).
{% end %}

It is easier to manage a system by splitting it into divided components, each of which does only one task.
Keep in mind _conceptual hierarchy_ of components and _type hierarchy_ using layered approach.
Components of the system belong to a layer and the interfaces between components and layers are well-defined.
[^Arpaci-Dusseau]
- _Entity_ (_element_): individual objects making up your system model
- _Use case_: business rules of the model, processes that happen, using domain models to work on real data.
- _Gateway_: components defining interfaces for external systems.
  Common access models to services that do not implement business rules.
  Aka API, interface, connector
- _External system_: exposed use cases via gateways used by components outside of the specific component.

Golden rule: talk inwards with simple structures and outwards through well-defined interfaces.

Example in C: a struct represents an entity for a database.
A set of use cases is provided by private functions in .c file.

The header file provides the main public interface (gateway) to use the use cases in a protected, well-defined manner.
Changes to behaviour can be specified by swapping the header file and its public interface.


A process should have clearly separated stages.

Data transformation by the use of common interfaces allows us to achieve _independence_ through abstraction.

This is the _loose coupling_ of legend.

1. Data moving from one stage to another, even if it is internal to the program, should only be through **well-defined interfaces**.
   They should be documented.


## State

State is good.
State is bad.

What is state?
_State elements_ are memory elements in your system design that affect the execution of routines.
If we pause execution of any system, we could always get it to that state by restoring all the _state elements_ and hitting play.

They, along with the _combinational logic_, completely characterize a system.
Further, if saved for a time $t$, they completely describe the present and future values of the system.

System design:

- State should be stored in as few locations as possible.
- The entirety of system state should be documented and able to be dumped, inspected.

Reduction of states: systems should be continually planned such that the abstracted number of states is few.
That is, global state between components should be almost non-existent.

## Performance via parallelism



## Performance via pipelining


## Performance via prediction


## Dependability via redundancy


# Common algorithms


# Performance



# References

[^Arpaci-Dusseau]: Remzi H. Arpaci-Dusseau, Andrea C. Arpaci-Dusseau, _Operating Systems: Three Easy Pieces_, Version 1.10, [[Online]](https://pages.cs.wisc.edu/~remzi/OSTEP/) 

[^Harder]: Douglas Wilhelm Harder, _Abstract Data Types_, Accessed 2024-03-11, [[Online]](https://ece.uwaterloo.ca/~dwharder/aads/Abstract_data_types/)

[^Patterson]: David A. Patterson, _Computer Organization and Design_, Published x, [Book]

[^Rogov]: Egor Rogov, _PostgreSQL 14 Internals_, Published 2023, [[PDF]](https://edu.postgrespro.com/postgresql_internals-14_en.pdf)

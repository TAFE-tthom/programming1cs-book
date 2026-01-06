# Internals

This segment here is a brief discussionn on some of the internals of C# and the virtual machines.

Some of these concepts may be more specific to a particular kind of implementation of the virtual machine like **CLR** or **mono** (Which was or still is used by Unity).

## Memory Regions

Memory regions is an idea that carries over how most applications, that when compiled will orgnaise memory allocations.

### What is a memory allocation

Memory allocations is a generalisation of getting a segment to store data. The regions in a **process** that are typically categorised are as follows.

* Code
* Data/Global
* Stack
* Heap

This is different from what can be encoded in an executable **program**. What can be encoded is the following.

* Code
* Data/Global
* Frame Size (relates to Stack)

This is to point a significant difference between **process** and **program**. Process is a currently running program while a program is stored on disk and will need to be turned into a program.



### Why do the memory regions matter?

They matter because it creates a model in which the kinds of data types we use and how they are associated would be typically allocated. While it is true that the VM could optimise the allocation that does not neatly fit the model, it will still need to comply with the rules that are reflective of it.

A guideline here is that:

* Variables which are initialised to static values or primitive values, can be assumed to be **stack** allocated. Any reference type that is initialised in a function would have a cost of storing the address value (pointer size, typically 8 bytes to hold the address on a 64bit system or 4bytes on 32bit). 

* Variables which are initialised to values in global memory space are assumed to be in `Data/Global` and are known at parse time. However, it reasonable to also view these as heap allocated as well.

Within C#, it is reasonable to assume that any reference type is going to be heap allocated. These are run-time allocated types and while certain pieces of data can be known ahead of time and may exist in `Data/Global`, the difference between these two regions, in terms of their address space is not significant.

* Any bytecode is typically should be considered read-only and in the **code section**. **HOWEVER**, this is mostly to think of the process memory regions in a common model, in reality, the bytecode that is interpreted can end up being re-evaluated and optimised by the virtual machine at runtime if certain **assumptions** can be held.

## Garbage Collection

The role of the garbage collector is to clean up allocations that no longer have a reference to them. If you refer to the supplementary text in the **Data Structures** chapter about **Trees**, it help with understanding the structure of the references and memory.

The virtual machine will have objects that reference other objects.

```cs
int[] numbers1 = [1, 2, 3, 4, 5];

/// other code here

numbers1 = null;
```

The above snippet is a re-assignment of `numbers1` after its initial assignment, if there are no other variables assigned to what `obj2` was assigned to an array with the numbers `1, 2, 3, 4, 5`, it will be cleaned up by the **garbage collector**. This is because there are no more references to that object.

```cs

int[] numbers1 = [1, 2, 3, 4, 5];

/// other code here

int[] obj2 = numbers1;


numbers1 = new int[5];
```

The above scenario is different, `obj2` gets assigned to the reference that contains `[1, 2, 3, 4, 5]`, this object is then assigned to `obj2` and then `numbers1` is assigned to a different object. The garbage collector will not remove like it did before because the allocation is still alive.


### Why is it important to understand garbage collection?

When writing software with C# or any language with a managed memory model, there can be side-effects that require the developer to address. In this case, issues that are triggered by the garbage collector typically show up in **realtime applications**, these being games or anything where the garbage collector can **interrupt** execution to remove old allocations.

This interruption is usually referred to as a **stop the world** interruption. The execution is paused while the garbage collector cleans up. Within a realtime application that has a certain framerate to maintain, the pause of execution can result in dropping frames, reduction in framerate or poor experience where it feels like it stutters every now and then.  

## JIT - Just In Time Compilation

A concept to understand and was mentioned in a previous chapter is the idea of compilation. With languages that leverage a compiler to construct an executable file, this compilation process translates the source code into machine code.

However, the machine code may still not resemble the CPU architecture still. This is relevant for any programming language that can target a virtual machine as its compilation target or has a virtual machine as its runtime. C# fits this case, while it does get compiled by the user, it does get compiled by the virtual machine... some times, it will re-evaluate the output as well.

When your source code is interpreted by the virtual machine, it is translated to a bytecode for its own internal virtual machine. This bytecode is then translated into machine code.

In addition, as we have discussed in the previous parts, some allocations and code can be further optimised and objects that have long lifetimes or brief lifetimes can be allocated to a particular region for the garbage collector.

C# does now include a **AOT** compiler does exist for C# and has started becoming a little more prominantly used these days.


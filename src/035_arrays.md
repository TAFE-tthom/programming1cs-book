# Arrays

As established in the **Chapter 2, Datatypes**, Arrays are a reference type, designed to store more than one value. A typical limitation programmers encounter is when they need to hold multiple values that is not known until **runtime**.

## Initialisation, Adding, Retrieving and Removing

Arrays addresses this issue where we have a collection of values that can be assigned to a single variable. In the next snippet, we can observe an array initialisation of a few numbers.

```cs
double[] amounts = [1.50, 2.75, 10.59, 8.99, 7.65];
```

We can observe a number of values given to the array. However it may not be known when writing the code. You may observe array initialisation where the array is empty.

```cs
int[] amounts = new int[5];
```

An empty array just means there are no values stored inside. However, we are able to add values to an array using a **method** called `push`.

```cs
int[] amounts = new int[5];

for(int i = 0; i < 10; i++) {
  amounts[i] = i + 1;
}
```

The snippet above demonstrates adding 10 values (and the numbers 1 to 10) to the array assigned to `amounts`. To access values within the array, you are able to use an **index**.

Lets look at how data is laidout and how indexing works with arrays.

```cs
double[] amounts = [1.50, 2.75, 10.59, 8.99, 7.65];

double v = amounts[2]; // 10.59
```

What we can observe from the above snippet.

* `amounts` has 5 numbers
* `amounts[2]` holds `10.59`
* `v` will be assigned to `10.59`

We can visualise the array like so.

| Index     |   0   |   1   |   2   |   3   |   4   |
|-----------|-------|-------|-------|-------|-------|
| **Value** | 1.50  | 2.75  | 10.59 | 8.99  | 7.65  |

Given the five values, we are able to access the first values using **index** 0.

```cs
double r = amounts[0]; // 1.50
```

Within C# you cannot remove elements from an array but you can set them to 0 or a more relevant value.


## Index Calculation

**What is behind the retrieval of the value?**

The way indexing works and why arrays are part of **reference** types is that the assigned value to `amounts` is the address that relates to where the values are stored. Each value inside is either a primitive value or another reference object.

The way the statement `amounts[0]` is evaluated, **assuming** the memory address `amounts` is assigned to is **0x1000**.

```
0x1000 + (index * sizeof object)
```

The `sizeof object` is implementation defined by the Virtual Machine, however a valid model is to assume `sizeof object` is 8. This assumption is based on size of the pointer (which would make the object a reference type) or smaller than it (which would be a primitive type).

We will observe what happens when index is 0, 1, 2 and 4.

```
0: 0x1000 + (0 * 8) = 0x1000 (first element is at the base address)
```

```
1: 0x1000 + (1 * 8) = 0x1008 (adds 8 bytes to the base address)
```
```
2: 0x1000 + (2 * 8) = 0x1010 (adds 16 bytes to the base address)
```
```
4: 0x1000 + (4 * 8) = 0x1020 (adds 32 bytes to the base address)
```

It isn't necessarily important to know exactly how or have a model in how it works but it is information that helps explain how the mechanics map to the language.

# Objects

Objects are a very broad concept in both C# and other programming languages. It is common to refer values assigned to variables as objects as it is a generalisation.

Specifically, objects usually refer to another aggregate type which is specifically composed of fields, properties and methods.

## Initialising and Indirection Objects

Within C#, we construct objects as an instance of a class. This is a matter of using the `new` keyword and calling the constructor. We will use the type `Box` to help with demonstrating this concept of indirection.

```cs
class Box {

  string label;
  Box? nestedBox = null;

  Box(string label) {
    this.label = label;
    nestedBox = null;
  }
  
}

Box obj = new Box("Empty");
```

You can update the fields of `obj` afterwards but you cannot add new fields to the object.

## Reference Types, Indirection and Aliasing

It has been discussed that both **Arrays** and **Objects** are reference types. As outlined in **Index Calcuation**, Arrays are assigned to a memory address, Objects are also assigned to a similar value or modelled as such.

> **Author's note**: It is reasonable to assume that how objects and classes are modelled are offset calculations from a base address. However, in reality, objects are implemented similarly to HashMaps.

A powerful feature with objects is that we can nest objects inside objects.

### Indirection

Let's look at a simple form of indirection using objects.

```cs
Box x = new Box("BoxX");

Box a = new Box("BoxA");

a.nestedBox = x;

```

Our challenge here is to retrieve the string `'BoxX'` without explicitly using the variable `x`, this means we want to use `a` and fields associated with `a ` to do this.

We are able to refer to the field inside `x` via `a.nestedBox.label`. This is because what we assigned to `a.nestedBox` is the object that `x` is assigned to and this grants us access to that field.

### Nesting and more indirection

This now leads into a more complex topic, **Indirection with nesting**, we are now going to be using objects as a way to nest and group data but we can also group it up quiite a bit where it has layers!

Let's examine this onion! We will redefine the `Box` constructor to help ups with crafting an absurd statement.

```cs

class Box {

  string label;
  Box? nestedBox = null;

  Box(string label, Box nestedBox) {
    this.label = label;
    this.nestedBox = nestedBox;
  }
  
}

Box onionBox = new Box("1",
  new Box("2",
    new Box("3",
      new Box("4", null))));

// To get 3

string label3 = onionBox.nestedBox.nestedBox.label;
Console.WriteLine(label3);

```

The above snipper demonstrates how we can nest objects inside other objects, we do not necessarily need to have separate variables for each layer or an array but we can actively place another object inside one.

So, a question here is how dow e get the layers from the `onion` variable?

Remember, `onion` has the fields `label` and `nestedBox`. The `label` field is simply allowing us to know what layer we are at. To get layer 2, we will need to do:

```js
onion.nestedBox
```

The above is getting layer 2 in which we can retrive the value using `.label`.

To get layer 3, we simply just use `.nestedBox` again as we can see they follow the same pattern. This is an effective use of nesting.


### Aliasing

Aliasing is an interesting concept where we can have 2 or more **references** to the same object (or allocation).

Let's look at the following:

```cs
int[] a = [1, 2, 3, 4, 5];

int[] b = a;

b[2] = 100;

Console.WriteLine(a[2]);
Console.WriteLine(b[2]); //What's the print out here?
```

Specificaly we are leaning into some particular ideas when using **reference** types where if we were to do a similar operation but on a `number` or `boolean`, this will not be observable.

In short, there is a difference between **Reference** types and **Value** types, anything that is a reference like an `object` or `array` will copy the address while value types like `int` or `boolean` will copy the value.

The outcome from the snippet above is one where we observe the output for both was `100`. This is because both `a` and `b` are mapped to the same allocation (or memory address).



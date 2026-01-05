# Variables and Values

To make our programs interesting, we need to record and hold data within our programs. To achieve this, we use **variables**. A **variable** is a symbol within our C# program that we can read and write to.

There are different keywords that can be used in combination with the variable. Within C#, we typically start by specifying the **data type** of the variable.

```cs
int number = 5;
string text = "hello!";
boolean b = true;
```

The above examples demonstrate the pattern for declaring variables. It will follow.

```
(qualifier) <data type> <symbol> = <initial value>;
```

* `qualifier` here can mean that the variable could be declared as `const`, which means it is a read only variable or `static` which will mean the lifetime of the variable exceeds that of the class and method. This is optional.

* `data type`, while not strictly necessary as you can use **implicitly-typed** variables, it is necessary when declaring variables in this fashion. You will typically use `int`, `float`, `double`, `long`, `string`, `boolean` for now. But more complex types will be used in this position.

* `symbol`, this refers to the name of the variable itself, how we are able to refer to it through out our code. Without a name, it will not be valid.

* `initial value`, while it is possible to simply declare a variable but you also want to initialise them to a value that is sensible. This value must also resemble the same datatype.

### Implicitly-Typed variables

It is possible omit  the `data type` and just have the `symbol` but we will need to prefix a `var`.

```cs
var message = "Hello World!";
```

The above is an example of a declaration of a variable but without specifying the datatype. This is deriving the datatype from the assigned value. 

## Variable naming 

We need to be mindful about how we name our variables. The name of a variable should be meaningful in the context of the problem it is trying to solve. By convention, C# leans in to `camelCase` variable naming. While you are not limited to other kinds of naming conventions, however C# will also use **CapitalCamelCase** for classes and methods.

In addition to this convention, variables must start with a non-numeric character and not use any symbols that could be confused with an **operator**.

Consider the following scenarios and what variable name would be appropriate. 🖊️

* Number of soccer balls in a garage
* Players part of Red Team
* If a light is on or off
* Blood type
* Email message

You should name our **variables** sensibly and adhere to the **naming rules** that C# outlines.

## Variable Values and Assignment 📒

When creating a variable within C#, we would commonly use the `let` or `const` keyword followed by the **name** of the symbol we want to make it. To initialise the variable to a **value**, we use the `=` **operator** to assign it to the value on the right hand side.

Example:

```cs
string message1 = "Hello";

var message2 = "Hello";
```

The above demonstrates:

* Usage of a **keyword** of `var` as well as specifying the datatype and then the symbol for `message1`.
* The name of the variable **we** gave it is `message1` and `message2`
* We have assigned it to the **value** `"Hello"` using the `=` operator.
* In reference with **operators**, a **binary** operator has two **operands**
    a **left** and **right** operand, with `=`, the variable name and `"Hello"`
    are the operands.

We are then able to refer to the variable in lines that follow afterwards.


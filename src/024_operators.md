# Operators and Expressions

We have observed some basic operators in use. The most common kind of operator you will encounter are **binary operators**. However, there are two other kinds of operators you will use.

* **Unary operator**
* **Ternery operator**

The logic behind each one is that they are referring to the number of elements they are operting on. For a **unary** operator, it is needing one variable.

A common unary operator is `!`, which is applied to get the opposite result of a boolean expression.

Example:

```cs
bool r = !true; //Will be false

int i = 10;

i++;
```

In the snippet above, you will observe the `++` unary operator that will increment the value by 1 (i being changed from 10 to 11).

**Binary** operators will use the element on the *left* and the element on the *right*. This is common as most operators we use will be of this form. However, depending on the data type, they take on different behaviours.

Example:

```cs
int y = 10 + 20;

int z = y * 2;
```

The above snippet demonstrates `+` addition operator for numbers and `*` multiplication operator. Both work on the left and right operands.

The above 

**Ternary** operators will appear in a particular instance where they use the `?` and `:` symbols together.

Example:

```cs
int mark = 61;

int result = mark >= 50 ? "Pass" : "Failed";
```

The above snippet will evaluate if `mark` is greater than or equal to `50` and assign the value `"Pass"` or `"Failed"`.

## Datatypes changing operator behaviour 📒

Depending if the variables are strings or numbers will change what kind of operation we will get and if it is even supported.

Using the code snipept below:

```cs
var numberX = 10; // Number
var numberY = 20.5; // Number
var stringX = "Ten"; // String
var stringY = 'Twenty'; // String
var booleanX = true;
var booleanY = false; //boolean is only: true or false

//number + number = number
Console.WriteLine(numberX + numberY);

//number + string = string
Console.WriteLine(numberX + stringY);

//string + number = string
Console.WriteLine(stringX + numberY);

//string + string = string
Console.WriteLine(stringX + stringY);

//boolean + boolean = number?
Console.WriteLine(booleanX + booleanY);

//boolean || boolean = boolean (logical or)
Console.WriteLine(booleanX || booleanY);

//boolean && boolean = boolean (logical and)
Console.WriteLine(booleanX && booleanY);

//!boolean = boolean (logical not)
Console.WriteLine(!booleanX);
```

We can observe how `number + number` will result in a number, but will be addition.

But `number + string` or `string + number` or `string + string` will result in a `string` and will be string concatentation.

## Common Operators and Expressions 📒

The follow below in which you can use the reference from MDN (Mozilla Developer Network), you will get a breakdown of some common operators and expressions (and literals).

* `+` - If the type associated is a `number`, it will perform addition, if it is a `string`, it will perform concatenation

* `-` - When type `number`, it will perform `subtraction`

* `/` - When type `number`, it will perform `division`

* `*` - When type `number`, it will perform `multiplication`

* `"..."` or `'...'` - `'` and `"` pairs are used to indicate start and end point of a `string` literal

* `true` and `false` - boolean literals, commonly used with if statements to allow your program to make decisions

* `<` - Less than symbol, example: `5 < 10` would return `true`
* `>` - Greater than symbol, example: `10 > 5` would return `true`
* `>=` - Greater than or equal to symbol
* `<=` - Less than or equal to symbol
* `==` and `===` - Equality symbol, checks to see if two objects are the same, additional equal is ensuring type equality

* `!=` and `!==` - Inequality symbol, checks to see if two objects are not the same.

## Printing and Interpreting data

Within C#, we will want to print data to standard output and interpret strings into integers and floats. C# provides the capabilities with the following functions:

* `Console.WriteLine` - Allows you to print to standard output (terminal screen), `Console.WriteLine("Hello!")` as an example.

* `int.Parse` - Will attempt to convert a `string` to an `int`, this will convert to the type `int`.

* `float.Parse` - Will attempt to convert a `string` to a `float`, this will convert to the type `Number`.


Notice that there are two different ways to interpret the string and translate it to a number. Consider what the difference between an `int` and a `float`. 📒

**Note:** Write an experiment and use the following text: 🖊️ 💻

  * `"2"`
  * `"2.5"`
  * `"2.33"`
  * `"1.99"`
  * `"5.0"`

Consider what the behaviour is between the two and what **number sets** they relate to.


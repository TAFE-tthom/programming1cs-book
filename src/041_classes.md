# Classes Structure

Within C#, defining a class is also defining a type. This acts as template for objects that are instantiated as this type. Given that more than 1 object can be instantiated as this type, we are able to gaurantee certain behaivours and fields from that object.

It is easy to view a class as a **template** or **blueprint**. Objects instantiated as that type adhere to that blueprint. This is a very useful concept when structure your data within C#.


## Class Anatomy

A class can range from being a fairly complex description or simple, it depends on the scenario it is being used. Similar with objects and other constructs, we are able to compose a class with other classes, objects and types.


## Constructing our own

You have already interacted with classes before through `Array` and other builtins such as `int` and `string`. What has not be shown is that part of instantiating an object from that type is done using the `new` keyword.

Let's look into the different components, while this isn't all the components, it is outlining the most critical ones.

```cs
class ClassName {

  datatype instanceField; //Field just not initialised,
  // needs to be in the constructor or default value is given

  datatype initialisedField = "Hello!"; //Field but is initialised with a string value

  static datatype staticField; //Field but for the class, not initialised,
  // will be set to default
  
  static datatype staticInitialisedField = "And again!"; //Field but for the class, initialised

  ClassName() { } // Optional, when omitted, a constructor exist just with no params

  ReturnType AMethod() { //Similar to a function but operations on the object
    //Can have a return statement or not
  }

  static ReturnType AStaticMethod() { // Method that is associated with the class but not object
    //Similar to a function and method, can have a return statement
  }
  
}
```

Something to note is that `field` specifiers do not **need** to exist in class scope, they can be created and assigned during execution of the constructor.

### Field Initialisation

We will construct our own class and focus on the field variations that can be utilised. The following is an example a `Cupcake` class.

```cs
class Cupcake {
  bool delicious = false;
  string name = 'Chocolate Cupcake';
}

Cupcake cupcake1 = new Cupcake();

Console.WriteLine(cupcake1.name);
Console.WriteLine(cupcake1.delicious);
```

The above snipet defines a class with two instance fields, we then print out the values. Since the fields are assigned already, we get the output.

```
Chocolate Cupcake
true
```

However, it may seem quite redundant to have a whole concept that doesn't differentiate itself from objects that much. Lets consider how we could parameterise the fields themselves, we can do this through a **constructor**.

```cs
class Cupcake {
  bool delicious;
  string name;

  Cupcake(string name, bool delicious) {
    this.name = name;
    this.delicious = delcious;
  }
}

Cupcake cupcake1 = new Cupcake("Chocolate Cupcake", true);

Console.WriteLine(cupcake1.name);
Console.WriteLine(cupcake1.delicious);
```

We have been able to observe that we can parameterise what the field will be, similar to a **function**.

**What about the `this`** keyword?

The `this` keyword has a lot of utility within javascript and within the context above it is both addressing the ambiguity and also referring to the current reference.

> Note: As outlined in the previous chapter regarding **memory addresses**, you can consider `this` as the memory address of the current object executing the method.

We will be exploring the `this` keyword in more depth later on.

### Methods

To examine a method, you will likely not see too much of a difference between a function and method.

```
// Assume inside class scope

  ReturnType TheMethod(parameter) {

    // If not void, it needs to return a value
  }
```

Let's say we want to have some function to serve the purpose of printing out the name the cupcake and if it is delicious or not. This is where **methods** can be effectively be utilised.

```cs
class Cupcake {

  bool delicious;
  string name;
  
  Cupcake(name, delicious) {
    this.name = name;
    this.delicious = delcious;
  }

  void PrintDetails() {
    Console.WriteLine(cupcake1.name);
    Console.WriteLine(cupcake1.delicious);
  }
}

// Usage in another method

Cupcake cupcake1 = new Cupcake("Chocolate Cupcake", true);
cupcake1.PrintDetails();
```

We can observe that the output logic has been incorporated into the `Cupcake` class. We can refer to it by using `PrintDetails`.



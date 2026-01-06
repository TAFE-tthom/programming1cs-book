# Properties and Encapsulation

We will be outlining two common constructs within C#, Properties can be considered a bit of an inbetween fields and methods. It will look like a field but can have a method behind it or it can have the same kind of complexity as a method.

Encapsulation will govern how the fields, methods and properties are accessed. We are able to dictate what other classes can utilise them. It acts a mechanism to restrict usage or open it where appropriate.


## Properties

A property within C# takes on the two kinds of ideas. It contains a mechanism to have either `get` and/or `set` accessor components. There is a kind of property which is **Automatically implemented** when defined.

```cs
public class Person
{
  public int Age { get; set; }
}
```

The above snippet will have data allocated for the `Age` property. This is effectively like a `field`. However, since it is like one, it does allieviate some issues when there is access to this field throughout a codebase and refactoring to use methods may be undesirable.

The other kind of property are ones that can have an expression or have another field backing them. This refers to the behaviour where the `get` and/or `set` components have an expression associated with them.

```cs
public class Person
{
  
  public int yearBorn;
  public int Age {
    get => CurrentYear() - yearBorn;
    set => yearBorn = CurrentYear() - value;
  }
  
  public static int CurrentYear()
  {
    // omitted
  }
}  
```

We can observe above how the `Age` property is able to have logic for `get` and `set` that will impact the `yearBorn` field.

## Encapsulation

You have seen the `public` and `private` access modifiers show up. These are to outline what can access the fields and methods of an object.

* `public` modifier does not have a limit in what can access it. It is accessible outside of the class.

* `private` modifier limits how where the attribute can be accessed. While `public` allows access outside of the class, `private` limits itself to the scope of the class.

### Protected

We have used the `public` and `private` access modifier but we will now use the protected access modifier. What does protected mean?

Similar to `private` it will not be accessible to other classes but now with the **exception inherited classes**.

* Is only accessible within the class
* Attributes and methods will be accessible by all subtypes
* Allows single definition of an attribute instead of multiple



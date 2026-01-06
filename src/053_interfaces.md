# Interfaces and Abstract Classes

We will be visiting how we are able to define abstract classes and interfaces, how they are used and when to use them. These are two powerful constructs within OOP that allow us to create some elegant abstractions.

## Abstract Classes

Although similar to a concrete class, an abstract class cannot be instantiated. It can define methods and attributes which can be inherited, inherit from super types and can be inherited from.

However, abstract classes can also enforce a method implementation
for subtypes. The main case for abstract is that we have some type that we do not want instantiated but is a generalisation of many other types.

Let's consider the following generalisations and their concrete types.

* `Shape` is a generalisation of `Triangle`, `Square`, `Circle` but we don’t
have a concrete instance of `Shape`.

* `Furniture` is a generalisation of `Chair`, `Sofa`, `Table` and `Desk`.

Simply, we are able to define an abstract class by using the abstract
keyword. This immediately marks the class as abstract and we do not
need anything more.

```cs
public abstract class Furniture
{
  
}
```

The above is an abstract class however, it doesn't really do much outside of being a category for other subtypes. We cannot instantiate the type as noted. Let's make this a little more interesting by introducing an `abstract` method.

```cs
public abstract class Furniture
{
  public abstract void Stack(Furniture f);
}
```

As you can observe, we have a method which has no definition, only the **signature**. We are able to declare an abstract method in only abstract classes. When we declare an abstract method we do not define a method body
(the logic of the method).

If the class should not be instantiated or behaviour is defined by the subtypes and not the super type the class should be non-instantiable.

```cs
public abstract class Furniture
{
  private string name;
  private List<Part> parts;
  
  public Furniture(string name)
  {
    this.name = name;
    this.parts = new List<Part>();
  }
  
  public void AddPart(Part p) {
    parts.Add(p);
  }
  
  public abstract void Stack(Furniture f);

}
```

We will now implement a **concrete** class called `WoodChair` that will extend from `Furniture`.

```cs
public class WoodChair : Furniture
{
  public WoodChair() : base("WoodChair"){ }
  
  public void Stack(Furniture f) {
    Console.WriteLine("Don’t put furniture on chairs!");
  }
}
```

Now, utilising this, we can observe that `WoodChair` is able to be instantiated and also able to use the **defined** methods in `Furniture` and its own implementation of `Stack`.

```cs
WoodChair f = new WoodChair();
f.stack(new WoodChair());
```

By attempting to stack another `WoodChair` onto another we will get the `"Don't put furniture on chairs!"` message.


## Interfaces

Interfaces share a similarity with abstract classes in that they declare methods that a class must implement and that the interface type cannot be instantiated.

However, unlike class based inheritance, classes can implement as many interfaces as they like. **We are not bound to implementing a single interface, we can implement multiple interfaces.**

*Maybe it might be best to ask, why would we want to do that?*

Especially with these restrictions as well.

* Cannot specify any attributes only methods

* Do not provide a method definition

* Cannot be instantiated

They can seem like a weaker version of abstract classes but these are actually the more powerful tool.

### Creating and using interfaces

Simply we are able to define an interface by using the interface keyword. Afterwards we will need to define a few

```cs
public interface Swim
{
  public void Swim();
  public void Dive();
}
```

For a class to inherit and implement an interfaces,

```cs
public class Dog : Swim
{
  // Implementations needed
}
```

We will use the following as a case study here, we will have an interface called `Move`.

```cs
public interface Move {
  public void Move(double hours);
}
```

We will then have `Dog` and `Dolphin` which both implement it.

```cs
public class Dog : Move {
  private string region; //Water or Land
  private const double LAND_MOVEMENT_SPEED_KMH = 50.0;
  private const double WATER_MOVEMENT_SPEED_KMH = 8.0;
  private double kmTravelled = 0.0;

  public Dog(string region) {
    this.region = region;
  }
  public void Move(double hours) {
    if(region.equals("water")) {
      kmTravelled += (WATER_MOVEMENT_SPEED_KMH *hours);
    } else if(region.equals("land")) {
      kmTravelled += (LAND_MOVEMENT_SPEED_KMH * hours);
    }
  }
  public double GetKMTravelled() {
    return kmTravelled;
  }
}

public class Dolphin : Move {
  private string region; //Water or Land
  private const double LAND_MOVEMENT_SPEED_KMH = 1.0;
  private const double WATER_MOVEMENT_SPEED_KMH = 60.0;
  private double kmTravelled = 0.0;

  public Dolphin(string region) {
    this.region = region;
  }

  public void Move(double hours) {
    if(region.equals("water")) {
      kmTravelled += (WATER_MOVEMENT_SPEED_KMH * hours);
    } else if(region.equals("land")) {
      kmTravelled += (LAND_MOVEMENT_SPEED_KMH * hours);
    }
  }
  public double GetKMTravelled() {
    return kmTravelled;
  }

```

There is a lot to the above example, however one key point here is that we have a single interface that is then implemented by two types which are not nicely grouped with a class.

They both have a similar implementation but their land and water movement speed is different. However! **We could change it completely between the two implementations.** It also still leaves them free for both class to use class based inheritance if they resemble a common category accurately.

Since both of them implement the interface `Move`, they can be considered as a `Move` type as well.

Let's see what happens when we run this inside a program?

```cs

public static void Main(string[] args) {

  Dog dog = new Dog("land");

  Dolphin dolphin = new Dolphin("land");

  Move[] movingAnimals = {dog, dolphin};
  
  foreach(Move m in movingAnimals) {
    m.Move(1.0);
  }
  
  Console.WriteLine(dog.GetKMTravelled()); // 50
  Console.WriteLine(dolphin.GetKMTravelled()) // 1.0
```

To note, we can see both objects listed under the `Move[]` array. We are then able to utilise the common method `Move` within both. This is a demonstration of **Polymorphism**.

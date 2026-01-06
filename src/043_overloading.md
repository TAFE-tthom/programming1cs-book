# Constructor and Method Overloading

What is overloading? In regards to C# we are able to use the same method name but with different method **signature**. We are able to define a method such as add and have a version that accepts two integers and another version that accepts three integers.
 
## Method Overloading

You may have observed that when using `Console.WriteLine` that it was able to convert your data elegantly. You didn't have to convert your datatypes to strings unless it was a custom object. This is because `WriteLine` and `Write` leverage overloading here.

To do this ourselves, we are able to simply create a method of the same name but we need to ensure that it has a different signature.


```cs
int Add(int a, int b);

int Add(int a, int b, int c);
```

The snippet above outlines a difference because there is 3 parameters for one and 2 for the first. It is easy to create a distinction here. It is possible to have the same parameters **but** we need to distinguish it in another way.

Let's observe an invalid case.

```cs
int[] Add(int[] a, int[] b);

float[] Add(int[] a, int[] b);
```

Method overloading is unable to be applied here. This is because the callsite of the function would have difficulties creating a distinction here between the two, especially if the type it is being assigned to is not apparent. To emphasise this, let's throw some **nulls** here.

```cs
int[] x = Add(null, null);

float[] y = Add(null, null);

object o = Add(null, null);
```

For 1 and 2, it isn't clear what is being called, although the type it is being assigned to could give-away some more information about that.

For 3, this is why the return type isn't too helpful, since the datatype could used to assign either `float[]` or `int[]`, it isn't too useful.

So, we could have the following calls as well which can feel like a bit of a trap but can be resolved.

```cs
int[] CrossProduct(int[] a, int[] b);

int[] CrossProduct(float[] a, float[] b);
```

The above is okay but we do have ambiguous statements still, especially with `null` throwing some issues here. However we can leverage **casting** in this situation.

```cs
int[] x = CrossProduct((int[])null, (int[])null);

int[] y = CrossProduct((float[])null, (float[])null)
```

We can observe that when casting arguments to their appropriate types, it is able to decide what method it is calling.


## Constructor Overloading

Now that we have established method overloading, we can also apply this to constructors. We can observe the same overloading concept applied to constructors. This can be applied to both overloaded constructors within the same class as well as super constructors.

We are able to also utilise certain constructors for other constructors if we have already defined that behaviour.


```cs
public class Person {
  private static int DEFAULT_AGE = 21;
  private string name;
  private int age;
  
  public Person()
  {
    name = "Jeff";
    age = DEFAULT_AGE;
  }

  public Person(string name)
  {
    this.name = name;
    this.age = DEFAULT_AGE;
  }

  public Person(string name, int age)
  {
    this.name = name;
    this.age = age;
  }
}
```

We can see that there are 3 different constructors. Within our own code we choose to call anyone, in fact we have already been doing this!

```cs
  Person p1 = new Person(); //Jeff the default human!
  Person p2 = new Person("Janice");
  Person p3 = new Person("Dave", 32);
```

Since each constructor has a unique signature, we are able to utilise specific constructors by satisfying the correct types.

### `this` has another use!

Within C#, similar to where you may have seen with `inheritance` and using `base`, we can use the `this` keyword in a similar position. To refactor the class above, we can simply leverage the last constructor and the rest are able to utilise it.

```cs
public class Person {
  private static int DEFAULT_AGE = 21;
  private string name;
  private int age;
  
  public Person() : this("Jeff", DEFAULT_AGE) { }

  public Person(string name): this(name, DEFAULT_AGE) { }

  public Person(string name, int age)
  {
    this.name = name;
    this.age = age;
  }
} 
```

We are able to observe that constructor 1 and 2 are using Constructor 3, since 3 is setting the values for both fields.

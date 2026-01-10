# Supplementary - Structs, Records and Partial Classes

You will occasionally start seeing some interesting concepts in C# that are either unique or resemble something else. In this section, we will look into structs and partial classes.


## Structs

Structs are a type in C# with its roots back in C++ and C. While it is an aggregate type like others, it is a **value type**. This does mean that there are some slightly different rules than reference types.

```cs
public struct PixelData
{

  public byte Red { get; set; }
  public byte Green { get; set; }
  public byte Blue { get; set; }
  public byte Alpha { get; set; }

  public PixelData(byte red, byte green, byte blue, byte alpha)
  {
    Red = red;
    Green = green;
    Blue = blue;
    Alpha = alpha;
  }

  public int ToInt()
  {
    return (
      Red << 24 |
      Green << 16 |
      Blue << 8 |
      Alpha
    );
  }  
}  
```

The above defines a struct that represents pixeldata, it includes RGBA channels. We will look into the usage of structs in the snippet below.

```cs
public static void Main(string[] args)
{
  PixelData p1;

  PixelData p2 = new PixelData(255, 0, 255, 255);
  
}
```

We can observe how the above demonstrate two constructions, since `p1` is a value type, the values sets in are assigned to their default value (0).

Accessing the fields while we have not **initialised** `p1` in the conventional sense, is valid.

```cs
public static void Main(string[] args)
{
  PixelData p1;
  p1.Red = 255;
  p1.Green = 128;
  p1.Blue = 128;
  p1.Alpha = 255;

  PixelData p2 = new PixelData(255, 0, 255, 255);

  PixelData p3 = p1;
  
}
```

The above snippet is interesting because we can observe how we can set the fields of `p1` after declaration. With `p3` being assigned to `p1`. This will result in a **copy** of `p1` being written to `p3`. This is similar to how `int`, `float` and other value types work.


## Partial Classes

Partial classes are a fairly straight forward concept but one that should be sparingly used. Occasionally we will have generation of classes at compile time that may create more capabilities for a particular class.

This is where partial classes come in handy although they are also applicable for the programmer to use. You can consider the following as an example (`PixelData_Part1.cs`, `PixelData_Part2.cs`).

**PixelData_Part1.cs**

```cs
public partial class PixelData
{

  public byte Red { get; set; }
  public byte Green { get; set; }
  public byte Blue { get; set; }
  public byte Alpha { get; set; }

  public PixelData(byte red, byte green, byte blue, byte alpha)
  {
    Red = red;
    Green = green;
    Blue = blue;
    Alpha = alpha;
  }

  public int ToInt()
  {
    return (
      Red << 24 |
      Green << 16 |
      Blue << 8 |
      Alpha
    );
  }  
}  
```

We have our first component of the partial class. The second component will allow ass to add an additional method to it.

```cs
public partial class PixelData
{

  public static PixelData FromInt(int data)
  {
    byte red = data >> 24;
    byte green = (data & 0x00FF0000) >> 16;
    byte blue = (data & 0x000FF00) >> 8;
    byte alpha = (data & 0x00000FF);

    return new PixelData(red, green, blue, alpha);
  }
  
}
```

We have added an additional method ot the class itself that adds a static method to it.

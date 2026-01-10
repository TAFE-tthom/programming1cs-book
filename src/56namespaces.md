# Namespaces and Code Organisation

The idea of namespaces and encapsulation are linked, these two concepts are to control the scope/visibility of types and identifiers within our codebase. As we observed with encapsulation which governs the visibility of fields, properties and methods inside a class, namespaces are names which give to groups of types.

## Making Namespaces

In a classical usage of namespaces in C#, the scoping idea is similar to that of classes and methods. We use the braces to indicate what types are grouped under a namespace.


```cs
namespace MusicLibrary
{
  public class Album
  {
    private string title;
    private string artist;
    private string[] songs;

    public void SetArtist(string name)
    {
      artist = name;
    }

    /* Rest snipped */
  }
  
}
```

Alternatively, we can declare a namespace for a particular **file** by specifying it at the top without curly braces.

```cs
namespace MusicLibrary;

public class Album
{
  private string title;
  private string artist;
  private List<string> songs;

  public Album(string title, string artist)
  {
    this.title = title;
    this.artist = artist;
    this.songs = new List<string>();
  }

  public void SetArtist(string name)
  {
    artist = name;
  }

  /* Rest snipped */
}
```

### Using Namespaces

Now, to utilise the types grouped under the namespace we have created,w e can do this in a few different ways. We can use the full-qualified name of the namespace and type.

```cs
class Program
{
  public static void Main(string[] args)
  {
    var album = new MusicLibrary.Album()
  }
}
```

However, this may feel repetitive if we are using the full name each time. So we can shorten it by leveraging the `using` keyword.

```cs
using MusicLibrary;

class Program
{
  public static void Main(string[] args)
  {
    var album = new Album()
  }
}
```

The above will now expose the types that are scoped to the `MusicLibrary` namespace within this file.


## Organising Code

Using namespaces is somewhat key to structuring files and grouping them effectively. A key thing to note with **namespaces** is that the namespace identifier can be used in multiple files, it is not constrained to just one.

While there are components that will need to focus on application architecture, we can focus on how best to group namespaces and folders. As part of a good convention, group your namespaces inside folders.

```
ColorLib (Project)
|--- ColorModel (ColorLib.ColorModel)
|     |--- RGB.cs
|     |--- HSL.cs
|     |--- HSV.cs
|
|--- Blending (ColorLib.Blending)
      |--- Additive.cs
      |--- Subtractive.cs
      |--- Multiply.cs
      |--- Burn.cs
```

The above provies a structure where the namespaces are reflective of the folder structure itself. However, given the scale of your application it is reasonable to only create the folders when necessary (the project usually starts with 1 file initially).

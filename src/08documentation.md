# Documentation

As with many programming languages, we are able to build into and document our code using supported comment line signifiers in combination with XML tags. This will allow us to then automatically generate documentation that can be readable or targetable for another platform.

## Summary of classes and methods.

Let's study how we can build into documentation with C# with a particular scenario. Given the `Logger` class, we will now document the class and methods associated.


```cs
namespace Logger;

/// <summary>
/// Class <c>Logger</c> which will keep a log of the user input
/// </summary>
public class Logger
{

  /// <summary>
  /// Constructor <c>Logger</c>, constructs the Logger class
  /// </summary>
	public Logger(string path) {}

  
  /// <summary>
  /// Method <c>ReadLine</c> which reads a line and logs it
  /// </summary>
	public string? ReadLine()
  {
		return "";
	}


  // Rest snipper
}
```

The above code snippet demonstrates the summary tag being used to provide a description of the method or class. This can be also used in conjunction to code snippets and examples inside the documentation.

Refer to the [CSharp Documentation Comments](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/documentation-comments) for further insight.

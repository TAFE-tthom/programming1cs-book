# Source Files

With any programming language, we typically want to translate the keystrokes we input into our text editor that we will use to save the file that stores them.

This is no-different with C#.

Using the text editor of your choice, make sure you get familiar with the basics

* Opening a file
* Opening a folder
* Creating a new file
* Saving a file
* Writing and deleting text inside that file.

Prior to executing code, make sure you have saved your files so when the interpreter works with it, it has the latest updates.

## Okay! But what is a source file?

A source file is typically a text file that will contain **source code**. The kind of **source code** is going to be of the C# variety. As per convention, when we save a C# file, we should use the `.cs` extension.

By using the appropriate extension, this will give a hint to the operating system about what app to open it with. Hopefully it should default to your text editor however you can adjust this setting for your own benefit.

## What do we do with source files? 📒

In our current context? We will write code, compile and then execute it using `dotnet` (or you can run them directly once compiled). Later on, we will see how it will take on a different roles and purposes.

The tooling in the C# ecosystem 

* Retarget the platform, make binaries for Mac, Linux and Window (among other platforms)
* Build cross-platform applications using AvaloniaUI with XML/XAML
* Much more...

For our purpose and what is typically common regardless of what is mentioned above.

## Are source files the program? 📒

In the context of **C#** and **Java**, these are languages that are compiled languages. The compiler assists with catching some issues that the programmer may have left in if they were not mindful at the time. **C#** compilation process will typically emit a native executable when compared to **Java** but they will still contain bytecode that will need to be interpreted.

## Walkthrough 💻

Using your chosen text editor, make sure your can:

* Create a file and name it, make sure the file extension is `.cs`.
* Write into the file and save it.

Refer to the example below and how it is laid out.

```cs
class Program
{

  static void Main(string[] args)
  {

    int answer = 50;

    if(answer >= 50)
    {
        Console.WriteLine("You passed!");
    }
    else
    {
        Console.WriteLine("Oh no, something went wrong");
    }
  }
}
```

The above is from a source file that is simply testing a variable (`answer`) and checking to see if it is greater than `50` and outputting `You passed!` or going down the other path.

Use the command snippet below (and refer to the previous chapter on creating a project with `dotnet`), use the following and observe the output.

```
dotnet run
You passed!
```

You will the notice the output from the program on the next line.


## Structuring Your Source File 📒

While it is implied from the snippet above, the execution of program starts at the **top** of the file and goes down. While it isn't always going to be as simple as that, it is a crucial bit of information to hold onto.

When structuring your program it is best to form some good habits and reserve some space for when certain things are to be appropriately placed and clustered.

We will look at the following snippet.

```cs
class Program
{
  // Formatting output and printing it
  static void outputFilePath(string filepath)
  {
    string output = $"The file that will be used is: {filepath}";
    Console.WriteLine(output);
  }

  static void Main(string[] args)
  {
    string filepath = "example.txt";

    if(args.Length > 1) {
      filepath = args[0];
    }

    outputFilePath(filepath);
  }

}

```

* Class definition, since C# is an OOP language and is influence from **Java**, it will have a class definition, normally this is named `Program` if it contains an entry point method (such as `Main`).

* Method definitions are placed inside the **Class**. While it isn't strictly the only way to do this, it is common convention as part of structuring your program.

* Variable declarations and initialisation along with other statements, these are within method definitions or are considered class fields/properties. Top-level variables and statements are different to those made inside functions and classes, as they are normally considered **globals**.


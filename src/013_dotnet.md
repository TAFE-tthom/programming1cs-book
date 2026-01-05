# Dotnet

 `dotnet` is going to be a common build tool that you use through out this. It serves the purpose of building, packaging and running our programs that are constructed.

If you have installed the SDK correctly, you should have access to the `dotnet` command. This command will be responsibile for creating projects from templates, compiling and running your programs.

*Why aren't we using Visual Studio?*

You are free to do this! However, there is a lot of value in interacting with the command line for **dotnet** as you may be responsible for deploying and building programs and not have access to a GUI. It also supports when you want to automate builds for continuous integration and delivery.


## Concepts

* `dotnet` command, compilation and source code
* What a *Virtual Machine* is.
* Compiled and Interpreted programs

## C# Programs and `DotNet`

While C# default CLI program will outline using **Top-Level Statements** by default, it is best to be upfront and expose what is being generated for you and decompose it.

To create a project using `dotnet`, you will do the following.

```
[user@hostname Projects]$ dotnet new console -n HelloWorld --use-program-main

- Output Snipped

[user@hostname Projects]$ ls
HelloWorld
```

The above snippet will create a console application in a folder called `HelloWorld` and ensure we have a `Main` method as its entrypoint. Changing directories to the project folder `HelloWorld` will reveal the following files.

```
HelloWorld.csproj obj Program.cs
```

These are responsible for the following.

* `.csproj` is a project file which for now, we won't have too much interaction with but will be used to integrate third part libraries and references.

* `obj` folder is responsible for metadata and caches for your project. This is used alongside `.csproj` files and your program.

* `Program.cs` this file is our **program**, it will contain code that will be compiled.

Lets inspect `Program.cs`.

```cs
namespace HelloWorld;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, World!");
    }
}
```

When creating a project like this (ensuring we are not using top level statements). We will always have a `Main` method which is where the program starts. Our program is doing a simple job already which is emitting `Hello, World!` which is standard for most templates (The relation between the project name what is being outputted is down to convention, everyone's first program is usually something akin to `Hello World`).

### Building our program

We already have something we can build and run, so we will go through the steps of **compiling** and **running** our program. We will use the `build` subcommand for `dotnet` to achieve this.


```
[user@hostname HelloWorld]$ dotnet build
Determining projects to restore...
  All projects are up-to-date for restore.
  HelloWorld -> /home/user/Projects/HelloWorld/bin/Debug/net10.0/HelloWorld.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.68
```

The above snippet shows the usage of `dotnet build`, however you may want to observe what the output is stating here. If the `Build succeeded`, we are then able to run the program. However the build could fail for a large number of reasons, notably, if you have a syntax error in your code.


Now is time to run our program. We will use the `run` subcommand.

```
[user@hostname HelloWorld]$ dotnet run
Hello, World!
```

We can then observe the `Console.WriteLine` part in the source code will allow us to print to the screen. Do note! You can call `dotnet run` and if the build process has not been triggered, it will also recompile your code again.


### Compilation and Virtual Machines

To note though, we need to make the process behind compilation and execution clear as you will hear that C# is *compiled* and *interpreted*. The answer is that it is **both**.

What occurs when we build a project.

1. When running `dotnet build`, this will analyse your source code and perform the necessary checks to make it suitable for translation.

2. When translating your source code, it will be translating into **machine code**, now that **machine code** is not x86 or ARM (or the target platform). It is translating into **CIL** (Common Intermediate Language).

3. When running `dotnet run`, the **CIL** code is then interpreted by the **CLR** (Common Language Runtime) which is a virtual machine that then translate it to **machine code**. 

Importantly, the *interpreting* part is actually indicating that we have a machine inside our machine. This is called a *Virtual Machine*.

What compilation means is that when we are taking the source code and outputting machine code, normally something that is not pleasant for humans to read or write by hand.

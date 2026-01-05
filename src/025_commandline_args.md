# Command Line Arguments

This is specifically a desktop application component. As you have observed command line arguments from **Chapter 1**, you are able to build programs that are able to use command line arguments as well.

When executing code with `dotnet run`, you input command line arguments that can be used within your program. You would have observed this when going through the command line chapter.

## Using Command Line Arguments

To retrieve command line arguments from your application, you will need to use the following code segment:

```cs
static void Main(string[] args) {
  string arg1 = args[0];
  string arg2 = args[1];

  Console.WriteLine(arg1);
  Console.WriteLine(arg2);
}
```
The 0th and 1st index of the `args` array is where the arguments are stored for our program.


Example:

```
dotnet run Monday Tuesday
```

Given the snippet to retrieve the first two arguments given, `arg1` will map to `Monday` and `arg2` will map to `Tuesday`.

Keep this in mind as well, the datatype that `arg1` and `arg2` are associated with is the `string` datatype. Note down some of the concepts that may be new here. We will be revisiting some concepts like Arrays and Import later in the book. 📒

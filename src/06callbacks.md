# Callbacks and Delegates

An important piece in javascript and most programming languages is the idea of a `callback` or `function pointer`. The idea with callbacks is that, like other bits of data that we can pass as arguments as part of function calls, we can also pass a function as an argument as part of a function call.

Delegates, Func and Action are types within C# that represent callbacks. In addition, lambda operator is also a way of constructing a callback that is a more concise version of a delegate/callback.

*Why would you do this?*

Primarily, we can usually identify an algorithm that is mostly agnostic to the data it is using with the exception to when it needs to do something with that data.

A great example is **sorting**, this is because sorting algorithms are typically focused on how to traverse a collection efficiently 

## Examples of a callback

Let's look at a realworld example where we would 

```cs
int NumberCompare(int x, int y) {
  return x - y;
}

//Rest snipped

int[] nums = [ 5, 2, 7, 8, 1 ];

Array.Sort(nums, NumberCompare); // nums is now [1, 2, 5, 7, 8 ]
```

The above snippet outlines how we provided a callback outline the difference between two numbers. The `NumberCompare` method is passed as an argument to be used to compare two numbers when sorting.

The `Array.Sort` method will use the `nums` array and `NumberCompare` function to compare a pairing which will then inform if the elements are to be swapped. While we are not calling `NumberCompare` directly, we have handed it to `Sort` to manipulate it.

```cs

//Assuming s is a string
int GetLength(string s) {
  return s.Length;
}

string[] words = [ "One", "Zip", "Flower" ];
int[] wordLengths = words.Select(GetLength).ToArray(); //[ 3, 3, 6 ];
  
```

The above would typically require us to utilise a loop while the `.Select` call has the loop built into and will call the `GetLength` function during it.

Let's look at re-writing both examples to use **lambda operators** instead.

```cs
string[] words = [ "One", "Zip", "Flower" ];
int[] wordLengths = words.Select(s => s.Length).ToArray(); //[ 3, 3, 6 ];
```

We can observe the re-write of callback for `Select` to now be inlined rather than referring to a named method. This allows the developer to support methods which are suitable in the event one doesn't exist or it isn't appropriate to link it to anothher.

```cs
int[] nums = [ 5, 2, 7, 8, 1 ];

Array.Sort(nums, (x,y) => x - y); // nums is now [1, 2, 5, 7, 8 ]
```

With multiple parameters, we need to ensure that we distinguish between what is a lambda expression and method argument, we are able to do this by wrapping the paramters with paranthesis.

## Delegates

Delegates within C# are used as a mechanism to construct a type that will represent a callback in C#. In many ways they are similar to interfaces but limited to just a single method and that method is unnamed.

Let's take a look at the following example.

```cs
delegate void MyCallback(string msg);
```

The above delegate provides a return type and paramter list, the type name is called `MyCallback`. This means we are able to use this name as a variable type.

```cs
static void PrintMessage(string msg) {
    Console.WriteLine(msg);
}

// Rest snipped

MyCallback cb = PrintMessage;

cb("Hello!"); //Outputs "Hello!"
```

We can observe that `cb` can be assigned to a static method that meets the same `signature` as the `MyCallback` type. We can then invoke it like any other method.

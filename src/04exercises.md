# Exercises

## Tasks


### 1. Sum of 4

You will need to implement a function that will sum 4 numbers given as arguments. You will need to implement the function below in the `Sum.cs` file.

```cs
static int SumOfFour(a, b, c, d)
```

The `sumOfFour` function has 4 parameters (`a`, `b`, `c`, `d`), each parameter is assumed to be a number and as such, when called, will be supplied with a number.

The function `sumOfFour` must add all 4 numbers together and return the result.

Example Usage 1:

```cs

int result = SumOfFour(1, 2, 3, 4);

Console.WriteLine(result); //Outputs: 10

```

Example Usage 2:

```cs

let result = SumOfFour(4, 5, 1, 10);

Console.WriteLine(result); //Outputs: 20

```

Example Usage 3:

```cs

let result = SumOfFour(8, 9, 22, 10);

Console.WriteLine(result); //Outputs: 49

```

### 2. Searching Arrays


A common problem within programming is searching and it is best you get familiar with
implementing solutions to these problems. You have been tasked with implementing two
methods.

Implement the following function:

```cs

static int FindWord(string[] words, string word) {

  return -1; //You should return the index
} 
```

The `FindWord` function will search an array of strings (`words`) and check to see if `word` matches one of those. When the first instance of a match is found, the index of where that word is, should be returned.

If no match is found, `-1` should be returned.

```cs

string[] allwords = ["Hello",
  "Good", "Today", "Tomorrow", "Time", "Puzzle"]

int loc1 = findWord(allwords, "Good"); // 1

int loc2 = findWord(allwords, "Time"); // 4

int loc3 = findWord(allwords, "Jigsaw"); // -1

```

Comment and explain your implementation, consider using the `break` [keyword](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/jump-statements) to help exit a loop early.

Explain why `-1` is reasonable return value if we can't find the the word within the array.


### 3. Shopping List

Write a class that will allow the user to add new shopping items and their quantity to it. The class should be called `ShoppingList` and will have the following methods.

* `ShoppingList()` - Empty constructor, initialises fields

* `AddItem(product, quantity)` - Adds a product to the shopping and the quantity associated.

* `GetDetails(product)` - Find the product by name and returns both the product name and quantity.

* `Details()` - Returns an array of all products and their associated quantity.


### 4. Character Occurrence

You are tasked with writing a function that will accept a string as an argument and a character as an argument. Your function will count the number of times that character shows up in the string and return that value.


Example 1:

Checking the number of times 'l' shows up in 'Hello'

```cs

Occurence("Hello", "l"); //2
```


Example 2:

Checking the number of times 't' shows up in 'What is the time'

```cs

Occurence("What is the time", "t"); //3
```

Your solution should be case-insensitive (lower case 'l' will also map to 'L' and vice-versa).


## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-cs>.

Attempt the following exercises in the **Week04** folder.

Ensure you run `dotnet build` and `dotnet test` while your shell is in the directory of a particular question. Run `dotnet test` to check to see if your solution works as specified.


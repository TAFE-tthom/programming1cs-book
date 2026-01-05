# Exercises

## Tasks 💻

Work on the following tasks as a way to ensure you have understood this chapter's topic.

### 1. Even of Odd

You have been tasked with writing a program that can identify a value or even or odd. The input will be given as a command line argument.

Consider what operator you may want to use that could easily tell you if number is even or not.

Restrictions: You cannot use any `built-in` C# functions, only operators and if statements. You are also being asked to avoid the `/` operator and `Math.*` methods.

Your program should not be more than 10 lines.

Example 1:

```
dotnet run 23
Odd
```

Example 2:

```
dotnet run 52
Even
```

Example 3:

```
dotnet run 101
Odd
```

## 2. Timestable

Create a program that will output the timestable of a number specified from command line arguments. This should only be until we have reached a multiplication of `n * 12`

When the command line argument is 6.

```
6
12
18
24
30
36
42
48
54
60
66
72
```

## 3. Number Ranges

Construct a program that will accept 3 command line arguments in the form of `start`, `end`, `step`.

* `start` - is used as the starting number
* `end` - is used as the final number
* `step` - is how much to skip by.

To demonstrate how this works.

```
node generate.js 6 30 3
6
9
12
15
18
21
24
27
30 
```

For every iteration, `3` was added to the current counter.


### 4. Roller Coaster

This program requires you to implement a function called `checkHeight`. Firstly, construct a file called `rollercoaster.js`, afterwards define the following function:

```cs
static bool CheckHeight(height, threshold) {

  return 0;
}
```

You will need to implement `checkHeight` to do the following. Given that the function has two parameters `height` and `threshold`, your function is to check to see if the height matches or exceeds the threshold.

Consider the following usage, the heights are and threshold are assumed to be integers that correlate to centimetres:

```cs

//Paul is 180cm, the threshold is 160
bool doesPaulPass = CheckHeight(180, 160); //true;

//Alice is 160cm, the threshold is 160
bool doesAlicePass = CheckHeight(160, 160); //true;

//Jeff is 150cm, the threshold is 160
bool doesJeffPass = CheckHeight(150, 160); //false;
  
```

Comment on the usage of the parameters and how you have tested your function implementation outside of the example given.

## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-cs>.

Attempt the following exercises in the **Week03** folder.

Ensure you run `dotnet build` and `dotnet test` while your shell is in the directory of a particular question. Run `dotnet test` to check to see if your solution works as specified.


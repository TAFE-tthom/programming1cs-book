# Loops

Loops are our construct for iteration. They allow us to repeat operations until a condition is met. Similar to `if` statements, the condition that is used, is a boolean expression.

## Where and when would I use loops?

The keypoint with loops is the **iteration**, we are able to change values inside the loop scope itself.

Consider the following scenarios

* Outputting numbers 1 to 10
* Keeping a game running until only 1 player is left
* Finding a character in a string
* A program that requires input from a user until they write `QUIT`

These scenarios outline a pattern we want to encode and perpetuate until a condition is no longer met.

## while loop

Two primary loop constructs are `while` and `for`. `while`'s layout is very similar to an if statement and simply needs a boolean expression.

```
while( boolean_expression )
{
  
}
```

However, what happens if the expression is true? Well, if it is its first time evaluating it, it will enter the loop scope `{ ... }` and execute code in between.

If it is, the second or third or ... nth iteration and the expression remains true, it will continue executing the statements within the scope.

Example:

```cs
int x = 0;

while(x < 10)
{
  Console.WriteLine(x);
  x += 1;
}
```

The above snippet will print numbers 0 to 9. When `x` eventually reaches the value 10. It will exit the loop. To change the loop to output from 9 to 0, there are two ways we could restructure this.

Method 1:

```cs
int x = 0;

while(x < 10)
{
  Console.WriteLine(9 - x);
  x += 1;
}
```

We hadn't changed the condition, however we did change the **console.log** statement to subtract from `9`. In spirit though, `x` is still counting upwards.


Method 2:

```cs
int x = 9;

while(x >= 0)
{
  Console.WriteLine(x);
  x -= 1;
}
```

We have made some significant changes here. `x` now starts at 9, the condition is `x >= 0`, which is outlining that if x is greater than or equal to 0, continue executing the loop. Lastly, we decrement the value of `x`.

As an **experiment!** What happens if you forget `x -= 1;` or `x += 1` in either method? Does the loop terminate? 💻

**Important**
If you happen to have an non-terminating loop, use the shortcut `CTRL+C` which will send an interrupt signal to the process in your terminal.



## for loop

This leaves the `for` loop construct. This is where the construct has three parts but we will link it to how our previous `while` loop.

With a `for` loop, it follows the pattern:

```
for(initialisation; boolean_expression; updates)
{
  
} 
```

You should be able to understand the equivalence between the two. The way the above `for` loop maps to a `while` loop is as follows.

```
initialisation;

while(boolean_expression)
{

  updates;
}
```

To create a similar loop to the previous `while` loop section, one can write the following code.

```cs
for(int x = 0; x < 10; x += 1)
{
  Console.WriteLine(x);
}
```

To also note, commonly, `x += 1` isn't usually used, the shorthand version `x++` is typically preferred. There isn't anything different in this context, it is simply shorter.

We can now see that the initialisation which was once outside of the `while` loop is now in the `initialisation` position, the similarity of the boolean expression and the position of the update is different.


## What about do-while?

While this construct does exist, it is less common in practice. Normally this is because the `do-while` provides a guarantee that it will execute at least **one** iteration.

However, some optimisers will transform some `for` or `while` loops into a `do...while`. Assuming it can find a guarantee that the loop executes once, it may make this change.

Similar to a `while` loop, however, the block is always executed once.

```
do {

  
} while(boolean_expression)
```

Do write a similar counting loop like before, we can create the following loop.

```cs
int x = 0;

do {

  Console.WriteLine(x);
  x += 1;
} while(x < 10);
```

## Equivalance of loops 🖊️ 💻

It should be noted that for any loop you can construct with a `while` loop, you can construct it with a `for` loop and vice-versa.

Take the following on as a challenge, convert these two loops into an equivalent version but using a different loop keyword.

**Loop 1**

```cs
bool keepRunning = true;
int counter = 10;

while(keepRunning)
{

  if(counter <= 0)
  {
    keepRunning = false;
  }
  counter--;
}
```

**Loop 2**

```cs
int x = 10;
int y = 10;

int mx = 2;
double my = 2.003;

for(int i = 0; Math.Floor(x) === Math.Floor(y); i++)
{
  
  x = x * mx;
  y = y * my;
  Console.WriteLine(x);
  Console.WriteLine(y);
}

```

Just make sure you construct the opposite of what is there. No point redoing the `for` loop when one is right there.

# Recursion

Recursion is a technique within computer science that allows
calling a function within itself. They are made of at least these two compononents.

* Base-Case - Where the function terminates and does not call itself
* Recursive-Case - Where the function will converge eventually to the base case

Recursive functions are broken into one or more base cases and recursive cases. The base case is a condition under which the recursion stops and some value is returned, while the recursive case is where the function calls itself.

```
f(x):
  if x is 0
    return 1
  else
    return f(x - 1)
```

The above pseudo-code is simply counting down from value `x` to 0. When x is **not** 0, it will call `f` again and subtract 1 from x.

## Why recursion?

Problems can often been represented easier with recursion. However, we are able to translate any recursive function to an iterative counterpart. 

* Recursive methods can be simpler to read and write.

* Immediately writing an iterative method where there is an established recursive method can be considered a premature optimisation.

However there are drawbacks to recursion and you typically don't see it end up in production systems.

* You don't have infinite recursion, each stack-frame (from a function call) has to be held in memory.

* Inefficient with memory


## Call Stack

C# is a stack-based language so when a function or method is executed it is put onto a call-stack. The function or method being executed at the top of the stack is the most recently called method.

A method finishes executing once it has reached a return state or for `void` or function/method without a return statement, simply reaches the end of scope.

Everytime a method is called, data associated with that call needs to be allocated. This is known as a **stack frame**, it is a temporary allocation where the size of the frame is known at parsing time but the number of frames is not know until we are executing it.


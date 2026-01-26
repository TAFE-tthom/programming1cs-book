# Funcs and Actions

We are going to focus on two types of delegates that are used consistently through out C#. These two types help simplify and enforce consistency through out the standard library.

* `Func` - This particular type provides type parameters for zero to many parameter types and for **a return type**.

* `Action` - Action is similar to `Func` but does not provide a type parameter for the return type.

* In addition there is `Predicte` but it is a variant of `Func`. It forces the return type to be `bool`.

## Construction and usage

The construction of `Func` or `Action` callback is similar to that of others. However we need to leverage type arguments in this case. We will demonstrate this with a `Func` type and a comparator.

```cs
int IntCompare(int x, int y)
{
  return x - y;
}

// Rest is snipped
//   p1   p2   r
Func<int, int, int> intcmp = IntCompare;
```

We can observe, similar to the delegate definition that we are able to declare a variable and assign it to a method. `p1` and `p2` are the types for the parameters while `r` is the return type.

In addition, we can construct a method inline as well, we will demonstrate this with `Action`.

```cs
int z = 0;
// Rest is snipped
//     p1   p2 
Action<int, int> addoperation = (x, y) => {
  z += x;
  z += y;
};
```

We can observe that the `Action` does not return any value and part of the declaration here is that `Action` must have two parameters of type int.

# Exceptions and Handling

We will be exploring exceptions more in depth with C#. Why they are part of the design of the language as well as the advantages and disadvantages with exceptions.

Exceptions can be considered an except state within our program.

## Examples of Exceptions

Exceptions evolve from the state of the machine or program execution being considered invalid.

Consider the following issues and why an exception may be thrown here.

* Dividing by 0
* Accessing memory that does not belong to your process
* Dereferencing a null pointer
* Unable to parse text
* Out of memory

There are a number of aspects we need to consider with the usage of exceptions.

Within C#, exceptions are considered **unchecked** or at least may **warrant** a warning from the compiler. This is by design but as a point of comparison, some languages like **Java** will require the programmer to handle the exception. Those are known as **checked** exceptions.

## Throwing and Handling Exceptions

If an error can occur and it is unreasonable for the caller to to attempt to prevent the catching of the exception then it can be a runtime exceptions. These kinds of exceptions should be rare instances.

*When to use exceptions?*

When we write a methods we may need to make a few assumptions.

* Using a floating point variable although the range of values should be between 0.0 and 1.0.

* If the system is in an invalid state, (Order is in the state Paid but no payment has occurred)

* Only positive values accepted.

This may result in most our methods being candidates for exceptions, however that would be absurd. We should consider the **precondition** that is required for our method and if there is an appropriate default or value to represent an error or if an exception is appropriate.

Let's look at using the `throw` and `try-catch` keywords/blocks in the example below.

```cs
try
{
  var emails = GetEmails(inboxId);
}
catch (ArgumentException e)
{
  Console.Error.WriteLine("Unable to retrieve the inbox");
}  
```

In the above snippet, we are using what is known as a `try-catch` block. Since we are aware that the method can **throw** an exception, we are making sure we handle the case by `catch`-ing it.

This results in the catch block having code to output to the shell when this occurs. If it does not it will not trigger it.

```cs
  public Email[] GetEmails(int inboxId)
  {
    if(inboxId < 0)
    {
      throw new ArgumentException("Identifier given is invalid");  
    }
    // snipped the rest of the code  
  }
```

The above snippet shows the method `GetEmails` throwing an exception when the `inboxId` parameter contains the value that is less than 0. We use `throw` to create a new object and trigger an exception in the program.

### Preconditions

A precondition is input that must be within its bounds for it to execute correctly. For example, if the method expects only a positive integer, any negative integer breaks the constraint of afforded by the method.

We may want to invoke an exception NegativeIntegerException,`InvalidIntegerException` or something more specific the problem domain.


### Drawbacks to Exceptions

There are performance costs associated with throwing exceptions that
involve stack unwinding and stack trace construction.

* Stack Unwinding - Is costly because it has to copy stack frame information when entering a `try` block as to know where to move to next.

* Stack Trace Construction - Since an exception has occured, information about where it was generated needs to be known. This requires stack frame information and call-stack information to be extracted and constructed/formatted.

While performance is an issue, it is likely you wouldn't put exceptions in paths where they are likely to occur frequently, especially in a real-time or time sensitive system.


## Creating Exceptions

Within C#, you are able to construct your own exceptions and inherit from the base class from the standard library. To do this, you will need to leverage inheritance. We will use the domain of a `Monitor` and setting its refresh rate.

The following Monitor class will contain a field called `refreshRate`, this can't be a negative value and we may want to check to see if the refresh rate is even supported.

```cs
public class Monitor
{
  private double refreshRate;
  public const double MAX_REFRESH_RATE;

  public Monitor(double defaultRate, double max)
  {
    MAX_REFRESH_RATE = max;
    refreshRate = defaultRate;
  }
  public double SetRefreshRate(double hz)
  {
    refreshRate = hz;
    return refreshRate;
  }
}
```

To define an exception `InvalidRefreshRateException`, another class will be created to do this.

```cs
class InvalidRefreshRateException : Exception {

  public InvalidRefreshRateException() : base("Unsupported refresh rate value")
  { }
}
```


We can then change the `SetRefreshRate` method to utilise this exception.

```cs
  
  public double SetRefreshRate(double hz)
  {
    if(hz < 0 || hz > MAX_REFRESH_RATE)
    {
      throw new InvalidRefreshRateException();
    }
    else
    {
      refreshRate = hz;
    }
    return refreshRate;
  }
```

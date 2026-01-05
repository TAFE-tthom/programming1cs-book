# Break and Continue

Within loops, we may have situations where we want to exit the loop early or indicate that we want to go next iteration early.

There are some useful cases for `break` and `continue` as they can use `labels`. These mechanisms allow us to change the control flow on another level, although you may not see them in practice often as it can make the code very difficult to read.


## Break and Continue

We will examine some scenarios where `break` and `continue` are used.

### Break

`break` keyword allows for us to break out of a loop early. This means that the condition in which we entered the loop isn't necessarily the reason it has stopped.

Let's take loop of the following snippet of code. 

```cs

string hasMessages = true;

while(hasMessages)
{

  string message = GetMessage();

  string hasMessages = CheckForMessage();

  // Empty message, should finish early
  if(messages == "")
  {
    break;
  }
  else
  {
    Console.WriteLine("You have received: " + message);
  }
  
}
```

The snippet calls a function `getMessage` to retrieve the latest message for itself, it is a simple string in which we compare if the message received is an empty string.

If so, it does not matter if `hasMessages` is `true` or `false`.

 
### Continue

`continue` allows the code to go to next iteration. For loop statements where a particualr branch shouldn't be computed, this can be a useful tool.

```cs
int numberOfMessages = GetMessageCount();

for(int i = 0; i < numberOfMessages; i++) {
  string message = GetMessage();

  if(message == "IGNORE") {
    continue;
  } else {
    Console.WriteLine("You have received: " + message);
  }
}  
```

The above snippet outlines a case where given a message that specifies `"IGNORE"`, the program will go to the next message. Contrary to what the previous snippet was doing where it broke out the loop.



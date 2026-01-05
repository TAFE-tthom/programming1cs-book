# Nested Control Flow

Sometimes we need our programs to make many different decisions where simply just one condition isn't enough. Let's take the following snippet of code as an example.

```cs
int temperature = 21;
bool raining = true;

if(temperature > 30) {
    Console.WriteLine("It is very hot today!");
    if(raining == true) {
        Console.WriteLine(" and it is also humid!");
    }
} else if(temperature <= 30 && temperature >= 22) {
    Console.WriteLine("It is a little bit warm today");
} else if(temperature == 21) {

    Console.WriteLine("Perfect beach weather!");
    if(raining == true) {
        Console.WriteLine(" but it is raining :(");
    }
} else if(temperature < 21 && temperature > 13) {
    Console.WriteLine("It is a little cool today!");
} else if(temperature <= 13 && temperature > 6) {
    Console.WriteLine("It is quite cold!");
} else {

    Console.WriteLine("Absolutely freezing!");
    if(raining == true) {
        Console.WriteLine(" and it is snowing!");
    }
}
```

Given two variables and a few different ranges we want to check for, we can observe how complicated our nested if statements can be. For each temperature case, there is an additional case for `raining` where it will output in addition to the usual statement.

💻 Experiment with the snippet above and change the `temperature` and `raining` variables. Note down the different combinations you can construct and the different branches the code can go down.

## Switch Statements

While `switch` statements aren't the solution to addressing the complex we observe when we have heavily nested if statements, they are another control flow mechanism.

The most suitable time to use a `switch` statement is if we are aware of a fixed number of values that an expression could match. Some suitable examples would be:

* Days of the week
* Suits for play cards
* Fixed number of teams

However, it is probably still better to use if statements to handle number ranges.

```cs
switch (dayofweek)
{
    case "Monday":
        break
    case "Tuesday":
        break
    case "Wednesday":
        break
    case "Thursday":
        break
    case "Friday":
        break
    case "Saturday":
        break
    case "Sunday":
        break
}
```

There is the ability to enable fallthrough (not using `break`), which means the code that is used for more than one case will be grouped. However **fallthrough** with switch statements is usually considered a bad practice and can result in unintentional issues.

## Nesting Loops

Similarly with if statements, we can also nest loops within each other. This can be any combination and you may gravitate towards one construct over another based on the data you have to use.

We'll use the snippet below to examine nested loops.

```cs

for(let i = 0; i < 3; i++)
{
    for(let j = 0; j < 3; j++)
    {
      Console.WriteLine(i, j);
    }
}
```

We can observe that for every `i`, we do 3 iterations of the inner loop (`j`). The output we will observe is the following.

```
0 0
0 1
0 2
1 0
1 1
1 2
2 0
2 1
2 2 
```


## How many layers can we go?

We are not really limited with how much we can nest control-flow blocks within each other. However it can be difficult to comprehend and likely could be simplified.

It is advised to consider if you **need** that additional loop or if you are overcomplicating it. It is usually advisable to go through a scenario on paper when solving the problem and write down the steps you took 🖊️.



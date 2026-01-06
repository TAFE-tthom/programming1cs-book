# Standard Library Collections and ADTs


An abstract data type (ADT) is a type that is an aggregation of other types. However, we may have an ADT that only has methods and no data.

* Primitive types is not an ADT
* Reference types is is an ADT

Our applications will require certain needs in storing and organising data. Collections or aggregate types allow us to store data in the appropriate objects.

For a few examples for collections and ADTS.

* A school contains students
* A stage has performers
* Running times from athletes for race
* TV Shows on netflix

Within this section, we will looking at Lists, Sets and Maps.

## Standard Library - List Data Structures

The most common list type that is used is an `List`. This comes from the convenience of having a resizable Array. However there also exists `Queue`, `Stack` and `LinkedList`.

These collections are under the `System.Collections.Generic` namespace. While you can access the `System.Collections` version, it will contain datatypes that do not leverage **generics**.

*Why would we use a list?*

Let’s take a look at this problem and see if we can solve it just using arrays.

*“We want to **store all input** given by the user in a collection and be
able to review it.”*

Storing all the input does present a slight problem here. The issue with arrays is that we need to declare the number of elements **ahead of time**. While it is solvable with **Arrays** it isn't without creating a pattern and managing memory itself.

Here comes the use of `List`.

```cs
List<string> list = new List<string>();

list.Add("First String!");
list.Add("Second String!");
list.Add("Woof!!");

list.Remove(1);

list.Set(1, "Meow");

Console.WriteLine(list.get(0));
Console.WriteLine(list.get(1));
```

What you will observe here is that we do not need to specify the size with a list. We are able continually add elements to the list and **internally** it will resize itself.

**TODO: Provide diagram**

## Standard Library - Sets and Maps

C#, similar to Java and other programming languages does boast a large data structure collection. Included in this are two common data structures, **HashSet** and **Dictionary**.

The two types operate similarly because they treat one of the types stored as a **Key**. If you have taken a **databases** class, you can think of this as a primary key, which means it is unique.

Let's take a look at the snippet of a **Dictionary** here.

```cs
Dictionary<string,int> seats = new Dictionary<string,int>();

seats.Add("Bus", 30);
seats.Add("Car", 5);

seats["Bike"] = 1;
seats["Truck"] =  2;

seats.Remove("Truck");

Console.WriteLine(seats.Get("Bike"));
Console.WriteLine(seats["Car"]);
```


The above snippet contains a fair anount to unpack. However it will provide some insight into how we can use these types.

* `Add` is a mechanism to insert data under a particular key. The first line where we add an element (`seats.Add("Bus", 30);`), demonstrates that given the string `"Bus"`, we associate it with the value `30`,

* However, we are able to use indexers to perform this as well. `["Bike"] = 1`, is demonstrating the same logic as above.

* `Remove` is removing the value associated with `Truck`.

* `Get` and `[key]` is similar, however to note, if the indexer is used in conjunction with assignment it will operate similar to `Add`.

 




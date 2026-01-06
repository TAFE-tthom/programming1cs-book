# Exercises

The following exercises will be constructing a set of different data structures. I would encourage the reader to build the data structures and use the test cases provided in the task set.

## Tasks

### 1. Associative Array

You have been tasked with constructing an associative array. An associative array is a kind of map. However, with this question, you have a constraint you will need to adhere to.

You cannot use Objects as a Map to create an associative array, you need to complete the following class `ArrayMap` and the methods:

* `ArrayMap()` - Creates an empty `ArrayMap`. Should initialise a key array and a values array.

* `static WithArrays(keys, values)` - Creates an ArrayMap with the keys and values arrays.

* `GetElement(key)` - Gets an element by its key, if the key exists within the `ArrayMap`, you will need to return the value associated with that key.

* `SetElement(key, value)` - Sets an element, associated to key. When `getElement` is called with the same key, it should return it.

* `RemoveElement(key)` - Removes and returns the value from the `ArrayMap`

* `Keys()` - Gets the array of keys

* `Values()` - Gets the array of values

Make sure each of these methods are implemented correctly.


### 2. Linked List

Welcome to building your first data-structure! This isn't going to be an easy task but will be a rewarding one, nonetheless.

If you inspect `LinkedList.cs`, you will notice that there are two classes within this file.

* `LinkedList`

    A linkedlist is a container class, it will hold onto
    the first node in the list when initialised.

    The list will first node (Root) will be set to null
    as it will not contain any items until Append is called.



* `Node` - This stores the data and the link to the next node.

#### What do you need to implement?

You will need to implement the following methods:

* `Add(int item)` - Adds to the end of the LinkedList

* `Prepend(int item)` - Adds to the front of the LinkedList, replaces the value at Root

* `Get(index)` - Checks to see if the index is within bounds, if it is, searches for the element in the list that matches its
logical index.

If index is < 0 or >= Size, the method should return null.

* `Remove(int index)` - Checks to see if the index is within bounds, if it is, searches for the element in the list that matches its logical index. If it does, it will remove the node from the list and stitch the previous node to the one after.

Method should return the value held by the node that was removed.

If index is < 0 or >= Size, the method should return null.


### 3. Queue

You have been tasked with implementing a queue data structure that will hold
onto integers given to it.

#### What is a queue?

"Have you ever linked up at a bank or for food?"

The quote above does some lifting in providing a real-life scenario where one may have interacted with a queue. Within code, the analogy works as well but
we need to isolate the structures involved.

You have been given a class called `Queue` which will need the following
operations implemented:

* `Enqueue(v)` - This adds `v` to the end of the queue, as if they just lined up

* `Dequeue()` - Removes the first integer from the queue, if no one has lined up, it
    should return null

* `Peek()` - Returns the integer at the head of the queue, it does not remove them but
    you will get an idea what the number is before removing it. null is returned if the
    queue is empty.

* `Size()` - Returns the number of integers currently in the queue.


You will also have a few constraints to adhere by, since some collections and data structures
are already available from JS standard library, you will need to implement this assuming
you do not have access to these types.

* You aren't allowed any other data-structure such as JS's built-in Array type or other data structures that would trivialise the problem.

* It must implement the methods above


## Tasks with Test Cases

Please refer to the following code repository for the exercises <https://github.com/TAFE-tthom/programming1-cs>.

Attempt the following exercises in the **Week09** folder.

Ensure you run `dotnet build` and `dotnet test` while your shell is in the directory of a particular question. Run `dotnet test` to check to see if your solution works as specified.


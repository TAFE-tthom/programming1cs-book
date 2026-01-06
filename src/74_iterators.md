# Iterators and Iterables

The thing to note here is that all these components relate to an interesting pattern called an `iterator`.

An iterator is object that allows reading through a collection. It maintains state within the collection and where to go next. A collection itself could be something where it generates or retrieves input on demand.

Generally, iterators have their place in any domain where a series or sequence can be an expression.

This can include:

* Database Cursors
* Line Retrieval from a file
* Data Streams
* Data Structure Traversals (Trees, Graphs, Grids...)
* ... everywhere

## What is the advantage here?

We get to maintain state during the iteration, linking back to our time-complexity of our `get(...)` call on a linkedlist, this can be **O(n)**. This will result in the following code being O(n^2).

```cs
LinkedList list = new LinkedList();
// adds

for(int i = 0; i < list.size(); i++) {
    const e = list.get(i);
    // other things
}
    
```

Maintaining the state of the cursor means we aren't always restarting from the beginning and to find the **next** element.

The current iterators that have been outlined isn't the same as what Javascript expects but it at least breaks down the different components of it.

If we want to use iterators, we need to leverage `IEnumerable` and `IEnumerator`. To do this, we want a collection implement `IEnumerable` which will provide access to a method which returns an iterator and we then have `IEnumerator` which defines the methods for an iterator.

```cs
class RandomIntegerEnumerator : IEnumerator<int> {

  private Random random;
  private int step;
  private int endpoint;
  private int currentNumber;

  public RandomIntegerEnumerator(int step, int endpoint)
  {
    this.step = step;
    this.endpoint = endpoint;
    this.random = new Random();
  }

  public int Current
  {
    get { return currentNumber; }
  }
  
  public void Reset() {
    step = 0;
  }

  public bool MoveNext() {
    this.currentNumber = random.next(1, 100);
    bool isDone = step >= endpoint;

    step++;
    
    return isDone;
  }
  
}

class RandomIntegerIter : IEnumerable<int> {

  private int endpoint = 1;
  
  public RandomIntegerIter(int n)
  {
    this.endpoint = n;
  }

  public IEnumerator<int> GetEnumerator()
  {
    return new RandomIntegerEnumerator(1, endpoint);
  }
}   
```

Afterwards, we are able to construct a the above iterator and use it in a `foreach` loop.

```cs
int randiter = new RandomIntegerIter(5);

foreach(var i in randiter) {
  Console.WriteLine(i);  
}
```

We can then observe the following output from the snippet above.

```
14
49
48
23
66
```

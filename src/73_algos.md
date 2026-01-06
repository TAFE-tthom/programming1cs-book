# Sorting and Searching

## Linear Search

At this point in time, you have likely already written a linear search. However, the term can throw people who simply know it as a 'search'. For example, if you have built a search function that starts at the beginning of an array and checks each element in order.

```
def search(items, object)

  let n = items.length
  let match is None
  

  for i in 0..n
    if object is items[i]

      match = items[i]
      break

  return match
```

The pseudo-code above 

## Binary Search

Binary search is a different kind of search algorithm that reduces the search time substantially. While it can seem like a little more complicated searching algorithm, it exhibits a property where it can eliminate half the viable entries to check on each iteration.

However, for the algorithm to eliminate half, it requires the data to be sorted.

Lets take a look at the following pseudo-code.

```
def binarySearch(items, object)

  let lower = 0
  let upper = items.length - 1

  let match is None

  while lower <= upper

    mid = lower + floor((upper - lower) / 2)

    if items[mid] < object
      lower = mid + 1
    else if items[mid] > object
      upper = mid - 1
    else
      match = items[mid]
      break

  return match
  
```

The `lower` and `upper` variables are used to give a bound and also assist with computing the `mid`point of the remaining elements to check.

If the `items[mid]` is either less or greater than what we are searching, then we need to exclude the segments of that list. If it matches, we have found our object.


## Selection Sort

Selection sort is a sorting algorithm that encompasses many familiar concepts. It is composed of a `getMin` (or `getMax`) function and the sorting algorithm simply running it against all elements and swapping with the current element in focus.

It is a rudimentary but effective sorting algorithm.

```
def getMinIndex(items, index, length)

  let offset = index + 1

  let currentIndex = index
  let current = items[index]

  for i in offset..length
    if current > items[i]
      currentIndex = i
      current = items[i]

  return currentIndex


def selectionSort(items)

  for i in 0..n
    let minIndex = getMinIndex(items, i, n)
    swap(items, minIndex, i)
  
```

We can observe the `getMinIndex` function being used to find the smallest element. What occurs here is that selection sort is going through each position in the array and finding the next suitable element.


## Merge Sort

This kind of sort is a little tricky and relies on having a good understanding of recursion. The advantage of merge sort when compared to selection sort is that is also a stable sort but is also substantially faster.

```
def mergeSort(items, lower, upper)

  let elements = ((upper - lower) + 1);

  if elements <= 1
    return
  else if elements == 2
      if items[lower] > items[upper]
        swap(items, lower, upper)
  else

    let half = floor((lower + upper) / 2)

    mergeSort(items, lower, half)

    mergeSort(items, half+1, upper)

    merge(items, lower, half, end)
```

The above outlines the recursive calls and the two base cases. If the number elements to work on is either 1 or 2, it will simply perform a swap if the order is incorrect (if 2) or just return (if <= 1).

The recursive cases is where it will call `merge`. `merge` call can seem a little confusing as it is inputting 3 index points and just items. However, we are manipulating the `items` array directly.

```
def merge(items, lower, half, upper)


  let length = upper - lower;
  let tempspace = array(length)
  
  let endA = half
  let endB = upper
  let idxA = lower
  let idxB = half+1

  for i in 0..length

    if idxA >= endA
      tempspace[i] = items[idxB]
      idxB = idxB + 1

    else if idxB >= endB
      tempspace[i] = items[idxA]
      idxA = idxA + 1  

    else if items[idxA] <= items[idxB]
      tempspace[i] = items[idxA]
      idxA = idxA + 1
    else
      tempspace[i] = items[idxB]
      idxB = idxB + 1

  for i in 0..length
    items[lower+i] = tempspace[i]
```

The merge step is used to take two portions of a the array and re-order the elements. Given that the elements are sorted respective to their own portion, the portion themselves does not need to check elements that have already been check, however we need to get portions that are separate. 

# Sorting Algorithms
![GitHub last commit](https://img.shields.io/github/last-commit/cattoyt/csbook?path=src%2Fpaper_2%2F2.3%2Fsorting_algorithms.md&label=Last%20updated)

## Bubble sort
The bubble sort is a simple O(n^2) algorithm that sorts a dataset by iterating through the data with two pointers, switching the values where necessary.

### Example
Consider the following array:  
``[4, 2, 6, 8, 1, 3, 55, 9]``  
1. This array is considered 'unsorted'. To sort the array using Bubble sort, create two pointers pointing at index 0 and index 1.

```
 [4, 2, 6, 8, 1, 3, 55, 9]
  ⇑  ⇑
  p1 p2
```

2. Since the value that *p1* is pointing to is lower than the value at *p2*, the sorting algorithm will switch the two values around.

```
 [2, 4, 6, 8, 1, 3, 55, 9]
  ⇑  ⇑
  p1 p2
```
3. The two pointers are then incremented.

```
 [2, 4, 6, 8, 1, 3, 55, 9]
     ⇑  ⇑
     p1 p2
```
4. Since the two values dereferenced by the pointers are in the correct order, no switch is made. The pointers can be incremented.
```
 [2, 4, 6, 8, 1, 3, 55, 9]
        ⇑  ⇑
        p1 p2
```
5. These two are also in the correct order, so no switch is made, then the pointers are incremented:
```
 [2, 4, 6, 8, 1, 3, 55, 9]
           ⇑  ⇑
           p1 p2
```

6. These two are not in the correct order, so a switch is made.
```
 [2, 4, 6, 1, 8, 3, 55, 9]
           ⇑  ⇑
           p1 p2
```

7. This loop continues until one pass is finished. (Skipped as an exercise for the reader.)
```
 [2, 4, 6, 1, 3, 8, 9, 55]
                    ⇑  ⇑
                    p1 p2
```

> [!IMPORTANT]
> Notice how the data isn't sorted at this point. This is because bubble sort **often requires more than one pass** to sort the data.  
> This is what causes the algorithm to have an O(\\(n^2\\)) time complexity, since on average the algorithm will make one addition pass per additional element.

8. After a few passes, eventually we will have a sorted dataset.
```
 [1, 2, 3, 4, 6, 8, 9, 55]
                    ⇑  ⇑
                    p1 p2
```

Once there is a pass where no elements are switched, then the algorithm returns.

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                # Swap if the element found is greater than the next element
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break  # If no two elements were swapped, the array is sorted
    return arr
```

## Insertion Sort
- Insertion sort is a simple sorting algorithm that builds the final sorted list one item at a time.
- It is much like sorting playing cards in your hands. The list is split into a sorted part and an unsorted part.
- Elements from the unsorted part are picked one by one and placed at the correct position in the sorted part. 

### Example
Suppose you have the list `[5, 3, 8, 4, 2]`.
1. Start with the second element (3). Compare it with the first element (5). Since 3 is less than 5, insert 3 before 5. The list now looks like `[3, 5, 8, 4, 2]`.
2. Move to the third element (8). Compare it with the elements in the sorted part (3 and 5). Since 8 is greater than both, it stays in its place.
3. Move to the fourth element (4). Compare it with the elements in the sorted part (3, 5, and 8). Since 4 is greater than 3 but less than 5, insert 4 between 3 and 5. The list now looks like `[3, 4, 5, 8, 2]`.
4. Finally, move to the last element (2). Compare it with the elements in the sorted part (3, 4, 5, and 8). Since 2 is less than all of them, insert 2 at the beginning. The final sorted list is `[2, 3, 4, 5, 8]`.

```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
    
        # Move elements of arr[0..i-1], that are greater than key, to one position ahead
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    
    return arr
```


## Quicksort
Quicksort is a **divide and conquer** algorithm that has an average time complexity of O(\\(nlogn\\)). It works by choosing a 'pivot' element from the dataset, then moving it to the , and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.  

The sub-arrays are then sorted recursively.

>[!NOTE]
> [This link](https://www.hackerearth.com/practice/algorithms/sorting/quick-sort/visualize/) may be helpful. I will not provide an example, since I don't want this book to be impossibly big.
> The next section will rely on the visualiser with array size 10. Use those settings to follow along.
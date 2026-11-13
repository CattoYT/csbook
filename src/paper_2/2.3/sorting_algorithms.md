# Sorting Algorithms
![GitHub last commit](https://img.shields.io/github/last-commit/cattoyt/csbook?path=src%2Fpaper_2%2F2.3%2Fsorting_algorithms.md&label=Last%20updated)

## Bubble sort
The bubble sort is a simple O(\\(n^2\\)) algorithm that sorts a dataset by iterating through the data with two pointers, switching the values where necessary.

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

## Merge Sort
Merge sort is a **divide and conquer** algorithm that has an average time complexity of O(\\(nlogn\\)). It works by recursively splitting the dataset into halves until each sub-array contains a single element, and then merging those sub-arrays back together in sorted order.

### Example
Suppose you have the list `[5, 3, 8, 4, 2]`.
1. Split the list into two halves: `[5, 3]` and `[8, 4, 2]`.
2. Recursively split each half until you have single-element lists: `[5]`, `[3]`, `[8]`, `[4]`, `[2]`.
3. Merge the single-element lists back together in sorted order:
   - Merge `[5]` and `[3]` to get `[3, 5]`.
   - Merge `[8]` and `[4] to get `[4, 8]`.
   - Merge `[4, 8]` and `[2]` to get `[2, 4, 8]`.
4. Finally, merge `[3, 5]` and `[2, 4, 8]` to get the fully sorted list `[2, 3, 4, 5, 8]`.

```python
def merge_sort(array):

    # Base case: if the array has 0 or 1 elements,
    # it is already sorted, so return it.
    if len(array) <= 1:
        return array

    # Find the middle position of the array
    middle = len(array) // 2

    # Split the array into two halves
    left_half = array[:middle]
    right_half = array[middle:]

    # Recursively sort each half
    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)

    # Merge the two sorted halves together
    return merge(left_half, right_half)


def merge(left, right):
    # Create an empty list to store the sorted values
    result = []

    # Continue while both lists contain elements
    while len(left) > 0 and len(right) > 0:

        # Compare the first element of each list
        if left[0] <= right[0]:

            # Add the smaller element to the result
            result.append(left[0])

            # Remove the element that has been added
            left.pop(0)

        else:
            # Add the smaller element from the right list
            result.append(right[0])

            # Remove the element that has been added
            right.pop(0)

    # Add any remaining elements from the left list
    result.extend(left)

    # Add any remaining elements from the right list
    result.extend(right)

    # Return the fully sorted list
    return result
```


## Quicksort
Quicksort is a **divide and conquer** algorithm that has an average time complexity of O(\\(nlogn\\)). It works by choosing a 'pivot' element from the dataset, then moving it to the , and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.  

The basic steps are:
1. Pick an element from the array as a pivot.
2. Partition the array into two sub-arrays: elements less than the pivot and elements greater than the pivot.
3. At this point, only the pivot will be in the correct position. So, we recursively apply the same logic to the left and right sub-arrays, and do this again until the whole list is sorted.

In the best case, the data should split evenly at each stage, for maximum efficiency. In the worst case, the pivot is always the smallest or largest element, which results in the benefit of divide and conquer being lost and a time complexity of O(\\(n^2\\)).

Given that the array is not sorted, picking an optimal pivot is quite challenging. Approaches taken are:
- Take the first or last element
- Take the middle element
- Take a random element
- Take the median of the first, middle, and last elements
- Median of medians: take the median of several median sets taken from within the array: this is the most efficient when sorting, but also takes more processing overhead, which detracts from the overall efficiency of the algorithm.

### Example
Suppose you have the list `[5, 3, 8, 4, 2]` and you choose `4` as the pivot.
1. Partition the list into two sub-arrays: `[3, 2]` (elements less than `4`) and `[5, 8]` (elements greater than `4`).
2. Now, recursively apply the same logic to the left sub-array `[3, 2]` and the right sub-array `[5, 8]`.
3. For the left sub-array `[3, 2]`, choose `2` as the pivot. Partition it into `[ ]` (elements less than `2`) and `[3]` (elements greater than `2`). Now, the left sub-array is sorted as `[2, 3]`.
4. For the right sub-array `[5, 8]`, choose `5` as the pivot. Partition it into `[ ]` (elements less than `5`) and `[8]` (elements greater than `5`). Now, the right sub-array is sorted as `[5, 8]`.
5. Finally, combine the sorted left sub-array `[2, 3]`, the pivot `4`, and the sorted right sub-array `[5, 8]` to get the fully sorted list `[2, 3, 4, 5, 8]`.

When partitioning, you can use pointers. The pointers start at the left and right ends of the array, moving towards each other. When the left pointer finds an element greater than the pivot and the right pointer finds an element less than the pivot, they are swapped. This continues until the pointers cross, at which point the partitioning is complete.

Starting with `[5, 3, 8, 4, 2]` and pivot `4`:
1. left stops at 5; right stops at 2. Swap → [2, 3, 8, 4, 5]
2. left stops at 8; right stops at 4. Swap → [2, 3, 4, 8, 5]
3. The pointers have crossed, so this partition is done.


```python
def quicksort(items):
    def partition(left, right):
        pivot = items[(left + right) // 2]
        i, j = left, right

        while i <= j:
            while items[i] < pivot:
                i += 1
            while items[j] > pivot:
                j -= 1

            if i <= j:
                items[i], items[j] = items[j], items[i]
                i += 1
                j -= 1

        return i

    def sort(left, right):
        if left >= right:
            return

        split = partition(left, right)
        sort(left, split - 1)
        sort(split, right)

    sort(0, len(items) - 1)
    return items
```

# Search Algorithms
![GitHub last commit](https://img.shields.io/github/last-commit/cattoyt/csbook?path=src%2Fpaper_2%2F2.3%2Fsearch_algorithms.md&label=Last%20updated)

> [!NOTE]
> 🚧 This page is currently being worked on. Please check back soon.
## Linear Search
- Linear search is a simple search algorithm that checks every element in a list until the desired element is found or the list ends.
- The time complexity of linear search is O(n), where n is the number of elements in the list. This means that in the worst case, the algorithm will have to check every element in the list before finding the desired element or determining that it is not present.
- Linear search is easy to implement and does not require the list to be sorted.


Here is an example implementation in python:
```python
def linear_search(arr, target):
    # Traverse through the list
    for i in range(len(arr)):
        # If the target is found, return the index
        if arr[i] == target:
            return i
        # Repeat
        
    # (indicating that the target is not in the list)
    return -1

input_list = [1, 3, 5, 7, 9]
target_value = int(input("Enter the target value to search for: "))
result = linear_search(input_list, target_value)
if result != -1:
    print(f"Target found at index: {result}")
else:
    print("Target not found in the list.")

```

## Binary Search
- Binary search is a _divide and conquer_ search algorithm that repeatedly divides the search interval in half to find the target value. 
- The time complexity of binary search is O(log n), where n is the number of elements in the list. This means that the algorithm can quickly narrow down the search space, making it much faster than linear search for large lists.
- Binary search requires the list to be sorted before it can be applied. If the list is not sorted, the algorithm will not work correctly.

Here is an example implementation in python:
```python
def binary_search(arr, target):
    # Initialise the low and high pointers
    low = 0
    high = len(arr) - 1 
    # Continue searching as long as low <= high
    while low <= high:
        # Calculate the middle index
        mid = (low + high) // 2
                
        # If the target is at the middle, return its index
        if arr[mid] == target:
            return mid
        # If the target is smaller than the middle element, search the left half
        elif arr[mid] > target:
            high = mid - 1
        # If the target is larger than the middle element, search the right half
        else:
            low = mid + 1
        # Repeat
            
    # If the target is not found, return -1
    return -1

input_list = [1, 3, 5, 7, 9]
target_value = int(input("Enter the target value to search for: "))
result = binary_search(input_list, target_value)
if result != -1:
    print(f"Target found at index: {result}")
else:
    print("Target not found in the list.")
```

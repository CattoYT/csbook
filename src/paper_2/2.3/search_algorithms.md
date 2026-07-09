# Search Algorithms
![GitHub last commit](https://img.shields.io/github/last-commit/cattoyt/csbook?path=src%2Fpaper_2%2F2.3%2Fsearch_algorithms.md&label=Last%20updated)

## Linear Search
The linear search algorithms searches an dataset in a __linear fashion__.
This means that it checks the first element, then the second, third, etc.

Therefore, linear search has an average (and worst case) time complexity of O(n), since the number of steps needed to search successfully grows at the same rate as the dataset grows.

> [!NOTE]
> It is good to know the best case time complexities of algorithms. For linear search this is O(1)
> This is because the best case is the searched for element being the first in the dataset.

### Pros of Linear Search
- Easy to implement
- Quick for small datasets

### Cons of Linear Search
- Inefficient (very slow with big datasets)



## Binary Search
Binary search is far more efficient than linear sort, but has more overhead and the dataset must be sorted before the search as a __prerequisite__.

Binary sort works by selecting the midpoint of the dataset, and then comparing it to the __target value__ to see if it is higher or lower.
Since the dataset is sorted (let's say, in ascending order for the purpose of explanation) if the midpoint is higher than the target value, we know that the target value is below the midpoint, and vice versa if the target value is higher than the midpoint.

As a result of this, we can disregard the half of the dataset that we know does not contain the target value, and keep the other half as a __subset__ (aka a subarray if you are searching an array, which you most likely will be).

Therefore, the algorithm continues to disregard half of the dataset with each pass, until only one item is left.
If the dataset contains the target value, this last item will be the target value.


The average time complexity of binary search is O(log n) because it halves the dataset with every pass, and so the number of steps needed to search grows logarithmically as the size of the dataset increases.
The best case is O(1), where the midpoint is the target value

### Pros of Binary Search
- Efficient

### Cons of Binary Search
- Less efficient with small lists
- Bit more complex to implement



## Binary Tree Search

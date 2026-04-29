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

## Quicksort
Quicksort is a **divide and conquer** algorithm that has an average time complexity of O(\\(nlogn\\)). It works by choosing a 'pivot' element from the dataset, then moving it to the , and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.  

The sub-arrays are then sorted recursively.

>[!NOTE]
> [This link](https://www.hackerearth.com/practice/algorithms/sorting/quick-sort/visualize/) may be helpful. I will not provide an example, since I don't want this book to be impossibly big.
> The next section will rely on the visualiser with array size 10. Use those settings to follow along.
# **Introduction To The Binary Search Algorithm**

Binary search is a method for locating an element in a sorted linear data structure by repeatedly dividing the search space based on specific criteria until the target element is found.

For binary search to function effectively, the data must be sorted in a specific order.

Binary search can also be tailored to meet specific needs. For example, instead of searching for an exact match, you could look for any number greater than a given target in an array of integers.

To better understand binary search, consider this relatable example: Imagine you want to resume a movie you were previously watching but don’t remember the exact spot where you stopped. If you use linear search, you'd have to re-watch the entire movie from the beginning until you recognize where you left off. If the stopping point is near the end, this method can be very inefficient.

In contrast, binary search takes advantage of the movie's order. You could fast-forward to the middle of the film. If you find that you stopped there, you can simply continue watching. If you've not reached that point yet, you can eliminate the latter half of the movie from your search space, making the middle your new end. If you find that you've passed the middle, you know that searching in the first half is unnecessary, so you can adjust your new beginning to the middle and repeat the process.

This approach reduces the search space with each check, making it faster and more efficient than linear search.

<video src="bs-anim.mp4"></video>

Binary search can be implemented either recursively or iteratively. In this tutorial, we'll focus on the iterative implementation.

## **Algorithm**

1. Initialize a variable `n` to the size of the data structure.
2. Initialize two variables, `start` and `end`. Set `start` to `0` and `end` to the last index (`n - 1`) of the data structure.
3. Iterate while `start` is less than or equal to `end`:
   - Calculate a new variable `middle` as the sum of `start` and `end` divided by `2`.
   - Check if the data at index `middle` equals the target data. If it does, return `True`.
   - If the data at index `middle` is greater than the target data, shift `end` to `middle - 1`. Otherwise, shift `start` to `middle + 1`.
4. If the target data wasn't found, return `False`.

## **Implementation**

```python
def binary_search(arr, target):
    n = len(arr)
    start, end = 0, n - 1

    while start <= end:
        middle = (start + end) // 2

        if arr[middle] == target:
            return True

        if arr[middle] > target:
            end = middle - 1
        else:
            start = middle + 1

    return False
```

This function accepts two parameters: an array `arr` and the value to search for, `target`. It initializes two pointers, `start` and `end`, to represent the current search boundaries. The function iteratively checks if the middle element of the current search range is equal to `target`. If a match is found, the function immediately returns `True`. If the middle element is greater than `target`, the search continues in the left half of the array; otherwise, it continues in the right half. If no match is found after the search space is exhausted, the function returns `False`, indicating that the `target` is not present in the array.

## **Complexity Analysis**

- **Time Complexity**: The time complexity of the binary search algorithm is `O(log n)`, where `n` is the number of items in the data structure. In the worst case, the algorithm repeatedly divides the search space in half, which results in a logarithmic number of iterations.
- **Space Complexity**: The space complexity is `O(1)` because the algorithm only uses a constant amount of extra memory regardless of the input size, as it doesn't require any additional data structures to hold elements.

## **Advantages Of Binary Search**

1. Much faster than linear search for large datasets due to `O(log n)` time complexity.
2. Requires fewer comparisons, making it more efficient in sorted data structures.
3. Reduces the search space significantly with each iteration, leading to faster results.
4. Can be easily implemented both iteratively and recursively.
5. Suitable for large datasets where performance is critical, especially in sorted arrays.

## **Disadvantages Of Binary Search**

1. Requires the data to be sorted beforehand, which may incur additional overhead.
2. More complex to implement compared to linear search, particularly for recursive versions.
3. Not suitable for small datasets where linear search may be more straightforward.
4. Overhead of calculating midpoints and managing indices can slow down performance in certain contexts.
5. If the data structure frequently changes, maintaining the sorted order can be inefficient.

## **Binary Search use Cases**

1. Searching for an element in a large sorted array or list.
2. Implementing search functionalities in databases and search engines.
3. Efficiently finding the insertion point for a new element in a sorted list.
4. Solving problems that require searching for a threshold value or condition in a sorted dataset.
5. Used in algorithms and data structures, such as binary search trees and heaps.

## **Practical Problems on Binary Search**

- [Search Insert Position](https://leetprep.io/problems/35)
- [First Bad Version](https://leetprep.io/problems/278)
- [Search in Rotated Sorted Array](https://leetprep.io/problems/33)
- [Koko Eating Bananas](https://leetprep.io/problems/875)
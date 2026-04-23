# **INTRODUCTION TO ARRAYS**

In this course, we will explore the array data structure, a fundamental building block for many other data structures. This course is divided into the following sections:

1. **Definition of an Array**
2. **Array Representation in Memory**
3. **Types of Arrays**
4. **Array Operations**
5. **Advantages of Arrays**
6. **Disadvantages of Arrays**
7. **Applications of Arrays**
9. **Practice Problems on Arrays**

## **Definition of an Array**

An array is a **linear data structure** that holds a collection of elements, all of the same **data type**. These elements are stored in **contiguous** (adjacent) memory locations, meaning they are placed next to each other in memory. Arrays allow for easy access to elements using their **index**, making it efficient to retrieve or update values.

## **Array Representation in Memory**

In an array, elements are stored in consecutive memory locations, ensuring that each element is placed directly after the previous one. When an array is initialized, memory is allocated sequentially, allowing for quick access and efficient manipulation. Arrays use **zero-based indexing**, meaning the first element is stored at index 0. This contiguous layout makes arrays highly performant for tasks involving indexed retrieval of elements.

[Diagram Here]

## **Types of Arrays**

There are two main types of an array:

1. Fixed/Static Array
2. Dynamic Array

**Fixed/Static Array**: A **fixed** or **static** array is an array whose size is determined at the time of initialization and cannot be altered afterward. It is initialized with a predefined number of elements, which means the total amount of data expected must be known in advance.

For example, if you want to store the 26 letters of the English alphabet, a static array of size 26 can be used since you already know the number of items.

However, if the size of the data is uncertain:

- If you declare a larger size than needed, it leads to memory waste.
- If you declare a smaller size, you will run into memory overflow issues or exceptions.

Therefore, static arrays are best suited for scenarios where the number of elements is fixed and known.

```python
// initialization of a fixed/static array of integers
import array

arr = array.array('i', [1, 2, 3, 4, 5])
```

**Dynamic Array**: A **dynamic array** is more flexible. It doesn’t require specifying the size during initialization, as it automatically resizes to accommodate new elements. As more data is added, the array grows dynamically to fit the required size.

This is ideal for situations where the amount of data is unknown, like in a registration system where the number of users is not predetermined. A dynamic array prevents both over-allocation (wasting memory) and under-allocation (running out of space).

```python
// initialization of a dynamic array of integers

arr = []
```

**Key points on FIxed and Dynamic Arrays**

- **Use Fixed Arrays**: When the size of the data is known beforehand, like storing the alphabet or specific dataset.
- **Use Dynamic Arrays**: When the size of the data is unknown or may change during runtime.
- **Performance**: Fixed arrays typically offer faster access and lower memory overhead, whereas dynamic arrays offer flexibility at the cost of occasional resizing operations.
- **Memory Management**: Fixed arrays use a predefined block of memory, while dynamic arrays may allocate memory in chunks as needed.

[Diagram or Animation Here]

Arrays can also vary based on their dimensions. The two main types are:

1. **One-Dimensional Array (1-D Array)**
2. **Two-Dimensional Array (2-D Array)**

1. **One-Dimensional Array (1-D Array)**

   A **1D array** is the simplest form of an array, where elements are stored in a single linear sequence. Each element is accessed by its index, and memory is allocated in a contiguous block.

   In memory, the elements of a 1D array are stored sequentially, where each element’s memory address is computed based on its index. If the base address of the array is `BaseAddress`, the address of an element `arr[i]` can be calculated as:

   `Address of arr[i] = Base Address + (i × Size of each element)`

   

2. ### **Two-Dimensional Array (2-D Array)**

   A **2D array** is an array of arrays, where elements are arranged in rows and columns, forming a matrix-like structure. Each element can be accessed using two indices: one for the row and one for the column.

   In memory, a 2D array can be stored in **row-major order** or **column-major order**.

   - **Row-Major Order**: All elements of the first row are stored first, followed by the elements of the second row, and so on. The address of an element at `arr[i][j]` can be calculated as:

     `Address of arr[i][j]= Base Address + ((i × Number of columns) + j) × Size of each element`

     

   - **Column-Major Order**: All elements of the first column are stored first, followed by the elements of the second column, and so on. The address of an element at `arr[i][j]` can be calculated as:

     `Address of arr[i][j] = Base Address + ((j × Number of rows) + i) × Size of each element`

   

   ### **Key Points on Array Dimensions**

   - **1D Array**: Suitable for storing data in a single sequence, like a list of numbers or items.
   - **2D Array**: Ideal for matrix-like structures or grids, such as tables or images.
   - **Row-Major vs. Column-Major**: The memory layout (row-major or column-major) impacts how efficiently data is accessed, especially in large datasets or for matrix operations.

## **Array Operations**

Arrays support several basic operations:

1. **Traversing an Array**

2. **Searching an Array**

3. **Inserting into an Array**

4. **Deleting from an Array**

   

### **Traversing an Array**

Traversal involves visiting each element of the array one by one, typically using a loop. It’s the simplest operation where we simply iterate through the array.

```python
# Array traversal
arr = ['dog', 'cat', 'wolf', 'lion', 'snake']
n = len(arr)

for index in range(n):
    animal = arr[index]
    print(animal)
```

In this code, we loop through the array `n` times (where `n` is the length of the array). In each iteration, the element at the current index is accessed.

- Time Complexity: `O(n)` (because we visit each element once)
- Space Complexity: `O(1)` (since no additional memory is used, aside from the iterator variable)



### **Searching an Array**

 Searching means looking for a specific item within an array. To do this, we traverse the array and check each element to see if it matches the item we're searching for.

```python
# Searching an array
# Let's check if 'cat' exists in our array
arr = ['dog', 'cat', 'wolf', 'lion', 'snake']
n = len(arr)

for index in range(n):
    animal = arr[index]
    if animal == 'cat':
        print('cat exists!')
        break
```

In this example, the program iterates over the array and checks each item to see if it matches `'cat'`. Once it finds `'cat'`, it prints a message and stops.

Time Complexity:

- Best Case: `O(1)` (if the element is found at the beginning)
- Worst Case: `O(n)` (if the element is found at the end or doesn't exists)

Space Complexity: `O(1)` (since we only use a few variables)

In the worst case, the array must be traversed entirely, such as when searching for an item like `'snake'` (last element) or an item that doesn’t exist, like `'bat'`.

*Note*: Searching time can be improved with algorithms like Binary Search if the array is sorted or follows a particular order.



### **Inserting into an Array** 

Inserting an element involves adding a new value at a specified index. This can involve shifting the existing elements to create space.

**Algorithm**

1. Traverse the array in reverse, starting from the last index down to the target index.
2. Shift each element by one position to the right.
3. Insert the new element at the target index.

Example: Inserting `'bat'` at index `0` in a fixed-size array.

```python
arr = ['dog', 'cat', 'wolf', 'lion', 'snake']
n = len(arr)

# Inserting 'bat' at index 0
arr.insert(0, 'bat')
print(arr)
```

Time Complexity:

- Best Case:`O(1)` (if inserting at the end of the array)
- Worst Case: `O(n)` (if inserting at the beginning, as all elements must be shifted)

Space Complexity:

- Best Case: `O(1)` (if no additional memory is needed for shifting)
- Worst Case: `O(n)` if using an array that dynamically resizes, requiring a copy of the array.

### **Deleting from an array**

Deleting an element involves removing the value at a specified index and shifting the remaining elements to close the gap.

**Deletion Algorithm:**

1. Starting from the index after the target, shift all elements one position to the left.
2. This fills the gap left by the deleted element.

Example: Deleting `'dog'` from index `0`:

```python
arr = ['dog', 'cat', 'wolf', 'lion', 'snake']
n = len(arr)

# Deleting 'dog' from index 0
del arr[0]
print(arr)
```

Time Complexity:

- Best Case: `O(1)` (if deleting the last element)
- Worst Case: `O(n)` (if deleting the first element, as all subsequent elements must be shifted)

Space Complexity:

- Best Case: `O(1)` (if no additional memory is used)
- Worst Case: `O(1)` (since we only manipulate the original array)



## **Advantages of Arrays**

1. Direct access to elements using indices for quick retrieval.
2. Efficient traversal due to contiguous memory storage.
3. Memory efficiency when the size of the array is known in advance.
4. Simple to implement in most programming languages.
5. Cache-friendly memory layout that improves performance in data processing.

## **Disadvantages of Arrays**

1. Fixed size that must be declared at initialization, limiting flexibility (for fixed/static arrays).
2. Insertion and deletion operations can be time-consuming due to element shifting.
3. Potential wastage of memory if the array size is overestimated.
4. Inefficient for frequently resizing or reordering elements.
5. Searching is inefficient (`O(n)`) unless the array is sorted.

## **Applications of Arrays**

1. Building more complex data structures, such as heaps, hash tables, and trees.
2. Representing matrices in scientific computing and graphics.
3. Storing and organizing collections of data in various applications.
4. Serving as the base structure for sorting and searching algorithms.
5. Representing multi-dimensional data such as tables, grids, or images.

## **Bonus**

![](61R6Nb69w9L._AC_UF1000,1000_QL80_.jpg)

Imagine the wardrobe above as an array, with each hanger representing a specific index. If all hangers are occupied, it resembles a fully populated array. When looking for a particular trouser, if you know its exact position, you go directly to it. If not, you check each trouser one by one until you find the right one.

After finding and removing it, you must shift each trouser after it one hanger forward to maintain order—similar to deleting from an array. However, if the trouser is on the last hanger, no shifts are needed.

For insertion, let's assume we have more free hangers at the end, if we want to place a new trouser in the middle, the hanger is already occupied, we have to shift each subsequent trouser one hanger back. This process is only avoided if we just place the new trouser in the next empty hanger at the end, making it simpler to add without shifting.

## **Practical Problems on Arrays**

- [Contains Duplicate](https://leetprep.io/problems/217)
- [Plus One](https://leetprep.io/problems/66)
- [Two Sum](https://leetprep.io/problems/1)

Explore more from the recommendations of any of those problems on **LeetPrep**.
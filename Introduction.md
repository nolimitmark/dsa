# **Introduction**

In this course, we'll explore Big O notation and complexity analysis. Whether you're preparing for an interview or aiming to enhance your coding skills, this course will provide a solid foundation for understanding these crucial concepts.

We'll explain ideas using real-life examples to facilitate quicker comprehension. Before diving into the main sections, let's start by defining what an algorithm is:

An algorithm can be simply defined as a predefined set of steps to accomplish a specific task. For example, consider an algorithm for searching for a particular book on a bookshelf:

1. Start at the first row.
2. Check each book in this row. If you find the target book, stop the search.
3. If not, move to the next row and repeat step 2 until you have searched all the rows.

This simple algorithm outlines a method for locating a book. Now, if someone asks how long it might take to find a book on a different shelf, you might reply:

"The time required depends on the number of rows and the book's location. In the worst case, where the book isn't present, you'll need to check every book. However, if you're lucky and find it in the first row, it won't take long at all."

Instead of providing such a lengthy explanation, as a programmer, you can succinctly express the time it takes using **Big O** notation.

## **Definition of TIme and Space Complexity**

**Time Complexity**: Time complexity measures how long an algorithm takes to complete as a function of the input size. It represents the number of operations or steps an algorithm performs.

Example: In our bookshelf scenario, the time complexity depends on the number of rows and the book's location. In the worst case, where the book isn't present, you'll need to check every book. However, if you find it in the first row, it won't take long at all.

**Space Complexity**: Space complexity measures the amount of memory an algorithm uses as a function of the input size. It represents the additional space required by the algorithm, beyond the space needed to store the input.

Example: Let's consider a modified version of our book-finding algorithm where we write down the titles of all the books we've checked:

1. Start with an empty list for checked books.
2. Begin with the first row.
3. For each book in the current row:
   - If it's the target book, stop the search.
   - If not, add its title to our list of checked books.
4. If not found, move to the next row and repeat step 3 until all rows have been searched.

In this case, the space complexity would depend on the number of books we check before finding the target. In the worst case, we might end up writing down all the book titles, requiring space proportional to the total number of books.

##### **In Conclusion**

Time complexity focuses on how long the search takes, while space complexity considers the memory used by our list of checked books.

## **What Is Big O Notation?**

Big O notation is the mathematical language we use to describe the running time of an algorithm (time complexity) or the amount of memory it consumes (space complexity).

it describes the worst-case scenario in terms of time or space complexity.

### **Why is Big O Notation Important?**

Big O notation is crucial for evaluating and improving the performance of algorithms. It offers a clear way to understand how an algorithm behaves as the input size increases, which can greatly impact efficiency in real-world applications. Here are some notable importance of Big O:

1. It provides a concise way to describe how an algorithm's runtime or space usage grows with input size.
2. It allows for easy comparison of the efficiency of different algorithms.
3. It helps in selecting the most efficient algorithm for a given task.
4. It guides programmers in optimizing their code for better performance.
5. It ensures scalable solutions by predicting algorithm performance as input size increases.

**Common Big O Classifications**

- O(1) - Constant Time/Space Complexity
- O(log n) - Logarithmic Time/Space Complexity
- O(n) - Linear Time/Space Complexity
- O(n log n) - Linearithmic Time/Space Complexity
- O(n^2) - Quadratic Time/Space Complexity
- O(2^n) - Exponential Time/Space Complexity
- O(n!) - Factorial Time/Space Complexity

In the context of algorithm analysis, `n` typically refers to the input size. Let's clarify this using our bookshelf example:

- `n` represents the size of the problem or the amount of data the algorithm needs to process.
- In our bookshelf scenario, `n` could represent the total number of books on the shelf.

<img src="https://external-preview.redd.it/rQb83JE8O_rv33x39mn_kLEDJvynWbgiXlclw8szS3o.jpg?width=1080&crop=smart&auto=webp&s=f9e95ca7cabc7b231c2c26abeddc226d1b9a8bd9" style="zoom: 50%;" />

Now, let's walk through each of these classifications in more detail.

##### <u>O(1) - Constant Time/Space Complexity:</u> 

- **In terms of time**: An algorithm with **O(1) time complexity** always takes the same amount of time to execute, regardless of the input size. This means that no matter how large the input grows, the runtime remains constant. For example, consider a situation where you know exactly which row and which specific position (column) the target book is located on the shelf. No matter how large the shelf is or how many books it holds, you will always go directly to the correct spot, retrieving the book in constant time. Below are some examples:

  1. Accessing an element in an array by its index (e.g., `arr[3]`).
  2. Checking if a number is even or odd (e.g., `num % 2 == 0`).

  

- **In terms of space**: For **O(1) space complexity**, the algorithm uses a fixed amount of memory, independent of the input size. This means it doesn't need additional space that scales with the size of the input. Below are some examples:

  1. Initializing a fixed number of variables, such as `int x = 10;`.
  2. Swapping two variables using a temporary variable (e.g., `temp = a; a = b; b = temp;`).

  

##### <u>O(log  n) - Logarithmic Time/Space Complexity:</u> 

- **In terms of time**: An algorithm with **O(log n) time complexity** increases in runtime logarithmically as the input size grows. This means that even if the input size doubles, the time taken only increases by a fixed amount.

  In our bookshelf example, if the books are arranged alphabetically, instead of checking each book one by one, you can go directly to the middle of the shelf. If the target book is before the middle, you focus on the first half; if it’s after, you focus on the second half. By doing this, you eliminate half of the books with each step, repeating the process until you find the book. Below are some examples:

  1. Binary search in a sorted array or list.
  2. Adding an item to a Min Heap (Priority Queue).

  

- **In terms of space**: For **O(log n) space complexity**, the algorithm requires a logarithmic amount of memory in relation to the input size. This typically occurs in recursive algorithms that divide the problem space, where the depth of recursion is logarithmic. Below are some examples:

  1. Storing the call stack in a recursive binary search algorithm.
  2. Using a data structure like a balanced binary search tree, which maintains a logarithmic height relative to the number of elements stored.

##### <u>O(n) - Linear Time/Space Complexity:</u> 

- **In terms of time**: An algorithm with **O(n) time complexity** increases its runtime in direct proportion to the size of the input. If the input size doubles, the time taken will also double.

  In our bookshelf example, if the books are stored randomly (not alphabetically) and you have no information about where the target book is, you’d need to start at the first book and check each one sequentially until you find it. The more books there are, the longer it will take, because you might have to check every single book. In the worst-case scenario, the book could be at the very last position, making the search take `O(n)` time. While it's possible to find the book in the first position, which would take constant time `O(1)`, Big O notation focuses on the worst-case performance of an algorithm, hence the `O(n)` classification. Below are some examples:

  1. Searching for a specific value in an unsorted list.
  2. Traversing all elements in a data structure.

  

- **In terms of space**: For **O(n) space complexity**, the memory usage grows linearly with the size of the input. This typically happens when an algorithm needs to store or process each input element. For instance, imagine keeping a record of every book you’ve checked on a separate shelf as you search for the target book. The larger the shelf, the more space you’ll need. Below are some examples:

  1. Creating a copy of an array.
  2. Storing all nodes during a tree traversal.



##### <u>**O(n log n) - Linearithmic Time/Space Complexity:**</u>

- **In terms of time**: An algorithm with **O(n log n) time complexity** grows more quickly than linear time `O(n)` but less quickly than quadratic time `O(n²)`. This happens when the algorithm performs `O(log n)` work for each of the `n` input elements.

  Returning to our bookshelf example, imagine that instead of searching for a single book, you need to sort the entire shelf alphabetically. First, you could repeatedly divide the books into smaller sections, similar to our binary search process, and then rearrange each section in order. Sorting algorithms like merge sort and quicksort follow this pattern: dividing the problem in halves (`log n` steps) and then processing each element (`n` operations). Below are some examples:

  1. Merge Sort and Quick Sort algorithms.
  2. Heapsort, which organizes elements into a heap and sorts them.

- **In terms of space**: For **O(n log n) space complexity**, the memory usage grows in a similar linearithmic manner, typically due to recursive operations or temporary storage needed during the process. For example, sorting a large collection of books might require extra space to hold temporary groups of books while you sort each smaller section. Below are some examples:

  1. The space used by recursive merge sort, where temporary arrays are created to store subarrays.
  2. The additional space required for building heaps during heapsort.

  

##### <u>**O(n²) - Quadratic Time/Space Complexity:**</u>

- **In terms of time**: An algorithm with **O(n²) time complexity** grows quadratically with the input size, meaning that if the input size doubles, the time taken increases fourfold (`n × n`). This typically happens when the algorithm performs `n` operations for each of the `n` input elements.

  Using the bookshelf example, imagine you not only need to search through each row of the shelf but also compare every book with every other book in the shelf. This would significantly increase the time it takes as you check all pairs of books. A common example of this is a **nested loop**, where for each element, you iterate over the entire set again. Below are some examples:

  1. Bubble sort, where for each element in an array, the algorithm compares it with every other element.
  2. Checking for duplicate pairs in an unsorted list using two nested loops.

- **In terms of space**: For **O(n²) space complexity**, the memory usage increases quadratically with the input size. This occurs when the algorithm needs to store every pair or combination of elements. In our bookshelf analogy, imagine needing to store information about every possible comparison between books. Below are some examples:

  1. Storing a 2D matrix where both dimensions grow with `n`, such as for graph adjacency matrices.
  2. Generating all pairs of elements from a set and storing them.

##### <u>**O(2ⁿ) - Exponential Time/Space Complexity:**</u>

- **In terms of time**: An algorithm with **O(2ⁿ) time complexity** grows exponentially with the size of the input. This means that with each additional input element, the time required to process it doubles. Exponential algorithms are highly inefficient for large inputs, as the runtime increases rapidly.

  Below are some examples:

  1. Solving the traveling salesman problem using brute-force search, where you try every possible route.
  2. Recursive algorithms that explore all possible combinations, such as solving the subset sum problem.

- **In terms of space**: For **O(2ⁿ) space complexity**, the memory usage also doubles with each additional input element. This typically happens when an algorithm needs to store all possible solutions or combinations.

  Below are some examples:

  1. Storing all subsets of a set in memory.
  2. Storing intermediate states in a brute-force solution to a combinatorial problem.

In the context of the bookshelf example, Imagine you want to find all possible combinations of books from a collection of 3 books: [Book A, Book B, Book C]. The possible combinations include empty sets, single books, pairs, and all books together. The combinations are:

1. []
2. [Book A], [Book B], [Book C]
3. [Book A, Book B], [Book A, Book C], [Book B, Book C]
4. [Book A, Book B, Book C]

For 3 books, there are 2^3 =8 possible combinations. Now, if you add another book (Book D), the total number of combinations doubles to 2^4 = 16, because for every existing combination, you can either include or exclude Book D.

In this scenario, **the time complexity is O(2ⁿ)** because the number of combinations grows exponentially with each additional book. For every new book added, the number of operations doubles, which leads to an exponential increase in the time required to generate all combinations.

Similarly, **the space complexity is also O(2ⁿ)** because you need to store each combination. As the number of books grows, the space required to store all combinations also doubles, resulting in exponential space usage.

##### <u>**O(n!) - Factorial Time/Space Complexity:**</u>

- **In terms of time**: An algorithm with **O(n!) time complexity** grows at an incredibly fast rate as the input size increases. For every additional element, the number of operations multiplies by all previous elements, leading to a factorial explosion in runtime. This is one of the most inefficient complexities and is rarely feasible for large inputs

  Below are some examples:

  1. Generating all possible permutations of a set (e.g., rearranging books or numbers in every possible order).
  2. Solving the traveling salesman problem using brute-force, where you try every possible route for a set of cities.

- **In terms of space**: For **O(n!) space complexity**, the memory usage grows at the same factorial rate. This happens when an algorithm needs to store every possible configuration, permutation, or state as part of the solution.

  Below are some examples:

  - Storing all possible permutations of a set.
  - Keeping track of all paths in a brute-force solution to a complex problem, such as trying every combination of a large dataset.

  Imagine you want to find all possible ways to arrange 3 books on a shelf: [Book A, Book B, Book C]. The different possible arrangements (permutations) are:

  1. [Book A, Book B, Book C]
  2. [Book A, Book C, Book B]
  3. [Book B, Book A, Book C]
  4. [Book B, Book C, Book A]
  5. [Book C, Book A, Book B]
  6. [Book C, Book B, Book A]

  For 3 books, there are 3! = 6 different arrangements. Now, if you add a fourth book (Book D), the number of possible arrangements grows to 4! = 24, because each new book can be placed in every position of the existing permutations.

  In this case, **the time complexity is O(n!)** because the number of permutations (arrangements) grows factorially with the number of books. For every new book, you need to place it in all possible positions relative to the previous books, leading to a rapid explosion in the number of operations required.

  Similarly, **the space complexity is also O(n!)** because you need to store each possible arrangement. As the number of books increases, the number of permutations grows factorially, and so does the space required to store all of them.

### **What are the rules of using Big O notation?**

When working with Big O notation, there are a few simple rules to keep in mind:

1. **Focus on the biggest factor**: We only care about the part of the algorithm that grows the fastest as the input size increases. This is called the "dominant term." For example, if an algorithm takes `n^2 + n` steps, we focus on `n^2` because it grows faster than `n`.
2. **Ignore constant factors**: Multiplying by constants doesn't change the Big O classification. So, if an algorithm takes `3n` or `10n` steps, we just simplify it to `O(n)` because the constants (3 or 10) don't matter when the input size gets large.
3. **Focus on the worst-case scenario**: Big O notation is usually used to describe the worst-case performance of an algorithm. This gives us an upper bound, showing the maximum time or space the algorithm will take, no matter what.

### **Types of Complexity**

1. **Best Case Complexity**: This is the fastest possible time an algorithm can take, assuming everything goes perfectly.

   **Example**: If the target book is in the first row and first position on the shelf, you find it immediately. This would be a **best-case scenario** with **O(1)** time complexity, as it takes just one step to find the book.

2. **Average Case Complexity**: This refers to the time an algorithm takes on average, assuming all inputs are equally likely.

   **Example**: On average, the target book might be located somewhere in the middle of the shelf. In this case, you would likely need to search through half the books before finding it, making the **average case complexity** around **O(n/2)**, which simplifies to **O(n)**.

3. **Worst Case Complexity**: This represents the longest possible time the algorithm might take, usually considered when analyzing performance.

   **Example**: If the target book is at the very end of the shelf (last row and last position), you'd have to search through every single book before finding it. This is the **worst-case scenario**, with **O(n)** time complexity, where `n` is the number of books.

4. **Expected Complexity**: This is the expected time an algorithm will take based on the probability of different inputs.

   **Example**: If you have prior knowledge that books you commonly search for are usually in the first few rows, you can adjust the **expected complexity** based on these probabilities. If books are more likely to be near the start, the **expected complexity** might be closer to **O(1)**, but if they're equally spread out, it would still be **O(n)**.

### **Analyzing TIme and Space Complexity of some simple algorithms**

#### **Example 1:**

Let's define a function that takes in two inputs and returns the sum of those inputs:

```python
def add(x, y):
 answer = x + y
 return answer
```

**<u>Time Complexity</u>**

- The only operation here is the addition (`x + y`), which is a single, constant-time operation. The time it takes to add two numbers does not depend on their size, but rather on the number of operations required.
- Assigning the result of `x + y` to the variable `answer` is also a constant-time operation.
- Returning the result is another constant-time operation.

Thus the overall Time Complexity will be `O(1)`

**<u>Space Complexity</u>**

- The function takes two input variables, `x` and `y`. These inputs already exist in memory when passed to the function, so no additional space is needed for them.
- Inside the function, we create a variable `answer` to store the result of `x + y`. This variable requires constant space, regardless of the size of the inputs.

Thus the overall Space Complexity will be `O(1)`

#### **Example 2:**

Let's modify our Example 1 a bit by passing an array of integers to the function and returning the sum of all integers in the array.

```python
def add(nums):
 n = len(nums)
 answer = 0
 for num in nums:
     ans += num
 return answer
```

<u>**Time Complexity**</u>

- The function loops through each element in the input array `nums` exactly once.
- If the array has `n` elements, the loop runs `n` times, and each addition operation inside the loop takes constant time (`O(1)`).
- Therefore, the total time complexity is proportional to the number of elements in the array.

Thus the overall Time Complexity will be `O(n)`

<u>**Space Complexity**</u>

- The function uses a constant amount of extra space: the variable `answer` to store the sum and the variable `n` to store the length of the array.
- The input array `nums` is passed to the function, but it is not duplicated or modified in terms of memory allocation.

Thus the overall Space Complexity will be `O(1)`

#### **Example 3:**

Let's examine a function that takes an array of strings called `balls`, where each string represents a ball's color (either "red," "blue," or "green"). The goal is to check if any color appears more than once and print those repeated colors.

For instance, given `balls = ["blue", "red", "blue", "green", "red"]`, the function should print "blue" and "red".

```python
def containsDuplicate(balls):
 n = len(balls)
 for i in range(n):
     for j in range(n):
         if i == j:
             continue  # We don't want to compare a ball to itself
         if balls[i] == balls[j]:
             print(balls[j])
```

**<u>Time Complexity</u>**

- The function uses two nested loops to compare every pair of elements. For an array of `n` elements, the outer loop runs `n` times, and for each iteration, the inner loop also runs `n` times.
- This results in a time complexity of `O(n^2)` since we are comparing every ball with every other ball.

Thus the overall Time Complexity will be `O(n^2)`

<u>**Space Complexity**</u>

- The function uses a constant amount of extra space, such as the loop variables `i` and `j`, but no additional data structures or memory are used that scale with the input size.

Thus the overall Space Complexity will be `O(1)`

Now, we can improve the time complexity of the above program with the cost of some extra space, now imagine if as you pick a ball, you put it in a basket, and as you iterate through the balls, you check if such color of ball is already in the basket, if it is, you know it's a duplicate hence print the color.

```python
def containsDuplicate(balls):
    basket = set()  # represents the basket
    for ball in balls:
        if ball in basket:  # check if ball is already in the basket
            print(ball)  # print the duplicate ball
        else:
            basket.add(ball)  # put the ball in the basket

```

<u>**Time Complexity**:</u>

- We iterate through the array of `n` elements exactly once, which gives us a time complexity of `O(n)`.
- Checking if an element is in the set (our "basket") and adding an element to the set both take constant time, `O(1)`.

Thus, the overall **Time Complexity** is `O(n)`.

<u>**Space Complexity**:</u>

- The set `basket` will store up to `n` unique balls in the worst case, so the space complexity is proportional to the size of the input.

Thus, the overall **Space Complexity** is `O(n)`.

## **Conclusion**

In the upcoming courses, we'll build upon this foundation of Big O notation and complexity analysis. We'll explore various data structures such as arrays, linked lists, trees, and graphs, analyzing their efficiencies for different operations. We'll also delve into fundamental algorithms for searching, sorting, and graph traversal, applying our knowledge of time and space complexity to understand their performance characteristics.
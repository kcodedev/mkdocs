# 🔍 Binary Search Tutorial

## 🔍 What is Binary Search?

Binary search is an efficient searching algorithm that works on sorted arrays. It repeatedly divides the search interval in half, comparing the target value to the middle element and narrowing down the search space until the target is found or the interval is empty.

Think of it like looking up a word in a dictionary - you open to the middle and decide whether to look in the first or second half based on alphabetical order.

---

## 📋 The Binary Search Algorithm

### 👣 Step-by-Step Process

1. **Start with the entire sorted array** as the search interval (left = 0, right = length - 1)
2. **Calculate the middle index** of the current interval
3. **Compare** the middle element with the target value
4. **If they match**, you've found the target - return the middle index
5. **If target is less than middle element**, search the left half (update right = middle - 1)
6. **If target is greater than middle element**, search the right half (update left = middle + 1)
7. **Repeat** steps 2-6 until the target is found or the interval is empty (left > right)

---

### 👁️ Visual Example

Let's search for the number `7` in this sorted list: `[1, 3, 4, 5, 7, 9, 11]`

```
Position:  0  1  2  3  4  5  6
Values:   [1, 3, 4, 5, 7, 9, 11]
Start:     ↑                 ↑
          left              right

Step 1: Middle = (0+6)/2 = 3, value = 5
        Is 5 == 7? No, 5 < 7, so search right half
        New interval: left=4, right=6

Step 2: Middle = (4+6)/2 = 5, value = 9
        Is 9 == 7? No, 9 > 7, so search left half
        New interval: left=4, right=4

Step 3: Middle = (4+4)/2 = 4, value = 7
        Is 7 == 7? Yes! Found at position 4
```

---

Now let's search for `8` in the same list:

```
Position:  0  1  2  3  4  5  6
Values:   [1, 3, 4, 5, 7, 9, 11]
Start:     ↑                 ↑

Step 1: Middle = 3, value = 5
        5 < 8, search right: left=4, right=6

Step 2: Middle = 5, value = 9
        9 > 8, search left: left=4, right=4

Step 3: Middle = 4, value = 7
        7 < 8, search right: left=5, right=4
        Interval empty (5 > 4), target not found
```

---

## 🐍 Building the Python Solution

### 1️⃣ Version 1: Iterative Implementation

Let's start with the most common iterative version:

```python
def binary_search_iterative(arr, target):
    """
    Iterative binary search implementation
    Returns the index if found, -1 if not found
    Array must be sorted in ascending order
    """
    left, right = 0, len(arr) - 1

    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Test the function
numbers = [1, 3, 4, 5, 7, 9, 11]
result = binary_search_iterative(numbers, 7)
print(f"Found 7 at position: {result}")  # Output: Found 7 at position: 4
```

### 2️⃣ Version 2: Recursive Implementation

This version shows the recursive approach:

```python
def binary_search_recursive(arr, target, left=None, right=None):
    """
    Recursive binary search implementation
    Array must be sorted in ascending order
    """
    if left is None:
        left = 0
    if right is None:
        right = len(arr) - 1

    if left > right:
        return -1

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)

# Test the function
numbers = [1, 3, 4, 5, 7, 9, 11]
result = binary_search_recursive(numbers, 7)
print(f"Found 7 at position: {result}")  # Output: Found 7 at position: 4
```

### 3️⃣ Version 3: With Tracing for Learning

This version shows each step of the search process:

```python
def binary_search_with_trace(arr, target):
    """
    Binary search with detailed tracing output
    Useful for understanding the algorithm's steps
    """
    left, right = 0, len(arr) - 1
    step = 0

    while left <= right:
        step += 1
        mid = (left + right) // 2

        print(f"Step {step}: Checking position {mid}, value {arr[mid]}")
        print(f"         Interval: [{left}, {right}]")

        if arr[mid] == target:
            print(f"Found {target} at position {mid} after {step} steps!")
            return mid
        elif arr[mid] < target:
            print(f"         {arr[mid]} < {target}, searching right half")
            left = mid + 1
        else:
            print(f"         {arr[mid]} > {target}, searching left half")
            right = mid - 1
        print()

    print(f"{target} not found after {step} steps")
    return -1

# Test with tracing
numbers = [1, 3, 4, 5, 7, 9, 11]
print("Searching for 7:")
result = binary_search_with_trace(numbers, 7)
```

## 💪 Practice Exercises

### 1️⃣ Exercise 1: Basic Iterative Implementation
Write a binary search function that finds the position of a target in a sorted list.

```python
def binary_search_exercise(arr, target):
    """Implement binary search iteratively"""
    # Your code here

# Test
test_list = [2, 4, 6, 8, 10, 12, 14]
result = binary_search_exercise(test_list, 8)
print(f"Found 8 at position: {result}")  # Should be 3
```

### 2️⃣ Exercise 2: Count Occurrences
Write a function that counts how many times a target appears in a sorted list using binary search to find bounds.

```python
def count_occurrences_binary(arr, target):
    """Count occurrences using binary search for efficiency"""
    # Your code here (advanced - find leftmost and rightmost, then count)

# Test
test_list = [1, 2, 2, 2, 3, 4, 5]
result = count_occurrences_binary(test_list, 2)
print(f"2 appears {result} times")  # Should be 3
```

## 📚 Complete Example: Library Book Search

Here's a practical example using binary search to find a book in a sorted library catalog:

```python
def find_book_position(book_titles, target_title):
    """
    Find a book's position in a sorted library catalog using binary search

    Args:
        book_titles: Sorted list of book titles
        target_title: Title of the book to find

    Returns:
        int: Position of the book, or -1 if not found
    """
    left, right = 0, len(book_titles) - 1

    while left <= right:
        mid = (left + right) // 2

        if book_titles[mid] == target_title:
            return mid
        elif book_titles[mid] < target_title:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Example usage
library_catalog = [
    "1984", "Brave New World", "Dune", "Ender's Game",
    "Foundation", "Neuromancer", "Snow Crash", "The Hobbit"
]

book_to_find = "Neuromancer"
position = find_book_position(library_catalog, book_to_find)
if position != -1:
    print(f"'{book_to_find}' is at position {position} in the catalog")
else:
    print(f"'{book_to_find}' not found in the catalog")
```

## 📝 Summary

Binary search is a powerful algorithm that:

- **Requires sorted data** - the array must be sorted for the algorithm to work
- **Highly efficient** - O(log n) time complexity, much faster than linear search for large datasets
- **Divides and conquers** - repeatedly halves the search space
- **Works with any comparable data type** - as long as the data can be ordered

While binary search is much more efficient than linear search, it requires the data to be sorted first. For small datasets or unsorted data, linear search might still be preferable. Binary search is a fundamental algorithm that demonstrates the power of divide-and-conquer problem solving.
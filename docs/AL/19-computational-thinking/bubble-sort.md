# 🔄 Bubble Sort Tutorial

## 🔄 What is Bubble Sort?

Bubble sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

Think of it like bubbles rising to the surface - larger elements "bubble" up to their correct positions with each pass through the data.

---

## 📋 The Bubble Sort Algorithm

### 👣 Step-by-Step Process

1. **Start from the beginning** of the array
2. **Compare** each pair of adjacent elements
3. **Swap** them if they are in the wrong order (first > second)
4. **Continue** this process for each pair in the array
5. **Repeat** the entire process for the next pass, but ignore the last element (it's already in place)
6. **Stop** when no swaps are needed in a pass (array is sorted)

---

### 👁️ Visual Example

Let's sort this array: `[5, 3, 8, 4, 2]`

```
Initial: [5, 3, 8, 4, 2]

Pass 1:
Compare 5>3: swap → [3, 5, 8, 4, 2]
Compare 5<8: no swap → [3, 5, 8, 4, 2]
Compare 8>4: swap → [3, 5, 4, 8, 2]
Compare 8>2: swap → [3, 5, 4, 2, 8]

Pass 2:
Compare 3<5: no swap → [3, 5, 4, 2, 8]
Compare 5>4: swap → [3, 4, 5, 2, 8]
Compare 5>2: swap → [3, 4, 2, 5, 8]
Compare 5<8: no swap → [3, 4, 2, 5, 8]

Pass 3:
Compare 3<4: no swap → [3, 4, 2, 5, 8]
Compare 4>2: swap → [3, 2, 4, 5, 8]
Compare 4<5: no swap → [3, 2, 4, 5, 8]
Compare 5<8: no swap → [3, 2, 4, 5, 8]

Pass 4:
Compare 3>2: swap → [2, 3, 4, 5, 8]
Compare 3<4: no swap → [2, 3, 4, 5, 8]
Compare 4<5: no swap → [2, 3, 4, 5, 8]
Compare 5<8: no swap → [2, 3, 4, 5, 8]

Final: [2, 3, 4, 5, 8] (no swaps in pass 4, sorting complete)
```

---

## 🐍 Building the Python Solution

### 1️⃣ Version 1: Basic Implementation

Let's start with the simplest version:

```python
def bubble_sort_basic(arr):
    """
    Basic bubble sort implementation
    Sorts the array in ascending order
    """
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

# Test the function
numbers = [5, 3, 8, 4, 2]
bubble_sort_basic(numbers)
print(f"Sorted array: {numbers}")  # Output: Sorted array: [2, 3, 4, 5, 8]
```

### 2️⃣ Version 2: With Swap Counter

This version counts the number of swaps made:

```python
def bubble_sort_with_count(arr):
    """
    Bubble sort that counts the number of swaps
    Useful for understanding the algorithm's efficiency
    """
    n = len(arr)
    total_swaps = 0

    for i in range(n):
        swaps_in_pass = 0
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swaps_in_pass += 1
                total_swaps += 1
        print(f"Pass {i + 1}: {swaps_in_pass} swaps")
        if swaps_in_pass == 0:
            break  # Array is already sorted

    print(f"Total swaps: {total_swaps}")
    return arr

# Test with counting
numbers = [5, 3, 8, 4, 2]
sorted_numbers = bubble_sort_with_count(numbers)
print(f"Sorted array: {sorted_numbers}")
```

### 3️⃣ Version 3: Optimized with Early Termination

This version stops early if the array becomes sorted:

```python
def bubble_sort_optimized(arr):
    """
    Optimized bubble sort with early termination
    Stops when no swaps occur in a pass
    """
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        if not swapped:
            break  # No swaps in this pass, array is sorted

# Test the optimized version
numbers = [5, 3, 8, 4, 2]
bubble_sort_optimized(numbers)
print(f"Sorted array: {numbers}")  # Output: Sorted array: [2, 3, 4, 5, 8]
```

### 4️⃣ Version 4: Working with Different Data Types

Bubble sort works with any comparable data type:

```python
def bubble_sort_generic(arr):
    """
    Generic bubble sort that works with any comparable data type
    """
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

# Test with strings
words = ["zebra", "apple", "banana", "cherry"]
bubble_sort_generic(words)
print(f"Sorted words: {words}")

# Test with mixed comparable types (if needed)
mixed = [3.14, 1, 2.71, 0, 42]
bubble_sort_generic(mixed)
print(f"Sorted mixed: {mixed}")
```

## 💪 Practice Exercises

### 1️⃣ Exercise 1: Basic Implementation
Write a bubble sort function that sorts a list of integers in ascending order.

```python
def bubble_sort_exercise(arr):
    """Implement basic bubble sort"""
    # Your code here

# Test
test_list = [7, 2, 9, 1, 5]
bubble_sort_exercise(test_list)
print(f"Sorted: {test_list}")  # Should be [1, 2, 5, 7, 9]
```

### 2️⃣ Exercise 2: Descending Order
Modify bubble sort to sort in descending order.

```python
def bubble_sort_descending(arr):
    """Sort in descending order using bubble sort"""
    # Your code here

# Test
test_list = [3, 1, 4, 1, 5]
bubble_sort_descending(test_list)
print(f"Sorted descending: {test_list}")  # Should be [5, 4, 3, 1, 1]
```

### 3️⃣ Exercise 3: Count Passes
Write a function that counts how many passes were needed to sort the array.

```python
def bubble_sort_count_passes(arr):
    """Count passes needed for sorting"""
    # Your code here

# Test
test_list = [5, 4, 3, 2, 1]
passes = bubble_sort_count_passes(test_list)
print(f"Needed {passes} passes")  # Should be 4 for reverse sorted
```

### 4️⃣ Exercise 4: Advanced Challenge
Implement bubble sort that can sort a list of tuples by a specific index.

```python
def bubble_sort_by_index(arr, index):
    """Sort list of tuples by specified index"""
    # Your code here

# Test
data = [("Alice", 25), ("Bob", 20), ("Charlie", 30)]
bubble_sort_by_index(data, 1)  # Sort by age
print(f"Sorted by age: {data}")  # Should be [("Bob", 20), ("Alice", 25), ("Charlie", 30)]
```

## 📚 Complete Example: Sorting Student Scores

Here's a practical example using bubble sort to sort student exam scores:

```python
def sort_student_scores(students, scores):
    """
    Sort students by their scores using bubble sort

    Args:
        students: List of student names
        scores: List of corresponding scores

    Returns:
        tuple: (sorted_students, sorted_scores)
    """
    n = len(scores)
    for i in range(n):
        for j in range(0, n - i - 1):
            if scores[j] < scores[j + 1]:  # Sort in descending order (highest first)
                # Swap scores
                scores[j], scores[j + 1] = scores[j + 1], scores[j]
                # Swap corresponding students
                students[j], students[j + 1] = students[j + 1], students[j]

    return students, scores

# Example usage
class_names = ["Alice", "Bob", "Charlie", "Diana", "Eve"]
class_scores = [85, 92, 78, 96, 88]

sorted_names, sorted_scores = sort_student_scores(class_names, class_scores)
print("Students sorted by score (highest first):")
for name, score in zip(sorted_names, sorted_scores):
    print(f"{name}: {score}")
```

## 📝 Summary

Bubble sort is a fundamental sorting algorithm that's:

- **Simple** to understand and implement
- **Stable** - maintains relative order of equal elements
- **In-place** - doesn't require additional memory
- **Adaptive** - can be optimized to stop early when sorted

While bubble sort is easy to understand, it's not efficient for large datasets (O(n²) time complexity). It's best used for educational purposes or small datasets where simplicity is more important than performance.

Remember: The key to bubble sort is the repeated comparison and swapping of adjacent elements, gradually moving larger elements to the end of the array like bubbles rising to the surface.
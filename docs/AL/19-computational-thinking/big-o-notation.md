# 📊 Big O Notation Tutorial

## 📊 What is Big O Notation?

In computer science, Big O notation is used to classify algorithms according to how their run time or space requirements grow as the input size grows.

Think of it like describing how long it takes to complete a task as the amount of work increases - Big O tells us the **"worst-case scenario"** for algorithm performance.

---

## 📋 Understanding Big O Notation

![Big O Complexity Chart](https://miro.medium.com/v2/resize:fit:720/format:webp/1*V7xT-BrEhXKsOLajl1YkNg.png)

---

### Common Big O Complexities

- **O(1)** - Constant time: The algorithm takes the same amount of time regardless of input size
- **O(log n)** - Logarithmic time: Time increases slowly as input size grows
- **O(n)** - Linear time: Time scales directly with input size
- **O(n log n)** - Linearithmic time: Time grows faster than linear but slower than quadratic; common in efficient sorting algorithms
- **O(n²)** - Quadratic time: Time grows rapidly with input size
- **O(2ⁿ)** - Exponential time: Time doubles with each additional input element

---

### 👁️ Visual Comparison

```
Input Size (n)    O(1)    O(log n)    O(n)    O(n log n)    O(n²)
----------------------------------------------------------------------
10                1       3.32        10      33.2          100
100               1       6.64        100     664           10,000
1,000             1       9.97        1,000   9,970         1,000,000
10,000            1       13.3        10,000  133,000       100,000,000
100,000           1       16.6        100,000 1,660,000     10,000,000,000
```

---

## 🔍 Analyzing Our Algorithms

Fill in the table below with the Big O notation for each algorithm we've discussed:

| Algorithm          | Best Case | Worst Case | Average Case |
|--------------------|-----------|------------|--------------|
| Linear Search      |           |            |              |
| Binary Search      |           |            |              |
| Bubble Sort        |           |            |              |
| Insertion Sort     |           |            |              |

---

### 1️⃣ Linear Search - O(n)

**Time Complexity Analysis:**

- **Best Case:** O(1) - Element found at first position
- **Worst Case:** O(n) - Element not found or at last position
- **Average Case:** O(n) - Element found in middle on average

**Why O(n)?**
```python
def linear_search(arr, target):
    for i in range(len(arr)):  # ← This loop runs n times in worst case
        if arr[i] == target:
            return i
    return -1
```
The algorithm must potentially check every element, so time grows linearly with input size.

---

### 2️⃣ Binary Search - O(log n)

**Time Complexity Analysis:**

- **Best Case:** O(1) - Element found at middle position
- **Worst Case:** O(log n) - Element found after maximum divisions
- **Average Case:** O(log n) - Typically found in log n steps

**Why O(log n)?**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:  # ← This loop runs log n times
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
```
Each iteration eliminates half the remaining elements, so search space halves each time.

---

### 3️⃣ Bubble Sort - O(n²)

**Time Complexity Analysis:**

- **Best Case:** O(n) - Already sorted (with optimization)
- **Worst Case:** O(n²) - Reverse sorted
- **Average Case:** O(n²) - Random order

**Why O(n²)?**
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):        # ← Outer loop: n times
        for j in range(n-i-1): # ← Inner loop: up to n times
            if arr[j] > arr[j+1]:
                swap(arr[j], arr[j+1])
```
Nested loops create n×n comparisons in worst case.

---

### 4️⃣ Insertion Sort - O(n²)

**Time Complexity Analysis:**

- **Best Case:** O(n) - Already sorted
- **Worst Case:** O(n²) - Reverse sorted
- **Average Case:** O(n²) - Random order

**Why O(n²)?**
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):  # ← Outer loop: n times
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:  # ← Inner loop: up to n times
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
```
In worst case, each element may need to be compared with all previous elements.

---

## 🐍 Performance Comparison

### Timing Example

```python
import time
import random

def time_algorithm(algorithm, arr, *args):
    """Time an algorithm's execution"""
    start = time.time()
    result = algorithm(arr.copy(), *args)
    end = time.time()
    return end - start, result

# Test with different input sizes
sizes = [100, 1000, 5000, 10000]

print("Algorithm Performance Comparison")
print("=" * 50)
print(f"{'Size':<8} {'Linear Search':<15} {'Binary Search':<15} {'Bubble Sort':<15} {'Insertion Sort':<15}")
print("-" * 80)

for size in sizes:
    # Create test data
    arr = list(range(size))
    target = random.randint(0, size-1)

    # Time each algorithm
    linear_time, _ = time_algorithm(
        lambda a, t: next((i for i, x in enumerate(a) if x == t), -1),
        arr, target
    )

    binary_time, _ = time_algorithm(
        lambda a, t: binary_search(a, t),
        sorted(arr), target
    )

    bubble_time, _ = time_algorithm(bubble_sort, arr.copy())

    insertion_time, _ = time_algorithm(insertion_sort, arr.copy())

    print(f"{size:<8} {linear_time:<15.6f} {binary_time:<15.6f} {bubble_time:<15.6f} {insertion_time:<15.6f}")
```

---

## 💾 Space Complexity

### Space Requirements

- **Linear Search:** O(1) - Only needs a few variables
- **Binary Search:** O(1) - Only needs a few variables
- **Bubble Sort:** O(1) - In-place sorting, no extra space needed
- **Insertion Sort:** O(1) - In-place sorting, no extra space needed

All our algorithms are space-efficient, using constant extra space regardless of input size.

---

```

## 📚 Complete Example: Algorithm Performance Analyzer

```python
import time
import matplotlib.pyplot as plt

def analyze_algorithms():
    """
    Comprehensive analysis of algorithm performance
    """
    sizes = [100, 500, 1000, 2000, 5000]

    algorithms = {
        'Linear Search': lambda arr, target: next((i for i, x in enumerate(arr) if x == target), -1),
        'Binary Search': lambda arr, target: binary_search(sorted(arr), target),
        'Bubble Sort': lambda arr, _: bubble_sort(arr.copy()),
        'Insertion Sort': lambda arr, _: insertion_sort(arr.copy())
    }

    results = {name: [] for name in algorithms.keys()}

    for size in sizes:
        arr = list(range(size))
        target = size // 2  # Middle element

        for name, func in algorithms.items():
            start = time.time()
            if 'Search' in name:
                func(arr, target)
            else:
                func(arr, None)
            end = time.time()

            results[name].append(end - start)

    # Print results
    print("Algorithm Performance Analysis")
    print("=" * 50)
    print(f"{'Size':<8} {'Linear':<10} {'Binary':<10} {'Bubble':<10} {'Insertion':<10}")
    print("-" * 60)

    for i, size in enumerate(sizes):
        linear = results['Linear Search'][i]
        binary = results['Binary Search'][i]
        bubble = results['Bubble Sort'][i]
        insertion = results['Insertion Sort'][i]

        print(f"{size:<8} {linear:<10.6f} {binary:<10.6f} {bubble:<10.6f} {insertion:<10.6f}")

    # Calculate growth rates
    print("\nGrowth Analysis (relative to n=100):")
    print("-" * 40)
    base_size = sizes[0]
    base_results = {name: times[0] for name, times in results.items()}

    for i, size in enumerate(sizes[1:], 1):
        ratio = size / base_size
        print(f"n = {size} (ratio: {ratio:.1f}x)")

        for name, times in results.items():
            growth = times[i] / base_results[name]
            expected = ratio if 'Linear' in name else (ratio ** 2 if 'Sort' in name else ratio ** 0.5)
            print(f"  {name}: {growth:.2f}x actual vs {expected:.2f}x expected")

if __name__ == "__main__":
    analyze_algorithms()
```

## 📝 Summary

Big O notation is crucial for understanding algorithm efficiency:

- **Linear Search (O(n))**: Simple but slow for large datasets
- **Binary Search (O(log n))**: Fast searching but requires sorted data
- **Bubble Sort (O(n²))**: Simple sorting but inefficient for large arrays
- **Insertion Sort (O(n²))**: Good for small or nearly sorted arrays

**Key Takeaways:**

- Big O describes worst-case growth rate, not exact performance
- Different algorithms suit different scenarios
- Consider both time and space complexity
- Real performance depends on constant factors and input characteristics

Remember: Choosing the right algorithm means understanding both the theoretical complexity (Big O) and practical considerations like data characteristics and available memory.
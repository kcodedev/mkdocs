# List Comprehensions in Python

List comprehensions provide a concise way to create lists in Python. They are often more readable and efficient than using traditional loops. Below are various examples demonstrating different uses of list comprehensions.

## Basic List Comprehension

Create a list of squares for numbers from 0 to 9:

```python
squares = [x**2 for x in range(10)]
print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

## List Comprehension with Condition

Create a list of even numbers from 0 to 9:

```python
evens = [x for x in range(10) if x % 2 == 0]
print(evens)  # Output: [0, 2, 4, 6, 8]
```

## List Comprehension with Multiple Conditions

Create a list of numbers divisible by 2 or 3 from 0 to 9:

```python
div_by_2_or_3 = [x for x in range(10) if x % 2 == 0 or x % 3 == 0]
print(div_by_2_or_3)  # Output: [0, 2, 3, 4, 6, 8, 9]
```

## List Comprehension with Nested Loops

Create a list of all combinations of two lists:

```python
list1 = [1, 2, 3]
list2 = ['a', 'b']
combinations = [(x, y) for x in list1 for y in list2]
print(combinations)  # Output: [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b'), (3, 'a'), (3, 'b')]
```

## List Comprehension with Function Calls

Create a list of lengths of words in a sentence:

```python
sentence = "Hello world from Python"
word_lengths = [len(word) for word in sentence.split()]
print(word_lengths)  # Output: [5, 5, 4, 6]
```

## List Comprehension with String Manipulation

Convert a list of strings to uppercase:

```python
words = ['hello', 'world', 'python']
uppercase_words = [word.upper() for word in words]
print(uppercase_words)  # Output: ['HELLO', 'WORLD', 'PYTHON']
```

## Nested List Comprehension

Create a 3x3 matrix:

```python
matrix = [[i * j for j in range(3)] for i in range(3)]
print(matrix)  # Output: [[0, 0, 0], [0, 1, 2], [0, 2, 4]]
```

## List Comprehension with Conditional Expression

Create a list where even numbers are kept as is, odds are doubled:

```python
numbers = [1, 2, 3, 4, 5]
modified = [x if x % 2 == 0 else x * 2 for x in numbers]
print(modified)  # Output: [2, 2, 6, 4, 10]
```

## List Comprehension for Flattening Lists

Flatten a list of lists:

```python
nested = [[1, 2], [3, 4], [5, 6]]
flattened = [item for sublist in nested for item in sublist]
print(flattened)  # Output: [1, 2, 3, 4, 5, 6]
```

## List Comprehension with Enumerate

Create a list of tuples with index and value:

```python
items = ['a', 'b', 'c']
indexed = [(i, item) for i, item in enumerate(items)]
print(indexed)  # Output: [(0, 'a'), (1, 'b'), (2, 'c')]
```

These examples showcase the versatility of list comprehensions in Python. They can replace many for loops and make code more concise and readable.
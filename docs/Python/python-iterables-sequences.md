# Python Iterables vs Sequences

In Python, understanding the difference between iterables and sequences is crucial for working effectively with data structures and loops.

## What is an Iterable?

An iterable is any object that can be iterated over, meaning you can loop through its elements using a `for` loop or other iteration constructs. Iterables implement the `__iter__` method, which returns an iterator.

Examples of iterables include:
- Lists
- Tuples
- Strings
- Dictionaries
- Sets
- Generators
- Files

```python
# All of these are iterables
my_list = [1, 2, 3]
my_string = "hello"
my_dict = {'a': 1, 'b': 2}

for item in my_list:
    print(item)

for char in my_string:
    print(char)

for key in my_dict:
    print(key, my_dict[key])
```

## What is a Sequence?

A sequence is a specific type of iterable that supports:
- Indexing with `[]`
- The `len()` function
- Slicing

Sequences implement both `__iter__` and `__getitem__` methods, and they have a defined order.

Common sequences include:
- Lists
- Tuples
- Strings
- Range objects

```python
my_list = [1, 2, 3, 4, 5]
my_tuple = (1, 2, 3)
my_string = "hello"

# All support indexing
print(my_list[0])    # 1
print(my_tuple[1])   # 2
print(my_string[2])  # l

# All support len()
print(len(my_list))  # 5
print(len(my_tuple)) # 3
print(len(my_string))# 5

# All support slicing
print(my_list[1:3])   # [2, 3]
print(my_tuple[:2])   # (1, 2)
print(my_string[::2]) # hlo
```

## Key Differences

Not all iterables are sequences. For example:

```python
my_set = {1, 2, 3}
my_dict = {'a': 1, 'b': 2}

# These are iterables but NOT sequences
for item in my_set:
    print(item)  # Works

for key in my_dict:
    print(key)   # Works

# But these will fail:
# print(my_set[0])      # TypeError: 'set' object is not subscriptable
# print(len(my_set))    # This works! Sets do support len()
# Actually, sets support len() but not indexing

# Dictionaries support len() and some indexing (by key), but not integer indexing
print(len(my_dict))     # 2
print(my_dict['a'])     # 1
# print(my_dict[0])      # KeyError
```

Sets are iterables but not sequences because they don't support integer indexing.

Dictionaries are iterables and support `len()`, but they use keys for indexing rather than integer positions, so they're not considered sequences in the traditional sense.

## Generators: Iterables but not Sequences

Generators are iterables that don't store all values in memory:

```python
def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()

for value in gen:
    print(value)  # Works: 1, 2, 3

# But:
# print(len(gen))  # TypeError: object of type 'generator' has no len()
# print(gen[0])    # TypeError: 'generator' object is not subscriptable
```

## Why This Matters

Understanding the distinction helps you:

- Choose the right data structure for your needs
- Write more efficient code
- Avoid common errors when trying to index non-sequence iterables
- Use appropriate methods for different types of collections

For example, if you need random access and slicing, use a sequence like a list. If you just need to iterate once, a generator might be more memory-efficient.
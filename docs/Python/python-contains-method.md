# Python `__contains__` Method and the `in` Operator

The `in` operator in Python is used to check membership in containers like lists, sets, and dictionaries. Behind the scenes, it calls the `__contains__` method on the object. Understanding how to implement this method allows you to create custom classes that support the `in` operator.

## How the `in` Operator Works

When you write `item in container`, Python calls `container.__contains__(item)`. If `__contains__` is not defined, it falls back to iterating through the container using `__iter__`.

```python
# Built-in containers
my_list = [1, 2, 3]
print(2 in my_list)  # True - calls my_list.__contains__(2)

my_dict = {'a': 1, 'b': 2}
print('a' in my_dict)  # True - checks keys
print(1 in my_dict)    # False - 1 is not a key
```

## Implementing `__contains__` in Custom Classes

You implement `__contains__` when you want your custom class to support the `in` operator with specific membership logic.

### Example 1: Custom Collection Class

```python
class MyCollection:
    def __init__(self, items):
        self.items = items

    def __contains__(self, item):
        return item in self.items

# Usage
collection = MyCollection([1, 2, 3, 4])
print(3 in collection)  # True
print(5 in collection)  # False
```

### Example 2: Range-like Class with Custom Logic

```python
class TemperatureRange:
    def __init__(self, min_temp, max_temp):
        self.min_temp = min_temp
        self.max_temp = max_temp

    def __contains__(self, temp):
        return self.min_temp <= temp <= self.max_temp

# Usage
comfortable_range = TemperatureRange(18, 25)
print(22 in comfortable_range)  # True
print(30 in comfortable_range)  # False
```

### Example 3: Checking Membership Based on Object Attributes

```python
class StudentDatabase:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def __contains__(self, student_id):
        return any(student.id == student_id for student in self.students)

class Student:
    def __init__(self, id, name):
        self.id = id
        self.name = name

# Usage
db = StudentDatabase()
db.add_student(Student(1, "Alice"))
db.add_student(Student(2, "Bob"))

print(1 in db)  # True
print(3 in db)  # False
```

### Example 4: Set-like Behavior with Custom Equality

```python
class CaseInsensitiveSet:
    def __init__(self, items=None):
        self.items = set()
        if items:
            for item in items:
                self.items.add(item.lower())

    def add(self, item):
        self.items.add(item.lower())

    def __contains__(self, item):
        return item.lower() in self.items

# Usage
words = CaseInsensitiveSet(["Hello", "World"])
print("hello" in words)  # True
print("HELLO" in words)  # True
print("goodbye" in words) # False
```

## When to Implement `__contains__`

Implement `__contains__` when:

1. **Performance matters**: For large collections, `__contains__` can be more efficient than iteration
2. **Custom membership logic**: When membership isn't based on simple equality
3. **Semantic clarity**: To make your class behave like a container
4. **Attribute-based checking**: When you want to check for objects based on specific attributes

## Performance Considerations

- If `__contains__` is not implemented, Python falls back to iteration, which is O(n)
- For hash-based lookups, implement both `__contains__` and ensure your class supports hashing if needed
- Consider the time complexity of your `__contains__` implementation

## Common Pitfalls

- Don't forget that `__contains__` should return a boolean
- Be consistent with your membership logic
- If your class is mutable, ensure `__contains__` reflects the current state

By implementing `__contains__`, you can create intuitive and efficient custom containers that integrate seamlessly with Python's membership testing syntax.
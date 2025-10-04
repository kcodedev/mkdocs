# Python Dataclasses

Python dataclasses provide a concise way to create classes that primarily store data, reducing the amount of boilerplate code needed for initialization and other common methods.

## The Problem with Traditional Class Initialization

When creating classes in Python to represent simple data structures, you often end up writing repetitive code in the `__init__` method. For example:

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
```

This pattern becomes tedious for classes with many attributes, requiring you to manually assign each parameter to `self.attribute`.

## Introducing Dataclasses

Since Python 3.7, the `dataclasses` module (introduced in PEP 557) offers a decorator-based approach to simplify this. By applying the `@dataclass` decorator to a class, Python automatically generates the `__init__` method based on the class attributes with type annotations.

Here's the equivalent using dataclasses:

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: float
    y: float
```

The dataclass automatically creates an `__init__` method that accepts `x` and `y` parameters and assigns them to instance attributes.

## Usage Example

```python
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int
    email: str

# Create an instance
person = Person(name="Alice", age=30, email="alice@example.com")
print(person.name)  # Output: Alice
print(person.age)   # Output: 30
```

## Handling Mutable Defaults with `field()`

For attributes that need special handling, such as mutable defaults, use the `field()` function:

```python
from dataclasses import dataclass, field
from typing import List

@dataclass
class Student:
    name: str
    grades: List[int] = field(default_factory=list)

# Now each Student instance gets its own empty list
student1 = Student("Bob")
student2 = Student("Charlie")
student1.grades.append(95)
print(student1.grades)  # [95]
print(student2.grades)  # []
```

Without `field(default_factory=list)`, all instances would share the same list, leading to unexpected behavior.

## Additional Benefits

Dataclasses also automatically generate other methods like `__repr__`, `__eq__`, and `__hash__` if not explicitly defined, making them even more convenient for data-centric classes.
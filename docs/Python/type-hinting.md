# Type Hinting in Python

Type hinting is a feature in Python that allows you to specify the expected data types of variables, function parameters, and return values. This makes your code more readable, helps catch errors early, and improves IDE support for autocompletion and refactoring. Type hints are optional and do not affect runtime behavior—they are purely for static analysis tools like mypy.

## Basic Type Hints

You can use built-in types directly for simple hints.

### Variables

```python
name: str = "Alice"
age: int = 25
height: float = 5.6
is_student: bool = True
```

### Function Parameters and Return Types

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

def add(a: int, b: int) -> int:
    return a + b

def divide(a: float, b: float) -> float:
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

## Using the `typing` Module

For more complex types, import from the `typing` module.

### Lists, Dictionaries, and Tuples

```python
from typing import List, Dict, Tuple

numbers: List[int] = [1, 2, 3, 4]
person: Dict[str, str] = {"name": "Bob", "city": "New York"}
coordinates: Tuple[float, float] = (40.7128, -74.0060)
```

### Optional Types

Use `Optional` for values that can be `None`.

```python
from typing import Optional

def find_user(user_id: int) -> Optional[str]:
    # Simulate a database lookup
    users = {1: "Alice", 2: "Bob"}
    return users.get(user_id)
```

### Union Types

Use `Union` for parameters that can accept multiple types.

```python
from typing import Union

def process_data(data: Union[str, int]) -> str:
    return str(data)
```

## Advanced Type Hints

### Classes and Custom Types

```python
from typing import List

class Student:
    def __init__(self, name: str, grades: List[float]):
        self.name = name
        self.grades = grades

    def average_grade(self) -> float:
        return sum(self.grades) / len(self.grades)

student = Student("Charlie", [85.0, 90.0, 88.0])
```

### Generic Types

```python
from typing import TypeVar, Generic

T = TypeVar('T')

class Stack(Generic[T]):
    def __init__(self):
        self.items: List[T] = []

    def push(self, item: T) -> None:
        self.items.append(item)

    def pop(self) -> T:
        return self.items.pop()

int_stack = Stack[int]()
int_stack.push(1)
int_stack.push(2)
print(int_stack.pop())  # 2
```

## Best Practices

- Use type hints consistently throughout your codebase.
- Run static type checkers like mypy to validate your hints.
- Start with simple hints and add complexity as needed.
- Remember that type hints are for developers and tools, not enforced at runtime.

## Example Exercise

Write a function that takes a list of integers and returns the sum as a float. Add appropriate type hints.

```python
from typing import List

def sum_as_float(numbers: List[int]) -> float:
    return float(sum(numbers))
```

This introduction covers the basics of type hinting. Practice by adding hints to your existing code!
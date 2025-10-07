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

## Creating Meaningful Abstractions

Type hinting goes beyond type checking—it helps create clear, self-documenting abstractions in your code. By defining type aliases and using structured types, you can make complex data representations more readable and maintainable.

### Evolving from Basic to Abstract Types

Consider a function that processes a list of books, where each book is a tuple of ID (integer) and title (string).

**Step 1: Basic Annotation**
```python
def process_books(books: list) -> None:
    # Process the list of books
    pass
```
This provides minimal abstraction, hiding the structure.

**Step 2: Adding Detail**
```python
from typing import List, Tuple

def process_books(books: List[Tuple[int, str]]) -> None:
    # Process the list of books, where each is (id, title)
    pass
```
More explicit, but the tuple's meaning isn't self-evident.

**Step 3: Using a Type Alias**
```python
from typing import List, Tuple

Book = Tuple[int, str]  # ID and title

def process_books(books: List[Book]) -> None:
    # Process the list of books
    for book_id, title in books:
        print(f"Processing book {book_id}: {title}")
```
`Book` creates a meaningful abstraction, improving readability.

**Step 4: Enhanced with TypedDict**
```python
from typing import List, TypedDict

class Book(TypedDict):
    id: int
    title: str

def process_books(books: List[Book]) -> None:
    for book in books:
        print(f"Processing book {book['id']}: {book['title']}")
```
This provides a strong, interface-like abstraction.

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
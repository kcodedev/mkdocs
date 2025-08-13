# 🛠️ Understanding User-Defined Data Types in Python

## 🤔 Why Do We Need User-Defined Types?

In programming, **built-in types** like `int`, `float`, `str` are great for simple data.  
But sometimes, our problem is more complex — it involves multiple related values and operations.

**Example:**  
If we want to store information about a car 🚗, using separate variables:

```python
make = "Toyota"
model = "Corolla"
year = 2020
```

… works, but it’s messy. What if we have 100 cars?  
We need **user-defined types** to group related data and behaviors into one logical unit.

✅ **Advantages:**

- Organises related data together 📦
- Makes code easier to read 📖
- Can model real-world objects more naturally 🌍

---

## 🧩 Non-Composite User-Defined Types

Non-composite means **the type itself doesn’t hold multiple different fields**.  
They’re still “user-defined” because we design them.

### 1. Enumerated Types (`Enum`)
An **enumeration** is a set of named values.

```python
from enum import Enum

class Direction(Enum):
    NORTH = 1
    EAST = 2
    SOUTH = 3
    WEST = 4

# Usage:
print(Direction.NORTH)   # Direction.NORTH
print(Direction.NORTH.name)  # "NORTH"
```

💡 Good for representing a **fixed set of options**.

---

### 2. Pointers (Conceptual in Python)
Python does not have traditional pointers like C/C++,  
but **variables hold references** to objects.

```python
a = [1, 2, 3]
b = a  # b points to the same list as a
b.append(4)
print(a)  # [1, 2, 3, 4] — changes affect both!
```

---

## 🧱 Composite User-Defined Types

Composite types **combine multiple pieces of data** (fields/attributes) together.

### 1. Sets
A set is an **unordered collection** of unique items.

```python
colors = {"red", "green", "blue"}
colors.add("maroon")
print(colors)
```

---

### 2. Record (Using `NamedTuple` or `dataclass`)
A record is a **group of related fields** (like a database row).

```python
from collections import namedtuple
Car = namedtuple("Car", ["make", "model", "year"])

my_car = Car("Toyota", "Corolla", 2020)
print(my_car.make)  # Toyota
```

---

### 3. Class / Object
A class is a **blueprint** for creating objects with attributes and methods.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def display_info(self):
        return f"{self.year} {self.make} {self.model}"

my_car = Car("Toyota", "Corolla", 2020)
print(my_car.display_info())  # 2020 Toyota Corolla
```

---

## 🛠️ Designing a User-Defined Data Type for a Problem

**Problem:** A library 📚 needs to store details of books and check them out.

**Solution:** Create a `Book` class.

```python
class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
        self.checked_out = False

    def check_out(self):
        if not self.checked_out:
            self.checked_out = True
            return f"{self.title} has been checked out."
        return f"{self.title} is already checked out."

    def return_book(self):
        self.checked_out = False
        return f"{self.title} has been returned."

# Example usage
book1 = Book("1984", "George Orwell", 1949)
print(book1.check_out())
print(book1.return_book())
```

---

## 📌 Summary
- **User-defined types** let you model complex problems more naturally.
- **Non-composite**: Enumerations, pointers/references.
- **Composite**: Sets, records, classes.
- **Designing your own type** involves identifying **data** + **behaviors** that belong together.

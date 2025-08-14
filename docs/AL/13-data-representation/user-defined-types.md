# 🛠️ User-Defined Data Types

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

### ✅ **Advantages:**

- Organises related data together 📦
- Makes code easier to read 📖
- Can model real-world objects more naturally 🌍

---

## 🧩 Non-Composite User-Defined Types

Non-composite means **the type itself doesn’t hold multiple different fields**.  
They’re still “user-defined” because we design them.

### 1. Enumerated Types
An **enumerated type** is a user defined type where the programmer maps a set of names to numeric values. The values of enumerated types are ordered.

```
// Define the new type first
TYPE
TMonths(Jan, Feb, Mar, Apr, May, Jun,
		 Jul, Aug, Sep, Oct, Nov, Dec)
ENDTYPE

// Declare a variable of that new type
DECLARE BirthMonth : TMonths

// Example usage
BirthMonth ⬅ Feb
BirthMonth ⬅ Feb + 1

```

💡 Good for representing a **fixed set of options**.

---

### 2. Pointers
Pointers store an address, essentially **pointing** at that address. In Psuedocode you must define a pointer as a new TYPE. Then you can declare a variable of this type and use it.

Step 1️⃣: Define a pointer to an particular type:

`TYPE IntPointer = ^INT`

Step 2️⃣: Declare a variable of the new type `IntPointer`:

`DECLARE MyIntPointer : IntPointer`

You can **de-reference** (get the contents at the address being pointed at) a pointer as shown:

`ValueAtAddress ⬅ MyIntPointer^`

#### Pointer Exam Question

| Variable    | Address | Contents |
|-------------|---------|----------|
|             | 1260    |          |
| IntVar      | 1261    | 66       |
|             | 1262    |          |
|             | ...     |          |
|             | 2411    |          |
| IntPointer  | 2412    | 1261     |
|             | ...     |          |
|             | 3201    |          |
| Var1        | 3202    | 66       |
| Var2        | 3203    | 42       |

State the values of the following expressions:

- IntVar		
- IntPointer	
- IntPointer^
- @Var1			
- IntPointer^ = Var2 + 14

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

### 2. Record
A record is a **group of related fields** (like a database row).

```
TYPE TStudentRecord
	DECLARE FirstName : STRING
	DECLARE FamilyName : STRING
	DECLARE FeesPaid : BOOLEAN
ENDTYPE

DECLARE Student1 : TStudentRecord
Student1.FeesPaid ⬅ TRUE
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

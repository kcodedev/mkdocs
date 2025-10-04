# Structured Programming 🏗️

## Procedures

A procedure is a block of code that performs a task but doesn't return a value. Perfect for reusable actions!

```
PROCEDURE name(param: TYPE)
    statements
ENDPROCEDURE
```

Use procedures when you need to perform actions without needing a result, like printing or updating data.

**Parameters** can be passed **by value** (copy) or **by reference** (original).

## Functions

A function is similar but returns a value. Great for computations!

```
FUNCTION name(parameters) RETURNS type
    statements
    ...
    RETURN value
ENDFUNCTION
```

Use functions when you need to compute and return a value, like calculations.

## Terminology

- **Procedure/Function Header**: The first line declaring the procedure/function.
- **Parameter**: Variable in the definition.
- **Argument**: Value passed when calling.
- **Return Value**: Value sent back from a function.

## Writing Efficient Pseudocode

Use clear, concise statements, avoid redundancy, and structure logically for better readability and performance! 🚀

## Python Examples 🐍

```python
# Procedure example
def greet(name):
    print("Hello, " + name)

greet("Alice")

# Function example
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # 8

# Parameters by reference (mutable objects)
def append_item(lst, item):
    lst.append(item)

my_list = [1, 2]
append_item(my_list, 3)
print(my_list)  # [1, 2, 3]

# By value (immutable)
def modify_num(num):
    num = num + 1
    return num

x = 5
y = modify_num(x)
print(x, y)  # 5, 6
```
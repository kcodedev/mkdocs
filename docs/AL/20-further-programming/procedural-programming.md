# Procedural Programming

Procedural programming is a programming paradigm based on the concept of procedure calls, where programs are structured as a sequence of instructions that tell the computer what to do step by step. It emphasizes the use of procedures (also called functions or subroutines) to organize code into reusable blocks.

## Key Concepts

### Procedures/Functions

Procedures are self-contained blocks of code that perform a specific task. They can take inputs (parameters) and return outputs.

```python
def calculate_area(length, width):
    """Calculate the area of a rectangle."""
    area = length * width
    return area

# Using the procedure
result = calculate_area(5, 3)
print(result)  # Output: 15
```

### Variables and Data Types

Procedural programming uses variables to store data and supports various data types (integers, floats, strings, etc.).

```python
# Variable declarations
name = "Alice"
age = 25
height = 1.65
is_student = True
```

### Control Structures

- **Sequential Execution**: Statements execute one after another.
- **Selection**: Conditional statements like if-else.
- **Iteration**: Loops like for and while.

```python
# Selection
if age >= 18:
    print("Adult")
else:
    print("Minor")

# Iteration
for i in range(5):
    print(i)
```

## Modular Programming

Procedural programming supports breaking programs into modules or files, each containing related procedures.

### Example Module Structure

```
main.py
├── utils.py (utility functions)
├── math_operations.py (mathematical functions)
└── file_operations.py (file handling functions)
```

```python
# math_operations.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

```python
# main.py
from math_operations import add, multiply

result1 = add(5, 3)
result2 = multiply(4, 2)
print(f"Add: {result1}, Multiply: {result2}")
```

## Scope and Lifetime

### Local Variables

Variables declared inside a procedure are local to that procedure and cannot be accessed outside.

```python
def example_function():
    local_var = 10  # Local variable
    print(local_var)

example_function()
# print(local_var)  # This would cause an error
```

### Global Variables

Variables declared outside procedures are global and can be accessed throughout the program.

```python
global_var = 100

def modify_global():
    global global_var
    global_var = 200

modify_global()
print(global_var)  # Output: 200
```

## Parameter Passing

### Pass by Value

A copy of the value is passed to the procedure. Changes inside the procedure don't affect the original.

```python
def increment(x):
    x = x + 1
    print(f"Inside function: {x}")

num = 5
increment(num)
print(f"Outside function: {num}")  # Still 5
```

### Pass by Reference

The reference to the variable is passed. Changes affect the original (common in languages like Python for mutable objects).

```python
def append_item(lst):
    lst.append(4)

my_list = [1, 2, 3]
append_item(my_list)
print(my_list)  # [1, 2, 3, 4]
```

## Structured Programming

Procedural programming follows structured programming principles:

1. **Sequence**: Statements execute in order.
2. **Selection**: Choose between alternatives.
3. **Iteration**: Repeat statements.
4. **Modularity**: Break programs into smaller, manageable parts.

## Advantages

1. **Simplicity**: Easy to learn and understand for beginners.
2. **Efficiency**: Direct control over program flow and memory.
3. **Modularity**: Code can be broken into reusable functions.
4. **Performance**: Generally faster than interpreted languages.
5. **Wide Support**: Supported by most programming languages.

## Disadvantages

1. **Limited Abstraction**: Doesn't model real-world objects well.
2. **Global State**: Reliance on global variables can lead to bugs.
3. **Scalability**: Large programs can become complex and hard to maintain.
4. **Code Reuse**: Less emphasis on reusable components compared to OOP.
5. **Data Security**: Data is not encapsulated; can be modified anywhere.

## Common Procedural Languages

- C
- Pascal
- BASIC
- Fortran
- COBOL

## Comparison with Other Paradigms

| Aspect | Procedural | Object-Oriented | Functional |
|--------|------------|-----------------|------------|
| Focus | Procedures/Functions | Objects/Classes | Functions as first-class |
| Data Handling | Global/Local variables | Encapsulated in objects | Immutable data |
| Code Organization | Functions and modules | Classes and inheritance | Higher-order functions |
| State Management | Variables | Object state | No state (pure functions) |
| Complexity | Low to Medium | Medium to High | Medium |

## Best Practices

1. **Use Meaningful Names**: Choose descriptive names for procedures and variables.
2. **Limit Global Variables**: Minimize use of global variables to reduce side effects.
3. **Modular Design**: Break complex tasks into smaller, focused procedures.
4. **Consistent Indentation**: Use consistent formatting for readability.
5. **Documentation**: Comment procedures and complex logic.
6. **Avoid Deep Nesting**: Limit nested control structures for clarity.

## Example: Complete Procedural Program

```python
def get_user_input():
    """Get two numbers from user."""
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))
    return num1, num2

def perform_operation(num1, num2, operation):
    """Perform the specified operation."""
    if operation == '+':
        return num1 + num2
    elif operation == '-':
        return num1 - num2
    elif operation == '*':
        return num1 * num2
    elif operation == '/':
        if num2 != 0:
            return num1 / num2
        else:
            return "Error: Division by zero"
    else:
        return "Error: Invalid operation"

def display_result(result):
    """Display the calculation result."""
    print(f"Result: {result}")

# Main program
def main():
    num1, num2 = get_user_input()
    operation = input("Enter operation (+, -, *, /): ")
    result = perform_operation(num1, num2, operation)
    display_result(result)

if __name__ == "__main__":
    main()
```

This example demonstrates procedural programming principles: modular functions, clear separation of concerns, and a main function that orchestrates the program flow.
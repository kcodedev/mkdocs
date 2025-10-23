# Python Conditionals Tutorial

This tutorial covers Python conditionals, focusing on their use in the Fetch-Decode-Execute (FDE) simulator for instruction decoding and execution. Conditionals are essential for controlling program flow based on conditions, which is crucial for simulating how a CPU decodes opcodes and executes instructions.

## 1. What are Conditionals?

Conditionals in Python are statements that allow your program to make decisions based on whether certain conditions are true or false. They enable the code to execute different blocks depending on the evaluation of expressions.

**Why are they important?**
- They control the flow of execution, allowing programs to respond dynamically to data or user input.
- In the context of the FDE simulator, conditionals are used to decode opcodes (operation codes) in instructions and determine which operation to perform, such as LOAD, ADD, STORE, or HALT.
- Without conditionals, programs would execute linearly, limiting their ability to handle varying scenarios, like different instruction types in a CPU simulation.

## 2. If Statements

The basic `if` statement executes a block of code only if a condition is true.

**Syntax:**
```python
if condition:
    # Code to execute if condition is true
```

**Example:**
```python
# Basic if statement
temperature = 25
if temperature > 20:
    print("It's warm outside!")
```

In the FDE simulator, an `if` statement might check if an opcode matches a specific value before executing the corresponding instruction.

## 3. If-Else Statements

The `if-else` statement adds an alternative action if the condition is false.

**Syntax:**
```python
if condition:
    # Code if true
else:
    # Code if false
```

**Example:**
```python
# If-else for temperature check
temperature = 15
if temperature > 20:
    print("It's warm!")
else:
    print("It's cool.")
```

This is useful in simulators for handling binary decisions, like checking if an instruction is valid or not.

## 4. If-Elif-Else Chains

For multiple conditions, use `if-elif-else` chains. This is perfect for instruction decoding in the FDE simulator, where different opcodes require different actions.

**Syntax:**
```python
if condition1:
    # Code for condition1
elif condition2:
    # Code for condition2
else:
    # Default code
```

**Example:**
```python
# Multiple conditions for weather
weather = "rainy"
if weather == "sunny":
    print("Wear sunglasses!")
elif weather == "rainy":
    print("Take an umbrella!")
else:
    print("Check the weather app.")
```

In the FDE simulator, this structure decodes opcodes:
```python
opcode = "ADD"
if opcode == "LOAD":
    # Execute LOAD instruction
    print("Loading data...")
elif opcode == "ADD":
    # Execute ADD instruction
    print("Adding numbers...")
elif opcode == "STORE":
    # Execute STORE instruction
    print("Storing data...")
else:
    print("Unknown opcode!")
```

## 5. Comparison Operators

Comparison operators are used in conditions to compare values. They return `True` or `False`.

- `==` (equal to)
- `!=` (not equal to)
- `<` (less than)
- `>` (greater than)
- `<=` (less than or equal to)
- `>=` (greater than or equal to)

**Example:**
```python
# Using comparison operators
x = 10
y = 5
if x > y:
    print("x is greater than y")
if x != y:
    print("x and y are not equal")
```

In the simulator, compare opcodes or operands:
```python
opcode = 0b0001  # Example binary opcode for ADD
if opcode == 0b0001:
    print("This is an ADD instruction")
```

## 6. Logical Operators

Logical operators combine multiple conditions:
- `and` (both conditions must be true)
- `or` (at least one condition must be true)
- `not` (inverts the condition)

**Example:**
```python
# Logical operators
age = 25
has_license = True
if age >= 18 and has_license:
    print("Can drive!")
if age < 18 or not has_license:
    print("Cannot drive.")
```

For complex instruction decoding:
```python
opcode = "ADD"
operand1 = 5
operand2 = 3
if opcode == "ADD" and operand1 > 0:
    result = operand1 + operand2
    print(f"Result: {result}")
```

## 7. Application to FDE Simulator

In the FDE simulator, conditionals decode instructions by checking the opcode and executing the appropriate operation. Here's how:

- **Fetch**: Get the instruction.
- **Decode**: Use conditionals to identify the opcode.
- **Execute**: Perform the action based on the decoded opcode.

**Example Instruction Decoding:**
```python
# Simulated FDE cycle with conditionals
instruction = {"opcode": "LOAD", "address": 100}
opcode = instruction["opcode"]

if opcode == "LOAD":
    print(f"Loading from address {instruction['address']}")
elif opcode == "ADD":
    print("Adding two values")
elif opcode == "STORE":
    print(f"Storing to address {instruction['address']}")
elif opcode == "HALT":
    print("Halting the processor")
else:
    print("Invalid opcode")
```

This structure allows the simulator to handle different instruction types efficiently.

## 8. Nested Conditionals

Nested conditionals are `if` statements inside other `if` statements, useful for more complex logic in advanced instruction sets.

**Syntax:**
```python
if outer_condition:
    if inner_condition:
        # Code
```

**Example:**
```python
# Nested for complex checks
opcode = "ADD"
mode = "immediate"
if opcode == "ADD":
    if mode == "immediate":
        print("Add immediate value")
    else:
        print("Add register values")
```

In the simulator, nest for sub-conditions like addressing modes.

## 9. Practical Examples

**Complete Instruction Decoding Example:**
```python
# Full FDE simulator snippet
def decode_and_execute(instruction):
    opcode = instruction["opcode"]
    if opcode == "LOAD":
        address = instruction["address"]
        print(f"LOAD: Loading data from memory address {address}")
        # Simulate loading
    elif opcode == "ADD":
        src1 = instruction["src1"]
        src2 = instruction["src2"]
        print(f"ADD: Adding {src1} and {src2}")
        # Simulate addition
    elif opcode == "STORE":
        address = instruction["address"]
        value = instruction["value"]
        print(f"STORE: Storing {value} to address {address}")
        # Simulate storing
    elif opcode == "HALT":
        print("HALT: Stopping execution")
        return False  # Signal to stop
    else:
        print("ERROR: Unknown opcode")
    return True

# Example usage
instructions = [
    {"opcode": "LOAD", "address": 100},
    {"opcode": "ADD", "src1": 5, "src2": 3},
    {"opcode": "STORE", "address": 200, "value": 8},
    {"opcode": "HALT"}
]

for inst in instructions:
    if not decode_and_execute(inst):
        break
```

This example demonstrates a simple simulator loop using conditionals.

## 10. Common Mistakes

1. **Forgetting Colons**: Always end `if`, `elif`, and `else` with a colon (`:`).
   - Mistake: `if condition` (missing `:`)
   - Fix: `if condition:`

2. **Indentation Errors**: Python uses indentation to define blocks. Inconsistent indentation causes `IndentationError`.
   - Mistake: Mixing spaces and tabs.
   - Fix: Use consistent indentation (e.g., 4 spaces).

3. **Using `=` instead of `==`**: Assignment (`=`) vs. comparison (`==`).
   - Mistake: `if x = 5:` (assignment, not comparison)
   - Fix: `if x == 5:`

4. **Not Handling All Cases**: In `if-elif-else`, ensure all possibilities are covered or use a default `else`.
   - Mistake: Missing `else` for unknown opcodes.
   - Fix: Add `else: print("Error")`

5. **Overly Complex Nesting**: Deep nesting can make code hard to read. Refactor if possible.

By mastering conditionals, you can effectively simulate instruction decoding in the FDE cycle, making your Python programs more dynamic and responsive.
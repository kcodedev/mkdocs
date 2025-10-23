# Python Variables and Data Types Tutorial

This tutorial covers the fundamental concepts of variables and data types in Python, with a focus on how these concepts are used in the FDE (Fetch-Decode-Execute) CPU simulator exercise.

## Table of Contents

1. [What are Variables?](#what-are-variables)
2. [Basic Data Types](#basic-data-types)
3. [Type Conversion](#type-conversion)
4. [Variable Assignment and Modification](#variable-assignment-and-modification)
5. [CPU Register Simulation](#cpu-register-simulation)
6. [Scope and Lifetime](#scope-and-lifetime)
7. [Practical Examples](#practical-examples)
8. [Common Mistakes](#common-mistakes)

## What are Variables?

Variables are containers that store data values in a Python program. They act as named references to memory locations where data is stored.

### Variable Definition

A variable is created when you assign a value to it:

```python
# Creating variables
accumulator = 42
program_counter = 0
instruction = "10110000"
halted = False
```

### Variable Naming Rules

Python variable names must follow these rules:

1. **Start with a letter or underscore**: Variables must begin with a letter (a-z, A-Z) or an underscore (_)
2. **Contain only letters, numbers, and underscores**: After the first character, you can use letters, numbers (0-9), and underscores
3. **Case-sensitive**: `accumulator` and `Accumulator` are different variables
4. **Cannot be Python keywords**: You cannot use reserved words like `if`, `for`, `while`, `def`, `class`, etc.

### Valid Variable Names

```python
# Valid names
accumulator = 0
program_counter = 0
_memory_address = 1000
instruction1 = "LOAD"
reg_A = 42
```

### Invalid Variable Names

```python
# Invalid names - these will cause errors
1variable = 42      # Cannot start with number
my-variable = 42    # Cannot use hyphens
if = 42             # Cannot use Python keywords
```

## Basic Data Types

Python has several built-in data types that are essential for the CPU simulator. Each type serves a specific purpose in representing different aspects of the computer system.

### Integers (int)

Integers represent whole numbers and are used for CPU registers and memory addresses in the simulator.

```python
# Integer variables for CPU registers
ACC = 0          # Accumulator register
PC = 0           # Program Counter
MAR = 1000       # Memory Address Register
MDR = 0          # Memory Data Register
```

**Key characteristics:**
- Can be positive, negative, or zero
- No size limit in Python (unlike other languages)
- Used for arithmetic operations and counting

### Strings (str)

Strings represent text data and are used for binary instructions, memory contents, and assembly code in the simulator.

```python
# String variables for instructions and memory
current_instruction = "10110000"    # Binary instruction
memory_address = "0x1000"           # Hexadecimal address
opcode = "LOAD"                     # Assembly mnemonic
```

**Key characteristics:**
- Enclosed in single or double quotes
- Immutable (cannot be changed after creation)
- Used for representing binary data, instructions, and addresses

### Booleans (bool)

Booleans represent true/false values and are used for flags and conditional states in the simulator.

```python
# Boolean variables for system state
halted = False      # CPU execution state
zero_flag = False   # Arithmetic result flag
carry_flag = False  # Arithmetic carry flag
running = True      # Program execution state
```

**Key characteristics:**
- Only two possible values: `True` or `False`
- Used for decision making and state tracking
- Essential for control flow in the simulator

## Type Conversion

Type conversion (also called type casting) allows you to convert variables from one data type to another. This is crucial in the CPU simulator when working with different representations of data.

### Converting to Integer

```python
# Converting strings to integers
binary_value = "1011"      # Binary string
decimal_value = int(binary_value, 2)  # Convert binary to decimal: 11

hex_address = "0x1000"     # Hexadecimal string
memory_location = int(hex_address, 16)  # Convert hex to decimal: 4096

# Converting boolean to integer
flag = True
flag_value = int(flag)     # Results in 1
```

### Converting to String

```python
# Converting integers to strings
register_value = 42
binary_string = bin(register_value)    # "0b101010"
hex_string = hex(register_value)       # "0x2a"
decimal_string = str(register_value)   # "42"

# Converting boolean to string
halted = False
status = str(halted)       # "False"
```

### Converting to Boolean

```python
# Converting integers to boolean
result = 0
is_zero = bool(result)     # False (0 is falsy)

result = 42
is_nonzero = bool(result)  # True (non-zero is truthy)

# Converting strings to boolean
empty_string = ""
is_empty = bool(empty_string)  # False (empty string is falsy)

instruction = "LOAD"
has_instruction = bool(instruction)  # True (non-empty string is truthy)
```

## Variable Assignment and Modification

Variables in Python are dynamic - they can change type and value during program execution. This flexibility is important in the CPU simulator where registers and memory locations need to be updated frequently.

### Basic Assignment

```python
# Initial assignment
ACC = 0
PC = 0
halted = False

# Multiple assignment
ACC, PC, halted = 0, 0, False
```

### Variable Modification

```python
# Modifying variables
ACC = ACC + 1      # Increment accumulator
PC = PC + 1        # Increment program counter
halted = True      # Set CPU to halted state

# Using compound assignment operators
ACC += 5           # Add 5 to accumulator
PC *= 2            # Double the program counter
```

### Dynamic Typing

Python variables can change type during execution:

```python
# Variable starts as integer
register = 42
print(type(register))  # <class 'int'>

# Changes to string
register = "101010"
print(type(register))  # <class 'str'>

# Changes to boolean
register = True
print(type(register))  # <class 'bool'>
```

## CPU Register Simulation

In the FDE simulator, variables represent the various components of a CPU. Understanding how to use variables to simulate these components is essential for the exercise.

### Register Variables

```python
# CPU Registers as variables
ACC = 0                    # Accumulator - stores arithmetic results
PC = 0                     # Program Counter - points to current instruction
IR = ""                    # Instruction Register - holds current instruction
MAR = 0                    # Memory Address Register - holds memory address
MDR = 0                    # Memory Data Register - holds data from memory
```

### Memory Simulation

```python
# Memory as a list of strings (representing binary data)
memory = [
    "10110000",  # LOAD instruction
    "00001111",  # Data value
    "10110001",  # STORE instruction
    "00000000",  # More data
]

# Accessing memory using PC as index
current_instruction = memory[PC]
```

### Flag Variables

```python
# Status flags as boolean variables
zero_flag = False      # Set when result is zero
carry_flag = False     # Set when arithmetic operation carries
overflow_flag = False  # Set when result exceeds register capacity
halted = False         # Set when CPU should stop execution
```

### Complete CPU State Example

```python
# Complete CPU state representation
class CPUSimulator:
    def __init__(self):
        # Registers
        self.ACC = 0           # Accumulator
        self.PC = 0            # Program Counter
        self.IR = ""           # Instruction Register
        self.MAR = 0           # Memory Address Register
        self.MDR = 0           # Memory Data Register
        
        # Memory
        self.memory = [
            "10110000",  # LOAD 15
            "00001111",  # Data: 15
            "10110001",  # STORE
            "00000000",  # Address: 0
        ]
        
        # Flags
        self.zero_flag = False
        self.carry_flag = False
        self.halted = False
        
    def fetch(self):
        """Fetch instruction from memory"""
        self.IR = self.memory[self.PC]
        self.PC += 1
        
    def decode(self):
        """Decode the instruction"""
        # Extract opcode and operand from binary instruction
        opcode = self.IR[:4]    # First 4 bits
        operand = self.IR[4:]   # Last 4 bits
        
        return opcode, operand
        
    def execute(self, opcode, operand):
        """Execute the decoded instruction"""
        if opcode == "1011":  # LOAD instruction
            address = int(operand, 2)
            self.MAR = address
            self.MDR = int(self.memory[address], 2)
            self.ACC = self.MDR
            self.zero_flag = (self.ACC == 0)
```

## Scope and Lifetime

Variable scope determines where a variable can be accessed in your program. Understanding scope is important when writing functions for the CPU simulator.

### Local Variables

Variables created inside a function are local to that function:

```python
def execute_instruction(instruction):
    """Execute a single instruction"""
    # Local variables - only exist within this function
    opcode = instruction[:4]
    operand = instruction[4:]
    result = 0
    
    # These variables cannot be accessed outside the function
    return result

# opcode, operand, result are not accessible here
```

### Global Variables

Variables created outside functions are global and can be accessed anywhere:

```python
# Global variables - accessible throughout the program
ACC = 0
PC = 0
halted = False

def fetch_instruction():
    """Fetch next instruction"""
    global PC  # Declare PC as global to modify it
    instruction = memory[PC]
    PC += 1    # Modify global PC
    return instruction

def check_halt():
    """Check if CPU should halt"""
    global halted
    if ACC == 0:
        halted = True  # Modify global halted flag
```

### Variable Lifetime

- **Local variables**: Created when function is called, destroyed when function returns
- **Global variables**: Created when program starts, destroyed when program ends

```python
def simulate_step():
    """Simulate one FDE cycle"""
    local_counter = 0  # Created when function starts
    
    # Use local variable for temporary calculations
    local_counter += 1
    
    # Local variable destroyed when function returns
    return local_counter

# Global variable persists between function calls
global_step = 0

def next_cycle():
    global global_step
    global_step += 1
    return simulate_step()
```

## Practical Examples

Here are practical examples showing how variables work in the CPU simulator context:

### Simple CPU Simulation

```python
# Simple CPU simulator using variables
def run_cpu():
    # Initialize CPU state
    ACC = 0
    PC = 0
    memory = ["10110000", "00001111", "10110001", "00000000"]
    halted = False
    
    while not halted and PC < len(memory):
        # Fetch
        instruction = memory[PC]
        PC += 1
        
        # Decode
        opcode = instruction[:4]
        operand = instruction[4:]
        
        # Execute
        if opcode == "1011":  # LOAD
            address = int(operand, 2)
            if address < len(memory):
                ACC = int(memory[address], 2)
        elif opcode == "1010":  # ADD
            address = int(operand, 2)
            if address < len(memory):
                value = int(memory[address], 2)
                ACC += value
        elif opcode == "1111":  # HALT
            halted = True
            
    return ACC

# Run the simulation
result = run_cpu()
print(f"Final accumulator value: {result}")
```

### Memory Management Example

```python
# Memory management with variables
def initialize_memory(size):
    """Initialize memory with empty values"""
    memory = []
    for i in range(size):
        memory.append("00000000")  # Empty memory location
    return memory

def load_program(memory, program):
    """Load a program into memory"""
    for i, instruction in enumerate(program):
        if i < len(memory):
            memory[i] = instruction
    return memory

# Usage
memory = initialize_memory(16)
program = [
    "10110000",  # LOAD
    "00001111",  # Value 15
    "10110001",  # STORE
    "00000001",  # Address 1
]

memory = load_program(memory, program)
```

## Common Mistakes

Here are typical errors students make when working with variables and data types in the CPU simulator:

### 1. Variable Name Errors

```python
# Incorrect - starts with number
1register = 42

# Incorrect - uses hyphen
my-register = 42

# Incorrect - uses Python keyword
if = 42

# Correct
register1 = 42
my_register = 42
register_if = 42
```

### 2. Type Mismatch Errors

```python
# Incorrect - trying to add string and integer
ACC = 42
instruction = "LOAD"
result = ACC + instruction  # TypeError

# Correct - convert types properly
result = ACC + int("15", 2)  # Convert binary string to int
```

### 3. Index Out of Range

```python
# Incorrect - accessing memory without bounds checking
memory = ["1011", "1111"]
PC = 0
instruction = memory[PC]  # OK
PC = 1
instruction = memory[PC]  # OK
PC = 2
instruction = memory[PC]  # IndexError

# Correct - add bounds checking
if PC < len(memory):
    instruction = memory[PC]
else:
    halted = True
```

### 4. Variable Scope Issues

```python
# Incorrect - trying to access local variable outside function
def execute():
    local_var = 42
    return local_var

result = execute()
print(local_var)  # NameError - local_var doesn't exist here

# Correct - return the value or use global variables
def execute():
    global global_var
    global_var = 42
    return global_var
```

### 5. Type Conversion Errors

```python
# Incorrect - invalid conversion
binary_string = "1021"  # Invalid binary (contains 2)
decimal = int(binary_string, 2)  # ValueError

# Correct - validate input first
def safe_binary_to_int(binary_str):
    if all(bit in '01' for bit in binary_str):
        return int(binary_str, 2)
    else:
        raise ValueError("Invalid binary string")
```

### 6. Boolean Logic Errors

```python
# Incorrect - confusing assignment with comparison
halted = False
if halted = True:  # SyntaxError - single = is assignment
    stop_cpu()

# Correct - use double == for comparison
if halted == True:
    stop_cpu()

# Even better - direct boolean comparison
if halted:
    stop_cpu()
```

### 7. Memory Reference Issues

```python
# Incorrect - modifying memory reference instead of content
memory = ["1011", "1111", "0000"]
current_instruction = memory[0]
current_instruction = "LOAD"  # This doesn't change memory[0]

# Correct - modify the actual memory location
memory[0] = "LOAD"
```

## Summary

Variables and data types are the foundation of the CPU simulator. Understanding how to:

- Create and name variables correctly
- Use appropriate data types for different CPU components
- Convert between types when necessary
- Manage variable scope in functions
- Avoid common programming mistakes

These skills are essential for successfully implementing the FDE cycle simulator and understanding how a CPU processes instructions and data.

## Next Steps

After mastering variables and data types, you should explore:
- [Python Lists Tutorial](python-lists-tutorial.md) - for memory arrays
- [Python Binary Tutorial](python-binary-tutorial.md) - for instruction processing
- [FDE Cycle Exercise](python-exercise.md) - to apply these concepts
# Python Loops Tutorial

## 1. What are Loops?

Loops are control structures in programming that allow you to execute a block of code repeatedly. They are essential for automating repetitive tasks, processing collections of data, and implementing iterative algorithms.

There are two main types of loops in Python:

- **While Loops**: Repeat a block of code as long as a condition is true. Ideal for situations where the number of iterations is not known in advance.

- **For Loops**: Iterate over a sequence (like a list, tuple, or string) or other iterable objects. Best when you know the number of iterations or need to process each item in a collection.

## 2. While Loops

While loops are perfect for scenarios like the Fetch-Decode-Execute (FDE) cycle in computer architecture simulations, where you need to continue executing until a certain condition is met.

### Basic Syntax

```python
while condition:
    # Code to execute repeatedly
```

### Example

```python
count = 0
while count < 5:
    print(f"Count is {count}")
    count += 1
```

This loop will print numbers from 0 to 4.

## 3. Loop Control

Python provides several statements to control the flow within loops:

- **break**: Exits the loop immediately.

- **continue**: Skips the rest of the current iteration and moves to the next one.

- **else**: Executes a block of code when the loop condition becomes false (not executed if the loop is terminated by break).

### Example with break and continue

```python
i = 0
while i < 10:
    i += 1
    if i == 5:
        continue  # Skip 5
    if i == 8:
        break  # Exit at 8
    print(i)
else:
    print("Loop completed normally")
```

## 4. For Loops

For loops are used when you need to iterate over a sequence or range.

### Basic Syntax

```python
for variable in iterable:
    # Code to execute
```

### When to Use For vs While

- Use **for loops** when iterating over known sequences or ranges.

- Use **while loops** for conditional repetition where the number of iterations is unknown, like waiting for user input or simulating cycles until a halt condition.

## 5. Loop Variables and Iteration

Loop variables hold the current value during each iteration. In for loops, they automatically take values from the iterable. In while loops, you manage them manually.

### Example

```python
# For loop
for num in range(3):
    print(num)

# While loop
num = 0
while num < 3:
    print(num)
    num += 1
```

## 6. Application to FDE Simulator

In the context of the FDE (Fetch-Decode-Execute) cycle simulator, while loops are used to model the continuous operation of a CPU until it halts.

### Key Concepts

- **while not halted**: The loop continues as long as the CPU is not halted.

- **Main Simulation Loop**: The loop body implements the FDE cycle steps.

- **Loop Termination Conditions**: The loop stops when a halt instruction is encountered or an error occurs.

### Example Implementation

```python
halted = False
program_counter = 0
memory = [/* simulated memory */]

while not halted:
    # Fetch
    instruction = memory[program_counter]
    
    # Decode
    # Decode the instruction
    
    # Execute
    # Execute the instruction
    if instruction == "HALT":
        halted = True
    
    program_counter += 1
```

## 7. Infinite Loops

An infinite loop occurs when the loop condition never becomes false.

### Example

```python
while True:
    print("This will run forever!")
```

### How to Avoid

- Ensure the loop condition can eventually become false.

- Use counters or flags to control termination.

- Test with small inputs to verify behavior.

## 8. Nested Loops

Nested loops are loops inside other loops, useful for multi-dimensional data or complex simulations.

### Example

```python
for i in range(3):
    for j in range(3):
        print(f"i={i}, j={j}")
```

In simulators, nested loops might model multiple CPU cycles or layered processes.

## 9. Practical Examples

### Complete FDE Cycle Implementation

```python
class FDESimulator:
    def __init__(self):
        self.halted = False
        self.pc = 0
        self.memory = ["LOAD", "ADD", "STORE", "HALT"]
    
    def run(self):
        while not self.halted:
            instruction = self.fetch()
            self.decode_and_execute(instruction)
    
    def fetch(self):
        if self.pc < len(self.memory):
            return self.memory[self.pc]
        else:
            self.halted = True
            return None
    
    def decode_and_execute(self, instruction):
        if instruction == "HALT":
            self.halted = True
        elif instruction == "LOAD":
            # Simulate load
            pass
        # Add more instructions as needed
        self.pc += 1

# Usage
sim = FDESimulator()
sim.run()
```

## 10. Common Mistakes and Debugging Tips

### Common Mistakes

1. **Infinite Loops**: Forgetting to update the loop variable.

2. **Off-by-One Errors**: Incorrect loop bounds.

3. **Misusing break/continue**: Leading to unexpected behavior.

4. **Not Handling Edge Cases**: Like empty iterables in for loops.

### Debugging Tips

- Use print statements to track variable values.

- Add counters to monitor iterations.

- Test with simple cases first.

- Use Python's debugger (pdb) for step-by-step execution.

This tutorial provides a foundation for using loops in Python, with a focus on their application in simulations like the FDE cycle.
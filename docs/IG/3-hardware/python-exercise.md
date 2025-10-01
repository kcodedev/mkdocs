# FDE Cycle Simulator 🐍

**Task:**  
Write a Python program to simulate a simple CPU executing a basic instruction set through the Fetch-Decode-Execute cycle.

Your program should:

1. Define a small set of instructions (LOAD, ADD, STORE, HALT).
2. Use registers (accumulator, program counter) and a memory array.
3. Implement the FDE cycle in a loop until HALT.
4. Execute a sample program and output the CPU state after each cycle.

This exercise demonstrates CPU architecture, the Von Neumann model, and instruction processing.

---

## Step-by-Step Guidance

We'll build the simulator step by step. Start with an empty Python file and add code as we go.

### Step 1 — Define the instruction set and constants
First, define what each instruction does and assign numbers to them.

```python
# Instruction opcodes
LOAD = 1   # LOAD addr: Load value from memory[addr] into ACC
ADD = 2    # ADD addr: Add value from memory[addr] to ACC
STORE = 3  # STORE addr: Store ACC value to memory[addr]
HALT = 4   # HALT: Stop the program
```

### Step 2 — Set up CPU components
Create variables for the CPU's memory and registers.

```python
# Initialize CPU components
memory = [0] * 16  # Memory with 16 locations, all starting at 0
ACC = 0            # Accumulator register
PC = 0             # Program Counter register
halted = False     # Flag to stop the program
```

### Step 3 — Load the sample program
Put the program instructions and data into memory.

```python
# Load sample program: LOAD 4, ADD 5, STORE 6, HALT
memory[0] = 14  # LOAD 4 (1*10 + 4)
memory[1] = 25  # ADD 5 (2*10 + 5)
memory[2] = 36  # STORE 6 (3*10 + 6)
memory[3] = 40  # HALT (4*10 + 0)
memory[4] = 5   # Data
memory[5] = 10  # Data
memory[6] = 0   # Result location
```

### Step 4 — Implement the FDE cycle loop
Use a while loop to repeat the cycle until halted.

```python
while not halted:
    # Fetch: Get the instruction from memory at PC
    instruction = memory[PC]
    
    # Decode: Split into opcode and operand
    opcode = instruction // 10  # First digit
    operand = instruction % 10  # Second digit
    
    # Execute: Do what the instruction says
    if opcode == LOAD:
        ACC = memory[operand]
    elif opcode == ADD:
        ACC += memory[operand]
    elif opcode == STORE:
        memory[operand] = ACC
    elif opcode == HALT:
        halted = True
    
    # Increment PC for next instruction
    PC += 1
    
    # Print current state
    print(f"PC: {PC}, ACC: {ACC}, Memory[6]: {memory[6]}")
```

### Step 5 — Run the program
Put all the code together and run it. You should see the state printed after each cycle.

Full code example:

```python
# Instruction opcodes
LOAD = 1
ADD = 2
STORE = 3
HALT = 4

# Initialize CPU
memory = [0] * 16
ACC = 0
PC = 0
halted = False

# Load program
memory[0] = 14  # LOAD 4
memory[1] = 25  # ADD 5
memory[2] = 36  # STORE 6
memory[3] = 40  # HALT
memory[4] = 5
memory[5] = 10
memory[6] = 0

# Run FDE cycle
while not halted:
    instruction = memory[PC]
    opcode = instruction // 10
    operand = instruction % 10
    
    if opcode == LOAD:
        ACC = memory[operand]
    elif opcode == ADD:
        ACC += memory[operand]
    elif opcode == STORE:
        memory[operand] = ACC
    elif opcode == HALT:
        halted = True
    
    PC += 1
    print(f"After cycle: PC={PC}, ACC={ACC}, Memory[6]={memory[6]}")

print("Program finished!")
```

---

**Example to test:**  
Memory initial: [10, 21, 32, 40, 5, 10, 0]  // 10=LOAD 0, 21=ADD 1, 32=STORE 2, 40=HALT, data 5,10,0

- Cycle 1: Fetch 10, Decode LOAD 0, Execute ACC=5, PC=1
- Cycle 2: Fetch 21, Decode ADD 1, Execute ACC=5+10=15, PC=2
- Cycle 3: Fetch 32, Decode STORE 2, Execute memory[2]=15, PC=3
- Cycle 4: Fetch 40, Decode HALT, Stop

Final: ACC=15, memory[2]=15

---

## Extension Activity: Visualize the CPU with Rich and/or Textual

Enhance your CPU simulator by integrating visualization libraries for a more engaging experience:

- **Using Rich** ([Documentation](https://rich.readthedocs.io/en/stable/)): Display the CPU state (registers, memory) in colorful tables after each cycle. Use progress bars to represent execution progress or highlight changes in memory.
- **Using Textual** ([Documentation](https://textual.textualize.io/)): Build an interactive terminal app with live-updating widgets showing the FDE cycle in real-time, allowing step-by-step execution and dynamic memory inspection.

This extension promotes advanced Python skills in UI development while deepening understanding of CPU operations through interactive feedback.
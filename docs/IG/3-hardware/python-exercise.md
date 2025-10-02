# FDE Cycle Simulator 🐍

**Task:**  
Write a Python program to simulate a simple CPU executing a basic instruction set through the Fetch-Decode-Execute cycle.

Your program should:

1. Define a small set of instructions (LOAD, ADD, STORE, HALT).
2. Use registers (accumulator, program counter) and a memory(RAM) array.
3. Implement the FDE cycle in a loop until HALT.
4. Execute a sample program and output the CPU state after each cycle.

This exercise demonstrates CPU architecture, the Von Neumann model, and instruction processing.

---

## Step-by-Step Guidance

We'll build the simulator step by step. Start with an empty Python file and add code as we go.

### Step 1 — Define the instruction set and constants
First, define what each instruction does and assign numbers to them.

```python
# Instruction opcodes (4-bit binary)
LOAD = '0001'   # LOAD addr: Load value from memory(RAM)[addr] into ACC
ADD = '0010'    # ADD addr: Add value from memory(RAM)[addr] to ACC
STORE = '0011'  # STORE addr: Store ACC value to memory(RAM)[addr]
HALT = '0100'   # HALT: Stop the program
```

### Step 2 — Set up CPU components
Create variables for the CPU's memory and registers.

```python
# Initialize CPU components
memory = ['0000'] * 16  # Memory(RAM) with 16 locations, all starting at 0 (4-bit binary)
ACC = 0                  # Accumulator register
PC = 0                   # Program Counter register
halted = False           # Flag to stop the program
```

### Step 3 — Load the sample program
Put the program instructions and data into memory(RAM).

```python
# Load sample program: LOAD 4, ADD 5, STORE 6, HALT
memory[0] = '00010100'  # LOAD 4 ('0001' + '0100')
memory[1] = '00100101'  # ADD 5 ('0010' + '0101')
memory[2] = '00110110'  # STORE 6 ('0011' + '0110')
memory[3] = '01000000'  # HALT ('0100' + '0000')
memory[4] = '0101'      # Data: 5
memory[5] = '1010'      # Data: 10
memory[6] = '0000'      # Result location: 0
```

### Step 4 — Implement the FDE cycle loop
Use a while loop to repeat the cycle until halted.

```python
while not halted:
    # Fetch: Get the instruction from memory(RAM) at PC
    instruction = memory[PC]
    
    # Decode: Split into opcode and operand
    opcode = instruction[:4]      # First 4 bits
    operand = int(instruction[4:], 2)  # Last 4 bits as integer
    
    # Execute: Do what the instruction says
    if opcode == LOAD:
        ACC = int(memory[operand], 2)
    elif opcode == ADD:
        ACC += int(memory[operand], 2)
    elif opcode == STORE:
        memory[operand] = format(ACC, '04b')
    elif opcode == HALT:
        halted = True
    
    # Increment PC for next instruction
    PC += 1
    
    # Print current state
    print(f"PC: {PC}, ACC: {ACC}, Memory(RAM)[6]: {int(memory[6], 2)}")
```

### Step 5 — Run the program
Put all the code together and run it. You should see the state printed after each cycle.

Full code example:

```python
# Instruction opcodes (4-bit binary)
LOAD = '0001'
ADD = '0010'
STORE = '0011'
HALT = '0100'

# Initialize RAM & CPU
memory = ['0000'] * 16
ACC = 0
PC = 0
halted = False

# Load program
memory[0] = '00010100'  # LOAD 4
memory[1] = '00100101'  # ADD 5
memory[2] = '00110110'  # STORE 6
memory[3] = '01000000'  # HALT
memory[4] = '0101'      # 5
memory[5] = '1010'      # 10
memory[6] = '0000'      # 0

# Run FDE cycle
while not halted:
    instruction = memory[PC]
    opcode = instruction[:4]
    operand = int(instruction[4:], 2)
    
    if opcode == LOAD:
        ACC = int(memory[operand], 2)
    elif opcode == ADD:
        ACC += int(memory[operand], 2)
    elif opcode == STORE:
        memory[operand] = format(ACC, '04b') # convert to binary
    elif opcode == HALT:
        halted = True
    
    PC += 1
    print(f"After cycle: PC={PC}, ACC={ACC}, Memory(RAM)[6]={int(memory[6], 2)}")

print("Program finished!")
```

---

**Example to test:**

Memory(RAM) initial: ['00010000', '00100001', '00110010', '01000000', '0101', '1010', '0000']

```
// '00010000'=LOAD 0, 
// '00100001'=ADD 1, 
// '00110010'=STORE 2,
// '01000000'=HALT, data 5,10,0
```

- Cycle 1: Fetch '00010000', Decode LOAD 0, Execute ACC=5, PC=1
- Cycle 2: Fetch '00100001', Decode ADD 1, Execute ACC=5+10=15, PC=2
- Cycle 3: Fetch '00110010', Decode STORE 2, Execute memory(RAM)[2]='1111', PC=3
- Cycle 4: Fetch '01000000', Decode HALT, Stop

Final: ACC=15, memory(RAM)[2]=15

---

## Extension Activity: Visualize the CPU with Rich and/or Textual

Enhance your CPU simulator by integrating visualization libraries for a more engaging experience:

- **Using Rich** ([Documentation](https://rich.readthedocs.io/en/stable/)): Display the CPU state (registers, memory(RAM)) in colorful tables after each cycle. Use progress bars to represent execution progress or highlight changes in memory(RAM).
- **Using Textual** ([Documentation](https://textual.textualize.io/)): Build an interactive terminal app with live-updating widgets showing the FDE cycle in real-time, allowing step-by-step execution and dynamic memory(RAM) inspection.

This extension promotes advanced Python skills in UI development while deepening understanding of CPU operations through interactive feedback.
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

### Step 1 — Define the instruction set
- LOAD addr: Load value from memory[addr] into accumulator (ACC).
- ADD addr: Add value from memory[addr] to ACC.
- STORE addr: Store ACC value to memory[addr].
- HALT: Stop execution.

### Step 2 — Set up CPU components
- Memory: A list of integers (e.g., 16 locations).
- Registers: ACC = 0, PC = 0 (program counter).
- Load a sample program into memory.

### Step 3 — Implement the FDE cycle
- While not halted:
  - **Fetch**: Get instruction = memory[PC], PC += 1
  - **Decode**: Extract opcode and operand (e.g., opcode = instruction // 10, operand = instruction % 10)
  - **Execute**: Perform the operation based on opcode.
  - Print current state (PC, ACC, memory snapshot).

### Step 4 — Handle operations
- For LOAD: ACC = memory[operand]
- For ADD: ACC += memory[operand]
- For STORE: memory[operand] = ACC
- For HALT: Set halt flag.

### Step 5 — Run and observe
- Initialize memory with program and data.
- Run the cycle and observe changes.

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
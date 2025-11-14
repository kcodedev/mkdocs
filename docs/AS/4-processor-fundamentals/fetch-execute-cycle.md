# Fetch-Execute Cycle

## Introduction

The Fetch-Execute Cycle is the fundamental process by which a CPU retrieves and processes instructions. It consists of a repetitive sequence that forms the basis of program execution.

## Stages of the Fetch-Execute Cycle

### 1. Fetch

- **Purpose**: Retrieve the next instruction from memory
- **Actions**:
  - Copy Program Counter (PC) to Memory Address Register (MAR)
  - Send read signal via control bus
  - Memory places instruction in Memory Data Register (MDR)
  - Copy MDR to Current Instruction Register (CIR)
  - Increment Program Counter (PC)

### 2. Decode

- **Purpose**: Interpret the fetched instruction
- **Actions**:
  - Control Unit decodes the opcode in CIR
  - Identifies operation type and operands
  - Prepares necessary registers and components

### 3. Execute

- **Purpose**: Perform the required operation
- **Actions**:
  - Execute the decoded instruction
  - May involve ALU operations, memory access, or I/O
  - Update status flags and registers as needed

## Register Transfer Notation

Register Transfer Notation (RTN) describes data movement between registers and components using symbolic representation.

### Basic Syntax

- `Register ← Source`: Transfer from source to register
- `Destination ← Register`: Transfer from register to destination
- `Register ← Register op Value`: Operation result to register

### Common RTN Operations

#### Fetch Stage
```
MAR ← PC
MDR ← Memory[MAR]
CIR ← MDR
PC ← PC + 1
```

#### Execute Stage Examples

**Load Operation** (LDA #n - Load accumulator with value n)
```
MAR ← PC
MDR ← Memory[MAR]
CIR ← MDR
PC ← PC + 1
ACC ← MDR
```

**Store Operation** (STA addr - Store accumulator to address)
```
MAR ← PC
MDR ← Memory[MAR]
CIR ← MDR
PC ← PC + 1
MAR ← MDR
MDR ← ACC
Memory[MAR] ← MDR
```

**Add Operation** (ADD addr - Add value at address to accumulator)
```
MAR ← PC
MDR ← Memory[MAR]
CIR ← MDR
PC ← PC + 1
MAR ← MDR
MDR ← Memory[MAR]
ACC ← ACC + MDR
```

## Detailed Cycle Breakdown

### Complete Fetch-Execute Cycle

1. **Fetch Instruction**
   - MAR ← PC
   - MDR ← Memory[MAR]
   - CIR ← MDR
   - PC ← PC + 1

2. **Decode Instruction**
   - Control Unit interprets CIR
   - Determines operation and addressing mode

3. **Fetch Operands** (if needed)
   - MAR ← Address from CIR
   - MDR ← Memory[MAR]

4. **Execute Operation**
   - Perform ALU operation or data movement
   - Update registers and memory as required

5. **Store Results** (if needed)
   - Memory[MAR] ← MDR or register content

## Timing Considerations

- **Clock Cycles**: Each stage takes one or more clock cycles
- **Pipelining**: Modern CPUs overlap multiple instruction cycles
- **Interrupts**: Can occur between cycles

## Variations

### Different Instruction Types

- **Memory Reference**: Access memory locations
- **Register Reference**: Operate on registers only
- **I/O Instructions**: Communicate with peripherals

### Addressing Modes

- **Immediate**: Operand is part of instruction
- **Direct**: Operand address is part of instruction
- **Indirect**: Address points to location containing operand address

## Importance

The Fetch-Execute Cycle is the heartbeat of computer operation, enabling sequential program execution and forming the basis for all computing tasks.
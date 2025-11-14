# Assembly Language Instruction Groups

## Introduction

Assembly language instructions are organized into functional groups based on their purpose and operation. Each group serves specific computational needs and programming requirements.

## Data Movement Instructions

### Purpose

- Transfer data between registers, memory, and I/O devices
- Essential for data manipulation and storage

### Common Instructions

- **MOV/MOVE**: Copy data from source to destination
  - `MOV AX, BX` - Copy BX to AX
  - `MOV AL, [1000]` - Load from memory address 1000

- **LOAD/LDA**: Load data into registers
  - `LDA AX, VALUE` - Load VALUE into AX

- **STORE/STA**: Store register contents to memory
  - `STA RESULT, AX` - Store AX to RESULT

- **PUSH/POP**: Stack operations
  - `PUSH AX` - Push AX onto stack
  - `POP BX` - Pop from stack to BX

### Applications

- Variable assignment
- Parameter passing
- Memory management

## Input and Output Instructions

### Purpose

- Handle communication with peripheral devices
- Transfer data between CPU and external devices

### Common Instructions

- **IN**: Read from input port
  - `IN AL, 60H` - Read keyboard port

- **OUT**: Write to output port
  - `OUT 61H, AL` - Write to speaker port

- **I/O with Memory Mapping**
  - Treat I/O as memory locations
  - Use standard MOV instructions

### Applications

- Keyboard input
- Display output
- Peripheral device control

## Arithmetic Instructions

### Purpose

- Perform mathematical calculations
- Support numerical computations

### Common Instructions

- **ADD**: Addition
  - `ADD AX, BX` - AX = AX + BX

- **SUB**: Subtraction
  - `SUB CX, 5` - CX = CX - 5

- **MUL/IMUL**: Multiplication
  - `MUL BX` - AX = AX * BX (unsigned)
  - `IMUL DX` - DX:AX = AX * DX (signed)

- **DIV/IDIV**: Division
  - `DIV BX` - AX = AX / BX (quotient), DX = remainder

- **INC/DEC**: Increment/Decrement
  - `INC AX` - AX = AX + 1
  - `DEC BX` - BX = BX - 1

### Applications

- Mathematical calculations
- Counter operations
- Address calculations

## Unconditional and Conditional Instructions

### Unconditional Jump Instructions

- **Purpose**: Transfer control to different program location
- **Always Execute**: No conditions checked

- **JMP**: Unconditional jump
  - `JMP LABEL` - Jump to LABEL

- **CALL**: Subroutine call
  - `CALL SUB1` - Call subroutine SUB1

- **RET**: Return from subroutine
  - `RET` - Return to caller

### Conditional Jump Instructions

- **Purpose**: Transfer control based on conditions
- **Condition Dependent**: Execute only if condition met

- **JZ/JE**: Jump if zero/equal
  - `JZ LOOP` - Jump if zero flag set

- **JNZ/JNE**: Jump if not zero/not equal
  - `JNZ CONTINUE` - Jump if zero flag clear

- **JG/JNLE**: Jump if greater
  - `JG POSITIVE` - Jump if greater than

- **JL/JNGE**: Jump if less
  - `JL NEGATIVE` - Jump if less than

### Applications

- Loops and iteration
- Decision making
- Error handling

## Compare Instructions

### Purpose

- Compare two values and set condition flags
- Enable conditional operations without modifying data

### Common Instructions

- **CMP**: Compare operands
  - `CMP AX, BX` - Compare AX with BX
  - Sets flags: Zero, Carry, Sign, Overflow

- **TEST**: Test bits (AND without storing result)
  - `TEST AL, 80H` - Test if bit 7 is set
  - Sets Zero flag based on result

### Flag Operations

- **Zero Flag (Z)**: Set if result is zero
- **Carry Flag (C)**: Set if unsigned overflow
- **Sign Flag (S)**: Set if result negative
- **Overflow Flag (O)**: Set if signed overflow

### Applications

- Conditional branching
- Loop control
- Data validation

## Instruction Set Architecture

### Orthogonal Instruction Set

- Consistent operand usage across instructions
- Regular addressing modes
- Predictable behavior

### Complex Instruction Set (CISC)

- Variable-length instructions
- Many addressing modes
- Complex operations in single instruction

### Reduced Instruction Set (RISC)

- Fixed-length instructions
- Limited addressing modes
- Simple operations, higher speed

## Programming Considerations

### Instruction Selection

- **Efficiency**: Choose appropriate instructions for task
- **Readability**: Use clear, meaningful operations
- **Optimization**: Balance speed vs. code size

### Common Patterns

- **Loop Construction**: Compare + conditional jump
- **Decision Making**: Compare + conditional jump
- **Data Processing**: Load + operate + store

Understanding instruction groups enables effective assembly language programming and efficient code generation.
# Addressing Modes in Assembly Language

## Introduction

Addressing modes determine how operands are specified in assembly language instructions. They define how the CPU calculates the effective address of data or the next instruction.

## Immediate Addressing

### Description

- **Definition**: Operand value is part of the instruction
- **Format**: Constant value directly in instruction
- **Advantage**: Fast access, no memory reference

### Examples

- `MOV AX, 5` - Load 5 directly into AX
- `ADD BX, 10` - Add 10 to BX
- `MOV AL, 'A'` - Load ASCII 'A' (65) into AL

### Characteristics

- **No Memory Access**: Value comes from instruction stream
- **Limited Range**: Size depends on instruction format
- **Speed**: Fastest addressing mode

## Direct Addressing

### Description

- **Definition**: Operand address is part of the instruction
- **Format**: Memory address specified directly
- **Advantage**: Simple and straightforward

### Examples

- `MOV AX, [1000]` - Load from memory address 1000
- `STA 2000, BX` - Store BX to address 2000
- `LDA VALUE` - Load from address labeled VALUE

### Characteristics

- **Fixed Address**: Address hardcoded in instruction
- **Memory Access**: Requires one memory read/write
- **Global Variables**: Suitable for fixed memory locations

## Indirect Addressing

### Description

- **Definition**: Instruction contains address of a pointer
- **Format**: Register or memory location contains the actual address
- **Advantage**: Dynamic address calculation

### Examples

- `MOV AX, [BX]` - BX contains address, load from that address
- `STA [SI], CX` - SI points to destination address
- `LDA @PTR` - PTR contains address of data

### Characteristics

- **Pointer Usage**: Address stored in register/memory
- **Flexibility**: Can change target without modifying instruction
- **Two Memory Accesses**: One for pointer, one for data

## Indexed Addressing

### Description

- **Definition**: Base address plus offset from index register
- **Format**: Base + Index register value
- **Advantage**: Efficient array processing

### Examples

- `MOV AX, [BX + 4]` - Load from address BX + 4
- `STA ARRAY[SI], DX` - Store to ARRAY base + SI offset
- `LDA TABLE + CX` - Load from TABLE + CX

### Characteristics

- **Array Access**: Perfect for arrays and tables
- **Displacement**: Constant offset added to index
- **Scalability**: Easy to access array elements

## Relative Addressing

### Description

- **Definition**: Address relative to current instruction pointer
- **Format**: Offset from Program Counter
- **Advantage**: Position-independent code

### Examples

- `JMP +10` - Jump forward 10 bytes
- `CALL -5` - Call backward 5 bytes
- `JZ LOOP` - Jump to LOOP label (relative offset)

### Characteristics

- **PC-Relative**: Offset from current instruction
- **Relocatable Code**: Works when program moves in memory
- **Short Jumps**: Limited range but efficient

## Addressing Mode Comparison

| Mode | Syntax Example | Memory Accesses | Use Case |
|------|----------------|-----------------|----------|
| Immediate | `MOV AX, 5` | 0 | Constants |
| Direct | `MOV AX, [1000]` | 1 | Global variables |
| Indirect | `MOV AX, [BX]` | 2 | Pointers |
| Indexed | `MOV AX, [BX+4]` | 1 | Arrays |
| Relative | `JMP +10` | 0 | Branches |

## Practical Applications

### Data Structures

- **Arrays**: Indexed addressing for element access
- **Structures**: Base + offset for field access
- **Linked Lists**: Indirect addressing for node traversal

### Program Control

- **Loops**: Indexed for array iteration
- **Subroutines**: Relative for local jumps
- **Position Independence**: Relative addressing

## Implementation Considerations

### Instruction Encoding

- **Mode Bits**: Part of opcode specify addressing mode
- **Operand Size**: Varies by mode and data size
- **Address Calculation**: Hardware performs effective address computation

### Performance Impact

- **Immediate**: Fastest, no memory access
- **Direct**: Single memory access
- **Indirect/Indexed**: Additional calculations
- **Relative**: Efficient for local branches

### Programming Best Practices

- **Choose Appropriate Mode**: Match mode to data access pattern
- **Optimize for Speed**: Prefer immediate/direct when possible
- **Use for Flexibility**: Indexed/indirect for dynamic access

Understanding addressing modes is crucial for efficient assembly language programming and optimizing memory access patterns.
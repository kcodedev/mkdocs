# Two-Pass Assembler

## Introduction

A two-pass assembler processes assembly language source code in two distinct phases. This approach resolves forward references and generates efficient machine code.

## Stages of the Assembly Process

### Pass 1: Symbol Resolution

**Purpose**: Build symbol table and resolve symbolic references

**Activities**:

1. **Read Source Code**
   - Process assembly instructions line by line
   - Identify labels, mnemonics, and operands

2. **Build Symbol Table**
   - Record addresses of all labels
   - Store constants and variables
   - Calculate memory locations

3. **Resolve Forward References**
   - Identify symbols used before definition
   - Reserve space for unresolved references
   - Generate intermediate code with placeholders

4. **Calculate Memory Requirements**
   - Determine total program size
   - Assign addresses to instructions and data

### Pass 2: Code Generation

**Purpose**: Generate final machine code using symbol table

**Activities**:

1. **Translate Instructions**
   - Convert mnemonics to opcodes
   - Resolve operands using symbol table
   - Generate binary machine code

2. **Resolve Addresses**
   - Replace placeholders with actual addresses
   - Apply offset calculations
   - Handle relative and absolute addressing

3. **Generate Output**
   - Create object file with machine code
   - Include symbol table for linking
   - Add relocation information

## Example: Simple Assembly Program

### Source Code
```
START:  LDA #5      ; Load 5 into accumulator
        STA VALUE   ; Store to VALUE
        LDA VALUE   ; Load from VALUE
        ADD #10     ; Add 10
        STA RESULT  ; Store result
        HLT         ; Halt

VALUE:  DS 1        ; Reserve 1 word
RESULT: DS 1        ; Reserve 1 word
```

### Pass 1 Processing

**Symbol Table Building**:
- START: 0x0000
- VALUE: 0x0006 (after 3 instructions + HLT)
- RESULT: 0x0007

**Intermediate Code**:
- Address 0x0000: LDA #5
- Address 0x0001: STA [VALUE] (placeholder)
- Address 0x0002: LDA [VALUE] (placeholder)
- Address 0x0003: ADD #10
- Address 0x0004: STA [RESULT] (placeholder)
- Address 0x0005: HLT
- Address 0x0006: VALUE (data)
- Address 0x0007: RESULT (data)

### Pass 2 Processing

**Final Machine Code** (assuming simple instruction set):
- 0x0000: 0x15 (LDA immediate 5)
- 0x0001: 0x26 (STA direct, address 0x0006)
- 0x0002: 0x16 (LDA direct, address 0x0006)
- 0x0003: 0x35 (ADD immediate 10)
- 0x0004: 0x27 (STA direct, address 0x0007)
- 0x0005: 0x00 (HLT)
- 0x0006: 0x00 (VALUE initialized to 0)
- 0x0007: 0x00 (RESULT initialized to 0)

## Benefits of Two-Pass Assembly

### Forward Reference Resolution

- **Problem Solved**: Labels used before definition
- **Method**: First pass collects all symbols, second pass resolves

### Efficiency

- **Single Pass Limitation**: Cannot resolve forward jumps
- **Two-Pass Advantage**: Complete symbol information available

### Error Detection

- **Symbol Resolution**: Catches undefined symbols
- **Address Calculation**: Verifies memory constraints

## Detailed Two-Pass Process

### Pass 1 Algorithm

```
Initialize symbol table
Initialize location counter = 0
For each source line:
    If label present:
        Add label:location to symbol table
    If instruction:
        Generate intermediate code
        Increment location counter
    If directive:
        Process directive (DS, DB, etc.)
        Update location counter
Handle forward references with placeholders
```

### Pass 2 Algorithm

```
Reset location counter = 0
For each intermediate instruction:
    Translate mnemonic to opcode
    Resolve operands using symbol table
    Generate machine code
    Write to output file
    Increment location counter
Generate symbol table for linker
Add relocation information
```

## Applications

### Simple Assembly Programs

- **Educational Examples**: Demonstrate basic concepts
- **Boot Loaders**: Small initialization code
- **Embedded Systems**: Resource-constrained environments

### Complex Programs

- **Modular Code**: Multiple source files
- **Libraries**: Reusable code segments
- **Large Applications**: Multi-pass optimization

## Modern Variations

### One-Pass Assemblers

- **Limitation**: Cannot handle forward references
- **Use**: Simple programs, backpatching

### Multi-Pass Assemblers

- **Optimization**: Additional passes for code improvement
- **Complex Architectures**: Advanced instruction scheduling

The two-pass assembler provides a robust method for translating assembly language to machine code while handling the challenges of symbolic programming.
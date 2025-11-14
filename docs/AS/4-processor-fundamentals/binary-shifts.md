# Binary Shifts

## Introduction

Binary shifts are fundamental operations that move bits within a binary number, either left or right. These operations are essential for efficient arithmetic, data manipulation, and hardware control.

## Types of Shifts

### Logical Shifts

Logical shifts treat the number as a sequence of bits, with no special consideration for sign.

#### Left Shift (LSL)

- **Operation**: Bits move left by specified positions
- **Right Fill**: Zeros fill from the right
- **Effect**: Multiplication by powers of 2
- **Carry**: Leftmost bit may be lost to carry flag

**Example (8-bit):**
```
Original: 00001100 (12)
LSL #1:   00011000 (24)  - multiply by 2
LSL #2:   00110000 (48)  - multiply by 4
LSL #3:   01100000 (96)  - multiply by 8
```

#### Right Shift (LSR)

- **Operation**: Bits move right by specified positions
- **Left Fill**: Zeros fill from the left
- **Effect**: Division by powers of 2 (unsigned)
- **Carry**: Rightmost bit may be lost to carry flag

**Example (8-bit):**
```
Original: 00001100 (12)
LSR #1:   00000110 (6)   - divide by 2
LSR #2:   00000011 (3)   - divide by 4
LSR #3:   00000001 (1)   - divide by 8
```

### Arithmetic Shifts

Arithmetic shifts preserve the sign bit, making them suitable for signed numbers.

#### Arithmetic Left Shift

- **Same as Logical Left Shift**
- **Sign Preservation**: May change sign if bit 6 (for 8-bit) becomes 1

#### Arithmetic Right Shift (ASR)

- **Operation**: Bits move right, sign bit preserved
- **Left Fill**: Sign bit fills from the left
- **Effect**: Division by powers of 2 (signed)
- **Sign Preservation**: Maintains positive/negative status

**Example (8-bit signed):**
```
Positive: 00001100 (+12)
ASR #1:   00000110 (+6)   - divide by 2

Negative: 11110100 (-12)
ASR #1:   11111010 (-6)   - divide by 2
```

### Cyclic Shifts (Rotate)

Cyclic shifts move bits in a circular fashion, with no bits lost.

#### Left Rotate

- **Operation**: Bits move left, leftmost bit moves to rightmost position
- **No Loss**: All bits preserved
- **Carry**: May affect carry flag

**Example:**
```
Original: 10110001
Rotate L: 01100011  (bit 7 moves to bit 0)
```

#### Right Rotate

- **Operation**: Bits move right, rightmost bit moves to leftmost position
- **No Loss**: All bits preserved
- **Carry**: May affect carry flag

**Example:**
```
Original: 10110001
Rotate R: 11011000  (bit 0 moves to bit 7)
```

## Assembly Instructions

### LSL Instruction

```
LSL #n    ; Logical shift left by n positions
; Example: LSL #2 shifts bits left by 2, zeros fill right
```

### LSR Instruction

```
LSR #n    ; Logical shift right by n positions
; Example: LSR #1 shifts bits right by 1, zeros fill left
```

## Applications

### Arithmetic Operations

- **Fast Multiplication**: Left shifts for multiplying by 2^n
- **Fast Division**: Right shifts for dividing by 2^n
- **Power Calculations**: Efficient computation of powers of 2

### Data Manipulation

- **Bit Extraction**: Shift to isolate specific bits
- **Bit Insertion**: Shift and mask to place bits
- **Data Packing**: Compress multiple values into single word

### Hardware Control

- **Serial Communication**: Shift bits for serial data transmission
- **Display Control**: Shift data for LED displays
- **Motor Control**: Position encoding and decoding

### Algorithm Optimization

- **Graphics**: Fast pixel manipulation
- **Cryptography**: Data scrambling operations
- **Checksums**: CRC calculation algorithms

## Performance Considerations

- **Speed**: Shift operations are very fast (single cycle)
- **Hardware Support**: Dedicated shift units in modern CPUs
- **Overflow**: Monitor carry flag for overflow conditions
- **Precision**: Logical vs arithmetic shifts affect signed operations

## Common Pitfalls

- **Sign Loss**: Using logical shift on signed numbers
- **Overflow**: Not checking carry flag after shifts
- **Word Size**: Different behavior on different architectures
- **Endianness**: Bit ordering considerations

Binary shifts provide powerful and efficient methods for data manipulation in low-level programming.
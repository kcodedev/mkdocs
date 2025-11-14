# Logical Operations

## Introduction

Logical operations perform bit-wise manipulation of binary data. These operations compare or combine corresponding bits in two operands, producing a result based on logical rules.

## Bit-wise AND Operation

### Truth Table

| Bit A | Bit B | A AND B |
|-------|-------|---------|
| 0     | 0     | 0       |
| 0     | 1     | 0       |
| 1     | 0     | 0       |
| 1     | 1     | 1       |

### Assembly Instructions

```
AND #n        ; AND accumulator with immediate value
AND <address> ; AND accumulator with memory location
```

### Examples

**Clear specific bits:**
```
ACC = 11111111 (255)
AND #11110000 (240)
Result: 11110000 (240) - bits 0-3 cleared
```

**Test bit pattern:**
```
ACC = 10101010 (170)
AND #00001111 (15)
Result: 00001010 (10) - extract lower 4 bits
```

## Bit-wise OR Operation

### Truth Table

| Bit A | Bit B | A OR B |
|-------|-------|--------|
| 0     | 0     | 0      |
| 0     | 1     | 1      |
| 1     | 0     | 1      |
| 1     | 1     | 1      |

### Assembly Instructions

```
OR #n         ; OR accumulator with immediate value
OR <address>  ; OR accumulator with memory location
```

### Examples

**Set specific bits:**
```
ACC = 00000000 (0)
OR #00001111 (15)
Result: 00001111 (15) - bits 0-3 set
```

**Combine bit patterns:**
```
ACC = 10100000 (160)
OR #00001010 (10)
Result: 10101010 (170) - combine patterns
```

## Bit-wise XOR Operation

### Truth Table

| Bit A | Bit B | A XOR B |
|-------|-------|---------|
| 0     | 0     | 0       |
| 0     | 1     | 1       |
| 1     | 0     | 1       |
| 1     | 1     | 0       |

### Assembly Instructions

```
XOR #n        ; XOR accumulator with immediate value
XOR <address> ; XOR accumulator with memory location
```

### Examples

**Toggle specific bits:**
```
ACC = 10101010 (170)
XOR #00001111 (15)
Result: 10100101 (165) - bits 0-3 toggled
```

**Compare patterns (find differences):**
```
ACC = 11110000 (240)
XOR #11111111 (255)
Result: 00001111 (15) - inverted lower bits
```

## Logical vs Arithmetic Operations

### Logical Operations

- **Bit-wise**: Each bit independent
- **No Carry**: Operations don't affect carry flag
- **Masking**: Perfect for bit manipulation
- **Flags**: Only zero and negative flags affected

### Arithmetic Operations

- **Whole Number**: Treat as complete values
- **Carry Propagation**: Addition/subtraction carry between bits
- **Overflow**: Signed arithmetic overflow detection
- **All Flags**: Carry, zero, negative, overflow affected

## Common Applications

### Data Masking

**Extract specific bits:**
```
; Extract bits 4-7 from a byte
LDA DATA
AND #11110000  ; Mask upper 4 bits
LSR #4         ; Shift to lower position
```

### Flag Management

**Set multiple flags:**
```
; Set bits 1, 3, 5 in status register
LDA STATUS
OR #00101010   ; Set bits 1, 3, 5
STA STATUS
```

### Data Encryption

**Simple XOR encryption:**
```
; Encrypt data with key
LDA PLAIN_TEXT
XOR KEY
STA ENCRYPTED
```

## Instruction Formats

### Immediate Addressing

```
AND #decimal   ; e.g., AND #15
AND Bbinary    ; e.g., AND B00001111
AND &hex       ; e.g., AND &0F
```

### Direct Addressing

```
AND <address>  ; e.g., AND MASK_VALUE
AND <label>    ; e.g., AND STATUS_BITS
```

## Performance Characteristics

- **Speed**: Single-cycle operations
- **Hardware**: Dedicated logic circuits
- **Power**: Low power consumption
- **Predictability**: Deterministic results

## Best Practices

### Code Clarity

- **Comments**: Explain mask purposes
- **Constants**: Define masks as named constants
- **Modularity**: Separate masking logic

### Error Prevention

- **Mask Validation**: Ensure masks match data size
- **Bit Position**: Double-check bit positions
- **Overflow**: Consider result size requirements

### Optimization

- **Pre-computed Masks**: Store frequently used masks
- **Combined Operations**: AND/OR in single instructions
- **Shift Integration**: Combine with shift operations

Logical operations provide the foundation for bit-level data manipulation in assembly language programming.
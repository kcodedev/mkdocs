# Half Adders and Full Adders

This document covers the production of truth tables for logic circuits, specifically focusing on half adders and full adders. These are fundamental components in digital arithmetic circuits used for binary addition.

## Half Adder

A half adder is a digital circuit that adds two single-bit binary numbers (A and B). It produces two outputs: the sum (S) and the carry (C).

### Truth Table for Half Adder

| A | B | Sum (S) | Carry (C) |
|---|---|---------|-----------|
| 0 | 0 | 0       | 0         |
| 0 | 1 | 1       | 0         |
| 1 | 0 | 1       | 0         |
| 1 | 1 | 0       | 1         |

### Logic Expressions
- Sum (S) = A ⊕ B (XOR operation)
- Carry (C) = A ∧ B (AND operation)

### Circuit Diagram
![Half Adder Circuit](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Half_Adder.svg/640px-Half_Adder.svg.png)

## Full Adder

A full adder is a digital circuit that adds three single-bit binary numbers: two input bits (A and B) and a carry-in bit (Cin). It produces two outputs: the sum (S) and the carry-out (Cout).

### Truth Table for Full Adder

| A | B | Cin | Sum (S) | Carry-out (Cout) |
|---|---|-----|---------|------------------|
| 0 | 0 | 0   | 0       | 0                |
| 0 | 0 | 1   | 1       | 0                |
| 0 | 1 | 0   | 1       | 0                |
| 0 | 1 | 1   | 0       | 1                |
| 1 | 0 | 0   | 1       | 0                |
| 1 | 0 | 1   | 0       | 1                |
| 1 | 1 | 0   | 0       | 1                |
| 1 | 1 | 1   | 1       | 1                |

### Logic Expressions
- Sum (S) = A ⊕ B ⊕ Cin (XOR of all three inputs)
- Carry-out (Cout) = (A ∧ B) ∨ (Cin ∧ (A ⊕ B)) (OR of (A AND B) and (Cin AND (A XOR B)))

### Circuit Diagram
![Full Adder Circuit](https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Full_Adder_Blocks.svg/1024px-Full_Adder_Blocks.svg.png)

## Key Differences

- **Half Adder**: Adds two bits, no carry-in consideration
- **Full Adder**: Adds three bits, including carry-in from previous addition
- Full adders can be cascaded to create multi-bit adders, while half adders are typically used only for the least significant bit

## Applications

- Half adders are used in basic arithmetic operations and can be combined to form full adders
- Full adders are essential components in ALU (Arithmetic Logic Unit) of processors
- Both are fundamental building blocks for more complex arithmetic circuits like subtractors and multipliers
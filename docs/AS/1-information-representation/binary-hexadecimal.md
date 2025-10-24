# Binary and Hexadecimal Number Systems

In computer science, we often work with different number systems beyond the familiar decimal (base 10) system. Two important ones are **binary** (base 2) and **hexadecimal** (base 16). Understanding these systems, their place values, and how to convert between them is essential for topics like data representation and programming.

## 1. Binary Number System (Base 2)

Binary is the foundation of all computer operations because computers use electronic switches that are either on (1) or off (0).

### Place Values in Binary

In binary, each digit (bit) represents a power of 2. Starting from the right, the place values are powers of 2.

| Power of 2            | 2^7 | 2^6 | 2^5 | 2^4 | 2^3 | 2^2 | 2^1 | 2^0 |
|-----------------------|---|---|---|---|---|---|---|---|
| Decimal Value         | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

For example, the binary number 1011₂ (where the subscript ₂ indicates base 2) can be converted to decimal as follows:

| Binary Digit | 1 | 0 | 1 | 1 |
|--------------|---|---|---|---|
| Power of 2   | 8 | 4 | 2 | 1 |
| Result       | 8 | 0 | 2 | 1 |

Total: 8 + 0 + 2 + 1 = 11₁₀

### Converting Denary to Binary

To convert a decimal number to binary, use repeated division by 2 and record the remainders.

**Example: Convert 13₁₀ to binary**

| Step | Number | ÷ 2 | Quotient | Remainder |
|------|--------|-----|----------|-----------|
| 1    | 13     | 13 ÷ 2 | 6        | 1         |
| 2    | 6      | 6 ÷ 2  | 3        | 0         |
| 3    | 3      | 3 ÷ 2  | 1        | 1         |
| 4    | 1      | 1 ÷ 2  | 0        | 1         |

Reading the remainders from bottom to top: 1101₂

**Practice:** Try converting 25₁₀ to binary. (Answer: 11001₂)

### Converting Binary to Denary

Multiply each bit by its place value and sum them up.

**Example: Convert 1010₂ to decimal**

| Binary Digit | 1 | 0 | 1 | 0 |
|--------------|---|---|---|---|
| Power of 2   | 8 | 4 | 2 | 1 |
| Result       | 8 | 0 | 2 | 0 |

Total: 10₁₀

## 2. Hexadecimal Number System (Base 16)

Hexadecimal is useful for representing large binary numbers in a more compact form. It uses digits 0-9 and letters A-F (where A=10, B=11, C=12, D=13, E=14, F=15).

### Place Values in Hexadecimal

Each digit represents a power of 16.

| Power of 16           | 16^4 | 16^3 | 16^2 | 16^1 | 16^0 |
|-----------------------|---|---|---|---|---|
| Decimal Value         | 65536 | 4096 | 256 | 16 | 1 |

For example, the hexadecimal number 2A₁₆ :

| Hex Digit | 2 | A |
|-----------|---|---|
| Power of 16 | 16 | 1 |
| Calculation | 2×16 | 10×1 |
| Result    | 32 | 10 |

Total: 32 + 10 = 42₁₀

### Converting Denary to Hexadecimal

Use repeated division by 16 and record the remainders. Convert remainders 10-15 to A-F.

**Example: Convert 255₁₀ to hexadecimal**

| Step | Number | ÷ 16 | Quotient | Remainder | Hex Remainder |
|------|--------|------|----------|-----------|---------------|
| 1    | 255    | 255 ÷ 16 | 15       | 15        | F             |
| 2    | 15     | 15 ÷ 16  | 0        | 15        | F             |

Reading remainders: FF₁₆

**Practice:** Convert 100₁₀ to hex. (Answer: 64₁₆)

### Converting Hexadecimal to Denary

Multiply each digit by its place value.

**Example: Convert 1A3₁₆ to decimal**

| Hex Digit | 1 | A | 3 |
|-----------|---|---|---|
| Power of 16 | 256 | 16 | 1 |
| Calculation | 1×256 | 10×16 | 3×1 |
| Result    | 256 | 160 | 3 |

Total: 256 + 160 + 3 = 419₁₀

## 3. Conversions Between Binary and Hexadecimal

Since 16 = 2^4, each hex digit corresponds to exactly 4 binary digits (nibbles). This makes conversions straightforward.

### Binary to Hexadecimal

Group the binary digits into sets of 4 from the right, and convert each group to a hex digit.

**Example: Convert 11010110₂ to hex**

| Binary Group | 1101 | 0110 |
|--------------|------|------|
| Decimal      | 13   | 6    |
| Hex          | D    | 6    |

Result: D6₁₆

### Hexadecimal to Binary

Convert each hex digit to 4 binary digits.

**Example: Convert A5₁₆ to binary**

| Hex Digit | A | 5 |
|-----------|---|---|
| Decimal   | 10 | 5 |
| Binary    | 1010 | 0101 |

Result: 10100101₂

## Summary and Tips

- **Binary (Base 2):** Uses 0 and 1; place values are powers of 2.
- **Hexadecimal (Base 16):** Uses 0-9, A-F; place values are powers of 16.
- **Key Conversions:**
  - Denary ↔ Binary: Division/multiplication by 2.
  - Denary ↔ Hex: Division/multiplication by 16.
  - Binary ↔ Hex: Group in 4s or expand to 4 bits.
- Practice with small numbers first, and remember that leading zeros don't change the value (e.g., 0011₂ = 11₂).

For more practice, try converting numbers like 42₁₀ to both binary and hex, or vice versa!
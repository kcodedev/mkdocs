# Negative Binary Numbers: Two's Complement

Negative binary numbers are represented using a system called **two's complement**. 

This method allows computers to perform arithmetic operations on negative numbers efficiently. 

Two's complement represents negative numbers by inverting the bits of the positive equivalent and adding 1.

## The Most Significant Bit (MSB)

In two's complement, the most significant bit (MSB) acts as the sign bit:

- 0 indicates a positive number (or zero).
- 1 indicates a negative number.

## Conversion

### Method 1: Use place values

In this method, we directly assign place values to each bit, where the MSB has a negative weight. For example, in an 8-bit system:

| Bit Position | 7 (MSB) | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|--------------|----------|----|----|----|----|----|----|----------|
| Place Value  | -128    | 64 | 32 | 16 | 8  | 4  | 2  | 1        |
| Binary (-5)  | 1        | 1  | 1  | 1  | 1  | 0  | 1  | 1        |

### Method 2: Invert bits and +1

| Step | Binary Representation |
|------|-----------------------|
| Positive 5 in binary | 00000101 |
| Invert bits | 11111010 |
| Add 1 | 11111011 |

After you could check your work as follows:

Total: -128 + 64 + 32 + 16 + 8 + 0 + 2 + 1 = -128 + 123 = -5



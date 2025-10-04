# 🧮 Binary Floating-Point Real Numbers

Binary floating-point representation is a method of storing **real numbers** (numbers with fractional parts) in binary format, allowing computers to handle a wide range of values, including very small and very large numbers.

---

## A-Level Format of Binary Floating-Point Numbers

For A-Level a binary floating-point number consists of **two parts** both typically in **two's complement**:

1. **Mantissa (M)** → Holds the actual digits of the number in binary
2. **Exponent (E)** → Determines how far the binary point is shifted 


## Two’s Complement recap

Example: 4 bits in two's complement:

- `0111` = +7  
- `1000` = -8  
- `1111` = -1  

This allows both positive and negative exponents (for representing very large and very small numbers).

---

## 🧮 Effect of Changing Mantissa and Exponent Sizes

- **More mantissa bits** → Higher **precision** (more accurate numbers)
- **More exponent bits** → Larger **range** (can represent bigger or smaller numbers)

| Mantissa Bits | Exponent Bits | Effect |
|---------------|--------------|--------|
| Large         | Small        | High precision, small range |
| Small         | Large        | Low precision, large range  |

---

## 🔄 Binary Floating-Point → Decimal

Example:
Suppose we have `11010010` with 4 bits for the mantissa and 4 bits for the exponent:
```
Mantissa: 1.101
Exponent: 0010  
```
Step 1️⃣: Convert exponent:
`0010 → 2`

Step 2️⃣: Shift binary point:
`1.101 → 110.1`

Step 3️⃣: Convert to denary:
`110.1 → 4 + 2 + 0.5`

✅ Final Value: 6.5

---

## 🔄 Decimal → Binary Floating-Point

Convert `+1.5625` to normalised floating-point representation. 12 bits for mantissa 4 bits for the exponent:

Step 1️⃣: Convert to binary:  
`1.5625 → 1 + 0.5 + 0.0625 → 1.1001`  

Step 2️⃣: Shift binary point:  
`1.1001 → 0.11001 x 2¹` so the exponent is 1  

Step 3️⃣: Write out the binary (mantissa || exponent) :  
`0.11001000000 || 0001` 

✅ Final Value: **011001000000 0001**

---

## 🧠 Summary
- Floating-point allows storage of **very large** and **very small** numbers.
- **Two’s complement** can be used for the exponent to handle negative powers.
- **Precision** depends on mantissa size; **range** depends on exponent size.


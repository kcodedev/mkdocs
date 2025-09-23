# Floating-Point Converter Problem 🐍

**Task:**  
Write a Python program to convert a binary floating-point number into its decimal value.

The floating-point representation has:

- **6 bits for the mantissa** (two’s complement)
- **4 bits for the exponent** (two’s complement)

Your program should:

1. Extract the mantissa and exponent from the binary input.
2. Convert the exponent from binary (two’s complement) to an integer.
3. Apply the exponent to shift the binary point left or right.
4. Calculate and output the final denary value.


---

## Step-by-Step Guidance

### Step 1 — Convert the exponent
- Take the last 4 bits as the exponent.
- Convert from binary to decimal using two’s complement rules.

### Step 2 — Position the binary point
- Take the first 6 bits as the mantissa.
- Place the binary point immediately after the sign bit.
- Shift the point left or right depending on the exponent value.

### Step 3 — Calculate the decimal value
- You need to calculate the place values and for each occurance of a `1` and then sum those to arrive at the final answer.

---

**Example to test:**  
Binary input: `0110101110`

- Mantissa bits: `011010`
- Exponent bits: `1110`

The exponent value of -2 tells us to shift the decimal point in the binary mantissa two places to the left.

- Original binary mantissa: `0.11010`
- Shifted binary number: `0.0011010`

Multiply the 1's by their place value and sum to get `0.203125`

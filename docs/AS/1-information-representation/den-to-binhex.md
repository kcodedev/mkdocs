#  Denary to Binary/Hex Calculator 🐍

In this exercise, you'll create a Python program that takes a decimal (denary) number as input and converts it to both binary and hexadecimal formats. This will help reinforce your understanding of number systems and basic Python programming concepts.

## Knowledge Required

Before starting, make sure you're familiar with:

- Getting user input using `input()`
- Using the modulo operator (`%`) to get remainders
- Using the floor division operator (`//`) to get quotients
- Adding elements to Python lists using `append()`
- Looping through lists with `for` loops
- String manipulation, such as joining lists into strings

## Step-by-Step Guide

### 1. Plan the Program

- Prompt the user to enter a decimal number.
- For binary conversion: Use repeated division by 2, collecting remainders in a list.
- For hexadecimal conversion: Use repeated division by 16, collecting remainders and converting 10-15 to A-F.
- Reverse the lists (since we build them from least significant digit) and join into strings.

### 2. Implement Binary Conversion

```python
def denary_to_binary(n):
    if n == 0:
        return '0'
    binary = []
    while n > 0:
        pass
    #
    #
```

### 3. Implement Hexadecimal Conversion

For hexadecimal:

```python
def denary_to_hex(n):
    if n == 0:
        return '0'
    hex_digits = '0123456789ABCDEF'
    hex_list = []
    while n > 0:
        pass
    #
    #
```

### 4. Complete Program

Combine everything into a full program:

```python
# Get user input
number = int(input("Enter a decimal number: "))
if number < 0:
    print("Please enter a non-negative integer.")
else:
    binary_result = denary_to_binary(number)
    hex_result = denary_to_hex(number)
    print(f"Binary: {binary_result}")
    print(f"Hexadecimal: {hex_result}")
```

### 5. Testing Your Program

Run the program and test with these values:

- Input: 13 → Expected Binary: 1101, Hex: D
- Input: 255 → Expected Binary: 11111111, Hex: FF
- Input: 42 → Expected Binary: 101010, Hex: 2A

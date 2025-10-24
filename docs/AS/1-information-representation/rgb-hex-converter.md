# 🐍 Exercise: Build an RGB to Hex Colour Converter

In this exercise, you'll create a Python program that converts RGB color values to hexadecimal format and demonstrates color mixing. This will help you practice working with lists, string formatting, and basic color representation in computing.

## Knowledge Required

Before starting, ensure you're familiar with:

- Importing modules (e.g., `colorama` for terminal colors)
- String formatting using f-strings or `.format()`
- Working with lists and tuples for RGB values
- Basic arithmetic operations for color mixing
- Installing and using third-party modules like `colorama`

## Step-by-Step Guide

### 1. Understand RGB and Hex Colors

- RGB: Red, Green, Blue values (0-255 each)
- Hex: Six-digit code like #RRGGBB where each pair represents R, G, B in hex

### 2. Implement RGB to Hex Conversion

Convert each RGB component to two-digit hex:

```python
def rgb_to_hex(r, g, b):
    # your implementation goes here
    pass
```

### 3. Color Mixing Function

Mix two colors by averaging their RGB values:

```python
def mix_colors(color1, color2):
    r = (color1[0] + color2[0]) // 2
    g = (color1[1] + color2[1]) // 2
    b = (color1[2] + color2[2]) // 2
    return (r, g, b)
```

### 4. Complete Program with Colorama

```python
from colorama import init, Fore, Back, Style
init(autoreset=True)

def rgb_to_hex(r, g, b):
    """Convert RGB to hex color code."""
    pass

def mix_colors(color1, color2):
    """Mix two RGB colors by averaging."""
    r = (color1[0] + color2[0]) // 2
    g = (color1[1] + color2[1]) // 2
    b = (color1[2] + color2[2]) // 2
    return (r, g, b)

# Example usage
color1 = (1, 10, 255)  # Blue-ish
color2 = (255, 0, 0)   # Red

print(f"Color 1: rgb{color1} = {rgb_to_hex(*color1)}")
print(f"Color 2: rgb{color2} = {rgb_to_hex(*color2)}")

mixed = mix_colors(color1, color2)
print(f"Mixed Color: rgb{mixed} = {rgb_to_hex(*mixed)}")

# Display colors using colorama (approximate)
print(f"{Back.BLUE}   {Style.RESET_ALL} Color 1 sample")
print(f"{Back.RED}   {Style.RESET_ALL} Color 2 sample")
print(f"{Back.MAGENTA}   {Style.RESET_ALL} Mixed color sample")
```

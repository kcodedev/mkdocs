# 🐍 Exercise: Build an RGB to Hex Colour Converter

In this exercise, you'll create a Python program that converts RGB color values to hexadecimal format and demonstrates color mixing. This will help you practice working with lists, string formatting, and basic color representation in computing.

## Knowledge Required

Before starting, ensure you're familiar with:

- Importing modules (e.g., `colorama` for terminal colors)
- String formatting using f-strings or `.format()`
- Working with lists and tuples for RGB values
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
    # exampe rgb(51, 153, 255) should be converted to #3399ff
    pass
```

### 3. Complete Program with Colorama for printing the colour

```python
from colorama import init, Fore, Back, Style
init(autoreset=True)

def rgb_to_hex(r, g, b):
    # your implementation goes here
    # exampe rgb(51, 153, 255) should be converted to #3399ff
    pass

hex_colour = rgb_to_hex(51, 153, 255)
# use coloroama to print the colour
```


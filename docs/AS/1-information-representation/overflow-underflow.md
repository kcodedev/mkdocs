# Overflow and Underflow

In computer systems, **overflow** and **underflow** are errors that occur when arithmetic operations exceed the limits of the data type or representation used. These issues are particularly relevant in fixed-width binary representations, such as integers in two's complement or floating-point numbers.

## Overflow

Overflow happens when the result of an arithmetic operation is too large to be represented within the available bits. In signed integer arithmetic (using two's complement), this often manifests as a positive result wrapping around to a negative value, or vice versa.

### Example: 8-Bit Signed Integer Addition

Consider adding two positive 8-bit signed integers: 127 + 1.

- 127 in binary (8-bit): 01111111
- 1 in binary (8-bit): 00000001
- Sum: 10000000 (which is -128 in two's complement, the MSB is the sign bit)

| Operation | Binary Representation | Decimal Value |
|-----------|-----------------------|---------------|
| 127       | 01111111              | 127           |
| + 1       | 00000001              | 1             |
| Result    | 10000000              | -128 (overflow) |

### Famous Example: Pacman Score Overflow

In the original Pacman arcade game, the score is stored in an 8-bit register, limiting it to a maximum of 255 points. When a player reaches 255 points and earns more, the score overflows and wraps around to 0. This was a well-known bug that players exploited to reset their score and continue playing indefinitely.

## Underflow

Underflow occurs when the result of an operation is too small to be accurately represented. In integer arithmetic, this can happen during subtraction where the result goes below the minimum representable value.

### Example: Gandhi's Nuclear Aggression in Civilization

![Nuclear Gandhi Meme](https://www.kxnet.com/wp-content/uploads/sites/16/2023/02/5f9.jpg?resize=640,400)

In the video game Civilization (specifically Civilization II), the AI for Mahatma Gandhi was programmed with low aggression values. However, due to an underflow bug in the game's code, when Gandhi's aggression was decreased below zero (the minimum threshold), it wrapped around to the maximum value. 

This caused Gandhi's civilization to become extremely aggressive, frequently launching nuclear attacks. The bug stemmed from improper handling of integer underflow in the AI decision-making algorithm.

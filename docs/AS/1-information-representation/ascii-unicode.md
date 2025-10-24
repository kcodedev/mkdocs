# Representing Text

![ASCII Table](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/ASCII-Table-wide.svg/1024px-ASCII-Table-wide.svg.png)

## Introduction

In the world of computers, we need a way to represent text and characters so that machines can understand and process them. This is where character encoding systems like ASCII and Unicode come into play. In this tutorial, we'll explore what ASCII is, its limitations, and how Unicode solves those problems.

## What is ASCII?

ASCII stands for **American Standard Code for Information Interchange**. It is a character encoding standard that represents text in computers and other devices that use text.

- **Developed in**: 1963
- **Total Characters**: 128 (0 to 127)
- **Bits per Character**: 7 bits (but often stored in 8 bits with the 8th bit as 0)

ASCII includes:
- Uppercase letters (A-Z)
- Lowercase letters (a-z)
- Numbers (0-9)
- Punctuation marks (!, @, #, etc.)
- Control characters (like newline, tab)

### Example in Code

In Python, you can see the ASCII value of a character using `ord()`:

```python
print(ord('A'))  # Output: 65
print(chr(65))   # Output: A
```

## Limitations of ASCII

While ASCII was great for English text, it has several limitations:

1. **Limited to 128 characters**: It only supports English letters, numbers, and basic symbols. No support for accented letters (é, ñ), non-Latin scripts (Chinese, Arabic), or emojis.
2. **Language Barrier**: Not suitable for international communication.
3. **No Support for Modern Needs**: Things like emojis, mathematical symbols, or special characters are missing.

This led to the development of extended ASCII (8-bit, 256 characters), but even that wasn't enough for global use.

## Extended ASCII

Extended ASCII is an 8-bit version of the original ASCII standard, allowing for 256 characters (0-255). It includes the standard 128 ASCII characters in the lower half (0-127) and adds 128 additional characters in the upper half (128-255).

### What Extended ASCII Adds
- Accented letters (e.g., à, é, ñ)
- Additional symbols and punctuation
- Graphical characters (like box-drawing characters for simple GUIs)

### Problems with Extended ASCII
- **Limited Scope**: Still only supports a few languages (mostly Western European). No support for non-Latin scripts like Chinese, Arabic, or emojis.

Extended ASCII was a temporary solution, paving the way for the more comprehensive Unicode standard.

## What is Unicode?

Unicode is a universal character encoding standard that aims to represent every character from every language in the world, plus symbols, emojis, and more.

- **Developed by**: Unicode Consortium (started in 1991)
- **Total Characters**: Over 140,000 characters (as of recent versions)
- **Goal**: To provide a unique number (code point) for every character, no matter the platform, program, or language.

Unicode assigns a unique **code point** to each character, represented in hexadecimal, like U+0041 for 'A'.

### Unicode Encodings

Unicode itself is a standard, but to store it in bytes, we use encodings like:

1. **UTF-8**: Variable-length encoding (1-4 bytes per character). Backward compatible with ASCII.
   - ASCII characters use 1 byte (same as ASCII).
   - Other characters use 2-4 bytes.
   - Most common on the web.

2. **UTF-16**: Uses 2 or 4 bytes per character. Common in Windows and Java.

3. **UTF-32**: Fixed 4 bytes per character. Simple but uses more space.

### Example: UTF-8 Encoding

- 'A' (U+0041) in UTF-8: 41 (1 byte)
- 'é' (U+00E9) in UTF-8: C3 A9 (2 bytes)
- '🚀' (U+1F680) in UTF-8: F0 9F 9A 80 (4 bytes)

### Unicode Table Example

| Character | Code Point | UTF-8 Bytes |
|-----------|------------|-------------|
| A         | U+0041    | 41         |
| é         | U+00E9    | C3 A9      |
| 中        | U+4E2D    | E4 B8 AD   |
| 🚀        | U+1F680   | F0 9F 9A 80|

## Why Use Unicode?

- **Universality**: Supports all languages and scripts.
- **Consistency**: Same character has the same code point everywhere.
- **Future-Proof**: Can add new characters as needed.
- **Emojis and Symbols**: Includes modern elements like emojis, which are treated as characters.

### Example in Code

In Python, Unicode is the default:

```python
# Unicode string
text = "Hello, 世界! 🚀"
print(text)  # Output: Hello, 世界! 🚀

# Get code point
print(ord('🚀'))  # Output: 128640 (U+1F680)
```

## ASCII vs Unicode: Key Differences

| Feature          | ASCII                  | Unicode                  |
|------------------|------------------------|--------------------------|
| Characters       | 128                   | 140,000+                |
| Languages        | English only          | All languages           |
| Bits per Char    | 7 (or 8)              | Variable (1-4 bytes in UTF-8) |
| Compatibility    | Limited               | Includes ASCII as subset |

## Conclusion

ASCII was a foundational standard for text representation, but its limitations made it insufficient for global communication. Unicode, with its vast character set and flexible encodings like UTF-8, has become the standard for modern computing. Understanding these systems helps in programming, web development, and data handling.

# Number Systems 🔢

Computers use different number systems to represent data. The three main ones you need to know are **Denary**, **Binary**, and **Hexadecimal**.

| System | Base | Digits Used | Example |
|:---:|:---:|:---:|:---:|
| Denary | 10 | 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 | 123 |
| Binary | 2 | 0, 1 | 101 |
| Hexadecimal | 16 | 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F | A5 |

---

## Converting Between Denary and Binary 🔄

This is all about understanding **place values**. In binary, each position represents a power of 2.

### Denary to Binary ➡️

To convert a denary number to binary, you find which powers of 2 add up to your number.

*Example:* Convert the denary number 13 into an 8-bit binary number.

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |

The binary number is **00001101**.

### Binary to Denary ⬅️

To convert a binary number to denary, you multiply each digit by its place value and add them up.

*Example:* Convert the binary number `1101` to denary.

| Place Value: | 8  | 4  | 2  | 1  |
|:---:|:---:|:---:|:---:|:---:|
| Binary Digit: | 1 | 1 | 0 | 1 |

* ` (1 x 8) + (1 x 4) + (0 x 2) + (1 x 1) `
* ` 8 + 4 + 0 + 1 = 13 `

The denary number is **13**.

---

## Converting Between Denary and Hexadecimal 📝

This conversion also uses **place values**, but the base is 16.

### Denary to Hexadecimal ➡️

To convert from denary to hexadecimal, we use repeated division by 16.

*Example:* Convert the denary number **255** to hexadecimal.

| Place Value: | (16s) | (1s) |
|:---:|:---:|:---:|
| Divide by 16: | `255 / 16 = 15` remainder `15` | `15 / 16 = 0` remainder `15` |
| Hexadecimal Digit: | F | F |


### Hexadecimal to Denary ⬅️

To convert from hexadecimal to denary, you multiply each digit by its place value and add them up.

*Example:* Convert the hexadecimal number `A5` to denary.

| Place Value: |(16s) | (1s) |
|:---:|:---:|:---:|
| Hexadecimal Digit: | A | 5 |
| Denary Value: | 10 | 5 |

* ` (10 x 16) + (5 x 1) `
* ` 160 + 5 = 165 `

The denary number is **165**.

---

## Converting Between Hexadecimal and Binary 💡

This conversion is simple because each hexadecimal digit directly corresponds to a 4-bit binary number.

### Hexadecimal to Binary ➡️

Just look up each hexadecimal digit in the table and write down its 4-bit binary equivalent.

| Hex | Binary | Hex | Binary |
|:---:|:------:|:---:|:------:|
| 0 | 0000 | 8 | 1000 |
| 1 | 0001 | 9 | 1001 |
| 2 | 0010 | A | 1010 |
| 3 | 0011 | B | 1011 |
| 4 | 0100 | C | 1100 |
| 5 | 0101 | D | 1101 |
| 6 | 0110 | E | 1110 |
| 7 | 0111 | F | 1111 |

*Example:* Convert `A5` to binary.

* The hexadecimal digit `A` is `1010` in binary.
* The hexadecimal digit `5` is `0101` in binary.
* Combine them to get **`10100101`**.

### Binary to Hexadecimal ⬅️

Group the binary digits into sets of four and convert each group to its hexadecimal equivalent.

*Example:* Convert `10100101` to hexadecimal.

1.  Group the binary number into sets of four from right to left: `1010` `0101`.
2.  Look up each group in the conversion table above.
3.  The binary `1010` is hexadecimal `A`.
4.  The binary `0101` is hexadecimal `5`.
5.  The hexadecimal number is **A5**.
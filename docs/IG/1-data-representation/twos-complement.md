### **Understanding Two's Complement** 🔢

Two's complement is a clever way for computers to represent both **positive and negative binary numbers**. This method simplifies calculations for the processor. For an 8-bit number, the leftmost bit is the **most significant bit (MSB)**. For a negative number, this bit's place value is **-128**. If the sign bit is **0**, the number is **positive**; if it's **1**, it's **negative**. The range of an 8-bit two's complement number is from -128 to +127.

***

### **Positive Numbers** ✅

Representing a positive number in two's complement is simple. You just convert it to an 8-bit binary number as usual. The sign bit will always be `0`.

*Example:* Convert `19` to an 8-bit two's complement integer.
The place values for an 8-bit number are shown below. The value of -128 is not used for positive numbers as the binary digit in that column will always be 0.

|-128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 |

The binary representation is `00010011`. The sign bit is **0**, which confirms it's a positive number.

***

### **Negative Numbers** ❌

To find the denary value of a negative two's complement number, you add up the values of each place, including the **-128** for the sign bit.

*Example:* Convert the two's complement number `11101101` to denary.

1.  **Check the sign bit.** It's a `1`, so we know the number is negative. The value of this bit is **-128**.
2.  **Add up the place values.** Sum the values for all the bits that are `1`.

| -128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | 1 | 1 | 0 | 1 | 1 | 0 | 1 |


The sum is `-128 + 64 + 32 + 8 + 4 + 1 = -19`.

The denary number is **-19**.
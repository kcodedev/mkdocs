## Logical Binary Shifts ➡️⬅️

A logical binary shift is a simple operation that moves all the bits in a binary number either to the left or to the right. This is a fundamental operation in computer science because it's a very fast way to multiply or divide a number by a power of 2.

When you perform a logical shift, the bits that are shifted out of the register (the memory space for the number) are lost, and zeros are shifted in at the opposite end to fill the empty spots. This is different from a circular shift, where the bits that are shifted out are looped back around to the other side.

---

### **Logical Left Shift ⬅️**

A logical left shift moves all the bits to the left. For every position you shift the number to the left, you are effectively **multiplying the original denary value by 2**.

**The Rules:**

* Bits shifted off the left end of the register are lost.
* Zeros are shifted in from the right end to fill the empty spots.

Let's use an 8-bit register as an example. Our starting binary integer is `00001100`, which is 12 in denary.

**One Logical Left Shift:**

If we shift `00001100` one position to the left, the leftmost `0` is lost, and a `0` is added to the rightmost position.

* **Original:** `00001100` (12)
* **Shifted:** `00011000` (24)

The new binary number `00011000` is 24 in denary, which is `12 x 2`.

**Two Logical Left Shifts:**

If we shift the original number two positions to the left, the two leftmost `0`s are lost, and two `0`s are added to the right.

* **Original:** `00001100` (12)
* **Shifted:** `00110000` (48)

The new binary number `00110000` is 48 in denary, which is `12 x 4` (or `12 x 2^2`).

---

### **Logical Right Shift ➡️**

A logical right shift moves all the bits to the right. For every position you shift the number to the right, you are effectively **dividing the original denary value by 2**.

**The Rules:**

* Bits shifted off the right end of the register are lost. These are the **least significant bits**.
* Zeros are shifted in from the left end to fill the empty spots.

Let's again use our 8-bit register with the binary number `00001100`, which is 12 in denary.

**One Logical Right Shift:**

If we shift `00001100` one position to the right, the rightmost `0` is lost, and a `0` is added to the leftmost position.

* **Original:** `00001100` (12)
* **Shifted:** `00000110` (6)

The new binary number `00000110` is 6 in denary, which is `12 / 2`.

**Two Logical Right Shifts:**

If we shift the original number two positions to the right, the two rightmost `0`s are lost, and two `0`s are added to the left.

* **Original:** `00001100` (12)
* **Shifted:** `00000011` (3)

The new binary number `00000011` is 3 in denary, which is `12 / 4` (or `12 / 2^2`).

Notice that the right shift performs integer division; any fractional part of the result is discarded, as the bits shifted off the end are lost. For example, shifting 5 (`00000101`) one position to the right results in 2 (`00000010`), not 2.5.
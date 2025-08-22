### Why We Need Error🚨

Imagine you're sending a message and part of it gets jumbled on the way. The person receiving it wouldn't be able to understand the message correctly. The same thing can happen with digital data. **Errors can occur during data transmission** due to **interference**. This can lead to:

-   **Data loss**: A piece of data goes missing.
-   **Data gain**: Extra, incorrect data is added.
-   **Data change**: A piece of data is altered from its original form.

To ensure the data is received exactly as it was sent, we need error detection methods.

### Error Detection Methods 🔍

#### A. Parity Check 🔢

This is a simple way to check for errors in a single byte of data. A **parity bit** is a bit **reserved within a byte (8 bits)** of data. The value of this bit (0 or 1) is determined by the number of 1s in the other seven bits.

-   **Even Parity**: The parity bit is set so that the total number of 1s in the **8-bit word** is **even**.
-   **Odd Parity**: The parity bit is set so that the total number of 1s in the **8-bit word** is **odd**.

**Process**:

1.  The sender counts the number of 1s in the seven data bits.
2.  Based on the chosen parity (even or odd), they set the parity bit.
3.  The **8-bit word** is transmitted.
4.  The receiver counts the 1s in the received word.
5.  If the count matches the parity rule, no error is detected. If it doesn't, an error is flagged. 

This method can also be extended to a **parity block check**, where a parity bit is calculated for each row and column of a block of data, forming a **parity byte** which is transmitted with the data block. This allows for the detection of more complex errors.

#### B. Checksum ✅

This method works with a block of data rather than just a single byte.

**Process**:

1.  The sender adds up all the numerical values of the bytes in a block of data.
2.  The resulting sum is called the **checksum**.
3.  The checksum is transmitted along with the data block.
4.  The receiver also adds up the values of the bytes in the received block.
5.  If the receiver's sum matches the transmitted checksum, the data is likely correct. If they don't match, an error is detected.

#### C. Echo Check 🗣️

This is a simple, yet effective method where the receiver of the data immediately sends the received data back to the sender.

**Process**:

1.  The sender transmits a block of data.
2.  The receiver receives the data and, without processing it, **echos** (sends) it back to the sender.
3.  The sender then compares the received data (the echo) with the original data they sent.
4.  If the two match, it's assumed the data was transmitted correctly. If not, an error is detected.

***
#### D. Check Digit 🔢

A **check digit** is a single digit added to a series of numbers to detect errors in **data entry**. It's not typically used for transmission errors but for mistakes made when a person types in a number.

**Process**:

1.  A mathematical algorithm is applied to the main sequence of digits.
2.  The result of this calculation is the check digit.
3.  The check digit is added to the end of the number.
4.  When the number is entered, the same algorithm is applied to the main digits.
5.  If the result matches the check digit, the number is considered valid.

**Examples**:

-   **International Standard Book Numbers (ISBN)**: The last digit of a 10 or 13-digit ISBN is a check digit.
-   **Bar Codes**: The last digit of a bar code is a check digit. 
-   **Product codes** and **bank account numbers** also often use check digits.

***
#### E. Automatic Repeat Query (ARQ) 🔄

**ARQ** is a system used to ensure data is received without error by automatically requesting a re-send if an error is detected. It combines error detection with a feedback system.

**Process**:

1.  The sender transmits a block of data.
2.  The receiver performs an error check (like a parity check or checksum).
3.  If no error is found, the receiver sends a **positive acknowledgment (ACK)** message back to the sender. This tells the sender that the data was received correctly and they can send the next block.
4.  If an error is found, the receiver sends a **negative acknowledgment (NAK)** message. This tells the sender that an error occurred and they must **retransmit** the data.
5.  A **timeout** is used as a safety measure. If the sender doesn't receive an ACK or NAK within a set time, it automatically assumes the data was lost and retransmits it.

This process ensures reliable data transfer even with transmission errors.
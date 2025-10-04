A computer stores text by assigning a unique numerical code to each character. These codes are organized in a **character set**, which is like a secret key that tells the computer what each binary number represents.

***

### ASCII: The First Standard

**ASCII** (American Standard Code for Information Interchange) was one of the first and most widely used character sets. It was originally created for teleprinters and used **7 bits** for each character, giving it a total of 128 possible codes (from 0 to 127). This was enough for all the characters on a standard American keyboard, but it couldn't handle characters from other languages.

Here is a portion of the ASCII table to show you how different characters are mapped to a denary (decimal) number and a binary code.

| Character | Denary | 7-bit Binary |
| :---: | :---: | :---: |
| `Space` | 32 | `0100000` |
| `0` | 48 | `0110000` |
| `1` | 49 | `0110001` |
| `A` | 65 | `1000001` |
| `B` | 66 | `1000010` |
| `a` | 97 | `1100001` |
| `b` | 98 | `1100010` |
| `@` | 64 | `1000000` |
| `$` | 36 | `0100100` |
| `}` | 125 | `1111101` |

For a time, an **extended ASCII** was created that used 8 bits, expanding the number of characters to 256. However, even this couldn't solve the problem of supporting all the world's languages.

***

### Unicode: A Global Solution

**Unicode** was developed to be a universal character set that could include every character from all written languages and symbols, including emojis. It's the standard used by virtually all modern computers and the internet today. The core difference is that while ASCII uses a fixed number of bits (7 or 8), Unicode is much more flexible, using up to **32 bits** per character to represent hundreds of thousands of different symbols.

Think of it like this: if **ASCII** is a simple phrasebook for one language 🗣️, **Unicode** is a universal translator that can understand every language in the world 🌎.



| Feature | ASCII | Unicode |
| :--- | :--- | :--- |
| **Bits per Character** | 7 (or 8 for Extended) | Up to 32 |
| **Characters Supported** | 128 (or 256) | Over 140,000 |
| **Languages** | Primarily English | Nearly all languages and symbols |
| **Common Use** | Legacy systems, text-only files | Modern operating systems, web pages, emojis |
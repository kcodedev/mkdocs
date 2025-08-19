# 📏 Calculating File Size for Images & Sounds

Understanding how to calculate file sizes is important for managing storage and transferring files. Let's break it down with simple examples!

---

## 🖼️ Image File Size

**Formula:**  
```
File Size (bits) = Width × Height × Colour Depth
```

- **Width × Height:** Image resolution (in pixels)
- **Colour Depth:** Number of bits per pixel (e.g., 8 bits for 256 colours)

### Example

> **Question:**  
> An image is 32 pixels wide and 16 pixels high. It uses 8 bits per pixel. What is the file size in bytes?

**Step 1:** Calculate total pixels  
`32 × 16 = 512 pixels`

**Step 2:** Multiply by colour depth  
`512 × 8 = 4096 bits`

**Step 3:** Convert bits to bytes (1 byte = 8 bits)  
`4096 ÷ 8 = 512 bytes`

**Answer:**  
**512 bytes**

---

## 🎵 Sound File Size

**Formula:**  
```
File Size (bits) = Sample Rate × Bit Depth × Duration (seconds)
```

- **Sample Rate:** Samples per second (Hz)
- **Bit Depth:** Bits per sample
- **Duration:** Length in seconds

### Example

> **Question:**  
> A sound file is recorded at 1024 Hz, with 8 bits per sample, for 2 seconds. What is the file size in kilobytes (KB)?

**Step 1:** Calculate total samples  
`1024 × 2 = 2048 samples`

**Step 2:** Multiply by bit depth  
`2048 × 8 = 16384 bits`

**Step 3:** Convert bits to bytes  
`16384 ÷ 8 = 2048 bytes`

**Step 4:** Convert bytes to kilobytes (1 KB = 1024 bytes)  
`2048 ÷ 1024 = 2 KiB`

**Answer:**  
**2 KB**

---

## 📝 Key Points

- Always use **1024** for conversions (not 1000).
- Show your working for full marks!
- Check the units required in the question (bits, bytes, KiB, etc).

---

✨ **Practice makes perfect!.**
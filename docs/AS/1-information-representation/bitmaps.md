# Bitmap Graphics and Binary Representation

## 🖼️ What is a Bitmap?

A **bitmap** (or raster image) is made up of a grid of **pixels**.  
Each pixel stores a specific color, and the image is stored **pixel by pixel** in memory or in a file.

Bitmap formats include `.bmp`, `.png`, `.jpg`, and `.gif`.

---

## 💡 How Bitmaps Work in Binary

Each pixel's color is stored as a **binary value**.  
The number of bits used for each pixel is called the **color depth**.

| Color Depth | Bits per Pixel | Colors Available      |
|-------------|----------------|------------------------|
| 1-bit       | 1              | 2 (black and white)    |
| 4-bit       | 4              | 16                     |
| 8-bit       | 8              | 256                    |
| 24-bit      | 24             | 16.7 million (TrueColor) |

- In a **24-bit** image, each pixel has **3 color channels** (Red, Green, Blue), each stored in 8 bits:
  - Red: 8 bits  
  - Green: 8 bits  
  - Blue: 8 bits  
  → Total: **24 bits per pixel**

---

## 📏 Calculating Bitmap File Size

##### Reminders:

📐 Choosing the Right Units for File Size
In Computer Science exams (where calculators are not allowed), it helps to:

Write the full expression. Use cancellation to simplify units and avoid large multiplications.

##### 📏 Binary Prefix Reference

| Unit     | Symbol | Value      |
| -------- | ------ | ---------- |
| Bit      | b      | 1          |
| Byte     | B      | 8 bits     |
| Kibibyte | KiB    | 1024 bytes |
| Mebibyte | MiB    | 1024 KiB   |
| Gibibyte | GiB    | 1024 MiB   |


##### 🧮 Example 1: Black and White Image

- Dimensions: 100 × 100 pixels  
- Color Depth: 1-bit (black or white)
- So size = ???

##### 🧮 Example 2: 8 bit color depth

- Dimensions: 2048 × 1024 (Full HD)  
- Color Depth: 8-bit
- So size = ???

##### 🧮 Example 3: TrueColor Image

- Dimensions: 1920 × 1080 (Full HD)  
- Color Depth: 24-bit
- So size = 1920 × 1080 × 24 = 49,766,400 bits
- Then ... ÷ 8 = 6,220,800 bytes ≈ 6.22 MB


##### 🧮 Example 4: Simplifying calculation

- Image dimensions: 2048 x 1024
- Color depth: 16 bits per pixel
- So size  = ...

> ⚠️ These calcs are of **raw size**. Actual file size may be larger (with metadata) or smaller (if compressed).

---

## 🗂️ What is Metadata?

**Metadata** is "data about data". In the context of image files, it refers to additional information stored **alongside the actual pixel data**.

### 📷 Common Metadata in Image Files

- **Dimensions** (width, height)
- **Color depth**
- **File type and compression method**
- **Creation and modification dates**
- **Camera settings** (for photos): exposure, focal length, ISO
- **Author or copyright info**
- **Thumbnail previews**

### 🧠 Why Is Metadata Important?

- Helps software know how to **decode and display** the image
- Supports **organizing and searching** (e.g. by date or author)

---


## 🧱 Summary

- Bitmaps store images as grids of pixels.
- Each pixel’s color is stored in binary using a certain number of bits.
- Use `Width × Height × Color Depth ÷ 8` to estimate file size. Then choose an appropriate measurement.






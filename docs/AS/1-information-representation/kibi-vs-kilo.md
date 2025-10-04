# Data Storage Units and Speed

When measuring **data storage** and **data transfer speed**, it's important to distinguish between two systems of measurement: **binary** (used in computing) and **decimal** (used in storage marketing).

---

## 🔢 Binary vs Decimal Units

| Base | Description       | Used by        |
|------|-------------------|----------------|
| **Decimal (base 10)** | Multiples of 1000 (10³) | Hard drive manufacturers, networking |
| **Binary (base 2)**   | Multiples of 1024 (2¹⁰) | Operating systems, RAM specs         |

---

## 🧮 Storage Units – Binary vs Decimal

| Name        | Decimal (10ⁿ) | Binary (2ⁿ) | Abbreviation |
|-------------|----------------|----------------|---------------|
| **Bit**     | 1 bit          | 1 bit          | `b`           |
| **Byte**    | 8 bits         | 8 bits         | `B`           |
| **Kilobyte** | 1,000 B        | —              | `kB`          |
| **Kibibyte** | —              | 1,024 B        | `KiB`         |
| **Megabyte** | 1,000,000 B    | —              | `MB`          |
| **Mebibyte** | —              | 1,048,576 B    | `MiB`         |
| **Gigabyte** | 1,000,000,000 B | —             | `GB`          |
| **Gibibyte** | —              | 1,073,741,824 B | `GiB`        |
| **Terabyte** | 1,000,000,000,000 B | —         | `TB`          |
| **Tebibyte** | —              | 1,099,511,627,776 B | `TiB`    |
| **Petabyte** | 1,000,000,000,000,000 B | —      | `PB`          |
| **Pebibyte** | —              | 1,125,899,906,842,624 B | `PiB`  |

**Note:** OSs often report disk space in **binary** (e.g., 1 TiB), while disk manufacturers label using **decimal** (1 TB). This causes common confusion.

---

## ⚡ Measuring Speed

Data transfer speed is typically measured in **bits per second** (not bytes):

| Unit         | Meaning                     | Notes                      |
|--------------|-----------------------------|----------------------------|
| **bps**      | bits per second              | Base unit                  |
| **Kbps**     | kilobits per second (1,000 bps) |                           |
| **Mbps**     | megabits per second (1,000,000 bps) | Common for internet speeds |
| **Gbps**     | gigabits per second (1,000,000,000 bps) | High-speed networks       |

- **Networking** uses **decimal (10³)** multiples.
- **Storage** is often in **bytes**, but **network speed is in bits**.

> 🔁 **1 Byte = 8 bits**, so a 100 Mbps connection can transfer **12.5 MB/s**

---

## ✅ Summary

- **Binary**: used in computing (RAM, OS reporting) → KiB, MiB, GiB...
- **Decimal**: used in marketing (drives, network speeds) → kB, MB, GB...
- **Speed** is in **bits per second** (Mbps), **not bytes**

Understanding both systems helps avoid confusion when buying hardware or configuring networks.



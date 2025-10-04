# 📂 File Organisation, Access Methods

Understanding **how files are stored and accessed** is critical when designing efficient software systems. Let's explore different **file organisation methods**, **access methods**, and **hashing algorithms**.

---

## 🗄 1. File Organisation Methods

### 1.1 Serial Organisation
- **📜 Description:** Records are stored **one after another** in the order they are created.
- **🔍 Access:** Always searched **from the beginning to the end**.
- **✅ Pros:**
  - Very simple to implement.
  - Great for small datasets or logs.
- **⚠ Cons:**
  - Searching is slow for large files.
- **💡 Example:** Storing sensor readings in the order they arrive.

---

### 1.2 Sequential Organisation
- **📜 Description:** Records are stored **in order of a key field** (e.g., student ID).
- **🔍 Access:** Usually sequential but can be searched faster using the key.
- **✅ Pros:**
  - Faster searches than serial if sorted by key.
  - Good for processing all records in order.
- **⚠ Cons:**
  - Insertion into the correct place is slow.
- **💡 Example:** Payroll records sorted by employee number.

---

### 1.3 Random (Direct) Organisation
- **📜 Description:** Records are stored at **specific locations** calculated from a **record key** using a **hash function**.
- **🔍 Access:** Direct — jump straight to the record.
- **✅ Pros:**
  - Very fast access.
- **⚠ Cons:**
  - More complex to implement.
  - Collisions must be handled.
- **💡 Example:** Accessing bank customer details by account number.

---

## 📡 2. File Access Methods

### 2.1 Sequential Access
- Reads records **in order** from the start to the end.
- Works for **serial** and **sequential** files.
- **📌 Example:**
  ```python
  with open("students.txt") as f:
      for line in f:
          print(line)
  ```

---

### 2.2 Direct Access
- Jump directly to a specific record without reading all previous ones.
- Works for **sequential** (if positions are known) and **random** files.
- **📌 Example (binary file random access):**
  ```python
  with open("records.bin", "rb") as f:
      f.seek(record_number * record_size)
      data = f.read(record_size)
  ```

---

## 🔑 3. Hashing Algorithms

### What is Hashing?
A **hashing algorithm** takes a **record key** and calculates an **address** where that record should be stored.

---

### 3.1 Simple Modulo Hashing
- Formula:
  ```
  address = key % table_size
  ```
- Example:
  - Table size = 100
  - Key = 12345 → Address = 12345 % 100 = 45

---

### 3.2 Folding Method
- Split key into equal parts, sum them, then take modulo.
- Example:
  - Key = 123456  
  - Split into (12, 34, 56) → Sum = 102 → 102 % table_size

---

### 3.3 Collision Handling
When two keys hash to the same address:
- **Linear probing:** Try the next free address.
- **Chaining:** Store multiple records in a linked list at the same address.

---

## 🧠 Choosing the Right Method

| Problem Type | Recommended Organisation | Access Method | Why |
|--------------|---------------------------|--------------|-----|
| Log of website visits | Serial | Sequential | Simple and append-only |
| Payroll system | Sequential | Sequential | Sorted by employee ID |
| Online banking | Random | Direct | Instant access by account number |

---

## 🏆 Example Exam Task
**Task:** You are building a student database for quick lookups by student ID.  
**Best choice:** Random file organisation with direct access using a hashing algorithm.

```python
def hash_id(student_id, table_size):
    return student_id % table_size
```

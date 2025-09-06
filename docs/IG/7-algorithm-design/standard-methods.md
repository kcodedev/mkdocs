# 🔍 Standard Algorithm Methods

Common algorithms that solve typical programming problems. These include searching, sorting, and data processing operations.

---

## 🔎 Linear Search

Find an item in a list by checking each element:

- **Method**: Check each item from start to end
- **Best case**: Item found at first position
- **Worst case**: Item not found or at last position
- **Use**: Small lists or unsorted data

---

## 🫧 Bubble Sort

Sort a list by repeatedly swapping adjacent elements:

- **Method**: Compare adjacent pairs and swap if out of order
- **Process**: Multiple passes until no swaps needed
- **Efficiency**: O(n²) - good for small lists
- **Use**: Simple sorting for small datasets

---

## ➕ Totalling

Calculate the sum of values in a list:

- **Method**: Initialize total to 0, add each value
- **Process**: Loop through all items, accumulate sum
- **Use**: Calculate totals, averages, running sums

---

## 🔢 Counting

Count occurrences of items or conditions:

- **Method**: Initialize counter to 0, increment when condition met
- **Process**: Loop through data, check conditions
- **Use**: Frequency analysis, statistics

---

## 📊 Finding Maximum, Minimum, and Average

Process data to find extreme values and averages:

- **Maximum**: Track highest value encountered
- **Minimum**: Track lowest value encountered
- **Average**: Sum ÷ Count

---

## 📈 Example: Finding Maximum

```
Initialize max = first item
For each remaining item:
  If item > max:
    max = item
Return max
```

---

## 📝 **Key Points:**

- Linear search checks each item sequentially ✅
- Bubble sort swaps adjacent out-of-order elements ✅
- Totalling accumulates values ✅
- Counting tracks occurrences ✅
- Max/min/average operations process data extremes ✅

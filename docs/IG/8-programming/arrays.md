# 📊 Arrays: Organizing Data

Arrays store multiple values of the same type in a structured way. They allow efficient access to data using index positions.

---

## 🏗️ Array Basics

- **Definition**: Fixed-size structure of identical data types
- **Indexing**: Access elements by position number
- **Declaration**: ARRAY[lower:upper] OF data_type

---

## 📏 One-Dimensional Arrays

Single row of elements:

```
DECLARE Scores : ARRAY[1:10] OF INTEGER
```

- **Access**: Scores[1], Scores[2], etc.
- **Use**: Lists, sequences, collections

---

## 📐 Two-Dimensional Arrays

Rows and columns of elements:

```
DECLARE Grid : ARRAY[1:3, 1:3] OF CHAR
```

- **Access**: Grid[1,1], Grid[2,3], etc.
- **Use**: Tables, matrices, grids

---

## 🔄 Array Operations

### Writing Values
```
FOR Index ← 1 TO 10
  Scores[Index] ← 0
NEXT Index
```

### Reading Values
```
FOR Index ← 1 TO 10
  OUTPUT Scores[Index]
NEXT Index
```

### Processing Arrays
```
Total ← 0
FOR Index ← 1 TO 10
  Total ← Total + Scores[Index]
NEXT Index
Average ← Total / 10
```

---

## 🎯 Array Applications

- **Data storage**: Store related values together
- **Searching**: Linear search through elements
- **Sorting**: Organize data in order
- **Statistics**: Calculate averages, find min/max
- **Matrices**: Mathematical operations

---

## 📋 Best Practices

- **Meaningful indices**: Start from 1 or 0 consistently
- **Bounds checking**: Don't exceed array limits
- **Initialize**: Set values before use
- **Size planning**: Estimate required capacity

---

## 🔍 Common Operations

- **Traversal**: Visit each element
- **Search**: Find specific values
- **Sort**: Arrange in order
- **Filter**: Select elements meeting criteria
- **Aggregate**: Sum, average, count


## 📝 **Key Points:**

- Arrays store multiple values of same type ✅
- Use indices to access elements ✅
- Support 1D and 2D structures ✅
- Enable efficient data processing ✅
- Require careful bounds management ✅

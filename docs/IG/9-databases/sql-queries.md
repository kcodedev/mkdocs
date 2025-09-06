# 🔍 SQL Queries: Accessing Database Data

SQL (Structured Query Language) retrieves and manipulates data in databases. Basic queries select, filter, and organize information from tables.

---

## 📋 Basic SQL Structure

```sql
SELECT fields
FROM table
WHERE conditions
```

---

## 🎯 SELECT Statement

### Select All Fields
```sql
SELECT * FROM Students
```

### Select Specific Fields
```sql
SELECT FirstName, LastName FROM Students
```

### Select with Alias
```sql
SELECT FirstName AS 'First Name' FROM Students
```

---

## 🔍 WHERE Clause

### Simple Conditions
```sql
SELECT * FROM Students
WHERE Grade = 'A'
```

### Multiple Conditions
```sql
SELECT * FROM Students
WHERE Grade = 'A' AND Age > 16
```

### Range Conditions
```sql
SELECT * FROM Students
WHERE Age BETWEEN 15 AND 18
```

---

## 📊 ORDER BY

### Ascending Order
```sql
SELECT * FROM Students
ORDER BY LastName ASC
```

### Descending Order
```sql
SELECT * FROM Students
ORDER BY Score DESC
```

---

## 🔢 Aggregate Functions

### Count Records
```sql
SELECT COUNT(*) FROM Students
```

### Sum Values
```sql
SELECT SUM(Score) FROM Students
```

### Find Average
```sql
SELECT AVG(Score) FROM Students
```

### Find Maximum/Minimum
```sql
SELECT MAX(Score), MIN(Score) FROM Students
```

---

## 🎨 Complex Queries

### Grouped Results
```sql
SELECT Grade, COUNT(*)
FROM Students
GROUP BY Grade
```

### Filtered Aggregates
```sql
SELECT Grade, AVG(Score)
FROM Students
WHERE Age > 15
GROUP BY Grade
```

---

## 📋 Query Results

| StudentID | FirstName | LastName | Score |
|-----------|-----------|----------|-------|
| 1 | Alice | Smith | 95 |
| 2 | Bob | Jones | 87 |
| 3 | Carol | Brown | 92 |

---

## ✅ Best Practices

- **Clear field names**: Use descriptive names
- **Proper conditions**: Ensure correct filtering
- **Efficient queries**: Select only needed fields
- **Readable format**: Use proper indentation
- **Test queries**: Verify results before use

---

## 📝 **Key Points:**
 
- SELECT retrieves data from tables ✅
- WHERE filters records by conditions ✅
- ORDER BY sorts results ✅
- Aggregate functions calculate totals ✅
- Complex queries combine multiple clauses ✅

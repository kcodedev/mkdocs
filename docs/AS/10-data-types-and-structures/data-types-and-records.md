# Data Types and Records

Different types of data are used to solve different kinds of problems. Choosing the **appropriate data type** ensures programs are efficient, accurate, and readable.

### Common Data Types
| Data Type | Description | Example |
|-----------|-------------|---------|
| **INTEGER** | Whole numbers (no decimal point) | `42`, `-7` |
| **REAL** | Numbers with decimal points | `3.14`, `-0.5` |
| **CHAR** | A single character | `'A'`, `'9'`, `'#'` |
| **STRING** | A sequence of characters | `"Hello"`, `"CS2025"` |
| **BOOLEAN** | Logical values | `TRUE`, `FALSE` |
| **DATE** | Calendar dates | `12/09/2025` |
| **ARRAY** | Collection of values of the same type | `Array[1..5] OF INTEGER` |
| **FILE** | External storage of data | Used for reading/writing data to files |

---

## Record Structures

A **record** is a data structure that groups together **different data types** under one identifier.  
- Useful for representing a single "entity" with multiple attributes.  
- Example: A **student record** might store a name (STRING), age (INTEGER), grade (CHAR), and enrolment status (BOOLEAN).  

---

## Records in Pseudocode

### (a) Defining a Record
```text
TYPE StudentRecord
    DECLARE Name : STRING
    DECLARE Age : INTEGER
    DECLARE Grade : CHAR
    DECLARE Enrolled : BOOLEAN
ENDTYPE
```

### (b) Declaring and Storing Data in a Record
```text

DECLARE Student1 : StudentRecord

Student1.Name ⟵ "Alice"
Student1.Age ⟵ 17
Student1.Grade ⟵ 'A'
Student1.Enrolled ⟵ TRUE
```

### (c) Reading Data from a Record

```text
OUTPUT Student1.Name
OUTPUT Student1.Age
OUTPUT Student1.Grade
OUTPUT Student1.Enrolled
```

# 🔑 Primary Keys: Unique Identifiers

Primary keys uniquely identify each record in a database table. They ensure no duplicate records and enable efficient data retrieval.

---

## 🎯 Primary Key Characteristics

- **Unique**: No two records have the same value
- **Not null**: Every record must have a value
- **Stable**: Value doesn't change over time
- **Minimal**: Contains only necessary information

---

## 📊 Types of Primary Keys

### Natural Keys
- **Definition**: Uses existing data field
- **Examples**: Social Security Number, Email, Phone
- **Pros**: Meaningful, no extra fields needed
- **Cons**: May change, not always unique

### Surrogate Keys
- **Definition**: Artificial field created for uniqueness
- **Examples**: Auto-incrementing numbers, GUIDs
- **Pros**: Always unique, never changes
- **Cons**: No inherent meaning

---

## 🔍 Choosing Primary Keys

### Selection Criteria
- **Uniqueness**: Guaranteed unique values
- **Stability**: Won't change over time
- **Simplicity**: Easy to use and understand
- **Performance**: Efficient for searching

### Examples
- **Students**: Student ID number
- **Products**: Product code/SKU
- **Orders**: Order number
- **Users**: User ID

---

## 🏗️ Primary Key Implementation

### Single Field
```
StudentID (Integer) - Primary Key
```

### Composite Key
```
CourseID (Integer) + Semester (Text) - Primary Key
```

### Auto-Generated
```
ID (Integer, Auto-increment) - Primary Key
```

---

## 🔗 Relationships and Keys

- **Foreign Keys**: Reference primary keys in other tables
- **Referential Integrity**: Maintains relationships between tables
- **Joins**: Combine data using keys

---

## ⚠️ Common Mistakes

- **Null values**: Primary keys cannot be empty
- **Duplicates**: Each value must be unique
- **Changes**: Avoid changing primary key values
- **Meaningless**: Don't use meaningless surrogate keys unnecessarily

---

## 📈 Benefits

- **Data integrity**: Prevents duplicates
- **Fast access**: Efficient record retrieval
- **Relationships**: Enables table relationships
- **Consistency**: Maintains data quality

---

## 📝 **Key Points:**

- Primary keys uniquely identify records ✅
- Must be unique and not null ✅
- Choose stable, meaningful values ✅
- Support efficient data operations ✅
- Enable table relationships ✅

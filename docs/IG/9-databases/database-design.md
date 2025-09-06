# 🗄️ Database Design: Structuring Data

Databases organize data into tables with defined structures. Single-table databases store related information in rows and columns.

---

## 📋 Table Structure

- **Fields**: Columns that define data types
- **Records**: Rows containing actual data
- **Primary Key**: Unique identifier for each record

---

## 🎯 Designing a Database

1. **Identify requirements**: What data needs storing?
2. **Determine fields**: What information for each item?
3. **Choose data types**: Appropriate type for each field
4. **Set primary key**: Unique identifier field
5. **Add validation**: Rules for data entry

---

## 📊 Example: Student Database

| Field Name | Data Type | Description |
|------------|-----------|-------------|
| StudentID | Integer | Unique student number |
| FirstName | Text | Student's first name |
| LastName | Text | Student's last name |
| DateOfBirth | Date | Birth date |
| Grade | Text | Current grade level |

---

## 🔑 Primary Key Selection

- **Unique**: No two records have same value
- **Not null**: Every record must have a value
- **Stable**: Doesn't change over time
- **Simple**: Preferably single field

---

## ✅ Data Validation

- **Range checks**: Values within limits
- **Type checks**: Correct data types
- **Presence checks**: Required fields filled
- **Format checks**: Data follows patterns

---

## 📈 Database Benefits

- **Organized**: Structured data storage
- **Efficient**: Quick data retrieval
- **Consistent**: Validation ensures quality
- **Scalable**: Can handle growing data
- **Shareable**: Multiple users can access

---

## 📝 **Key Points:**

- Tables consist of fields and records ✅
- Primary keys uniquely identify records ✅
- Data types ensure appropriate storage ✅
- Validation maintains data quality ✅
- Design affects database effectiveness ✅

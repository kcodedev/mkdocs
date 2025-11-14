# Database Normalisation

Database normalisation is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller, related tables and defining relationships between them. The goal is to eliminate data anomalies and ensure efficient data storage and retrieval.

## Why Normalise?

### Problems with Unnormalised Data
- **Data Redundancy**: Same data stored in multiple places
- **Update Anomalies**: Changing data in one place but not others
- **Insertion Anomalies**: Cannot insert data due to missing related information
- **Deletion Anomalies**: Deleting data removes other necessary information
- **Data Inconsistency**: Different versions of same data

### Benefits of Normalisation
- **Data Integrity**: Ensures data accuracy and consistency
- **Storage Efficiency**: Reduces redundant data storage
- **Maintenance Ease**: Simplifies updates and modifications
- **Query Flexibility**: Enables efficient data retrieval and manipulation

## Normal Forms

### First Normal Form (1NF)

#### Definition
A table is in 1NF if:
1. All attributes contain atomic (indivisible) values
2. Each attribute contains values of a single type
3. The table has a primary key
4. No repeating groups or arrays

#### Example
**Unnormalised Table:**
```
StudentID | Name    | Subjects
----------|---------|----------
1         | John    | Math, Physics, Chemistry
2         | Mary    | English, History
```

**1NF Table:**
```
StudentID | Name    | Subject
----------|---------|----------
1         | John    | Math
1         | John    | Physics
1         | John    | Chemistry
2         | Mary    | English
2         | Mary    | History
```

#### Common 1NF Violations
- Storing multiple values in a single field
- Having arrays or lists in table cells
- Missing primary keys

### Second Normal Form (2NF)

#### Definition
A table is in 2NF if:
1. It is in 1NF
2. All non-key attributes are fully functionally dependent on the entire primary key
3. No partial dependencies exist

#### Partial Dependency
A partial dependency occurs when a non-key attribute depends on only part of a composite primary key.

#### Example
**1NF Table with composite key:**
```
OrderID | ProductID | OrderDate | ProductName | ProductPrice | CustomerName
--------|-----------|-----------|-------------|--------------|-------------
1       | 101       | 2023-01-01| Widget A    | 10.99        | John Smith
1       | 102       | 2023-01-01| Widget B    | 15.50        | John Smith
2       | 101       | 2023-01-02| Widget A    | 10.99        | Jane Doe
```

**Problem**: ProductName and ProductPrice depend only on ProductID, not on (OrderID, ProductID)

**2NF Tables:**
```
Orders:
OrderID | OrderDate | CustomerName
--------|-----------|-------------
1       | 2023-01-01| John Smith
2       | 2023-01-02| Jane Doe

OrderDetails:
OrderID | ProductID | Quantity
--------|-----------|----------
1       | 101       | 2
1       | 102       | 1
2       | 101       | 3

Products:
ProductID | ProductName | ProductPrice
----------|-------------|--------------
101       | Widget A    | 10.99
102       | Widget B    | 15.50
```

### Third Normal Form (3NF)

#### Definition
A table is in 3NF if:
1. It is in 2NF
2. No transitive dependencies exist
3. Non-key attributes depend only on the primary key

#### Transitive Dependency
A transitive dependency occurs when a non-key attribute depends on another non-key attribute, which depends on the primary key.

#### Example
**2NF Table:**
```
StudentID | StudentName | CourseID | CourseName | InstructorID | InstructorName
----------|-------------|----------|------------|--------------|----------------
1         | John        | CS101    | Intro CS   | 201          | Prof. Smith
2         | Mary        | CS102    | Data Struct| 202          | Prof. Johnson
1         | John        | CS102    | Data Struct| 202          | Prof. Johnson
```

**Problems**:
- CourseName depends on CourseID (not StudentID)
- InstructorName depends on InstructorID (not StudentID)
- InstructorID depends on CourseID (transitive dependency)

**3NF Tables:**
```
Students:
StudentID | StudentName
----------|-------------
1         | John
2         | Mary

Courses:
CourseID | CourseName | InstructorID
---------|------------|--------------
CS101    | Intro CS   | 201
CS102    | Data Struct| 202

Instructors:
InstructorID | InstructorName
-------------|----------------
201          | Prof. Smith
202          | Prof. Johnson

Enrollments:
StudentID | CourseID
----------|----------
1         | CS101
1         | CS102
2         | CS102
```

## Normalisation Process

### Step-by-Step Approach

1. **Identify Entities and Attributes**
   - List all data elements
   - Group related attributes

2. **Create Initial Table**
   - Put all attributes in one large table
   - Identify a primary key

3. **Apply 1NF**
   - Remove repeating groups
   - Ensure atomic values
   - Create separate tables for multi-valued attributes

4. **Apply 2NF**
   - Identify partial dependencies
   - Move partially dependent attributes to separate tables
   - Create foreign key relationships

5. **Apply 3NF**
   - Identify transitive dependencies
   - Move transitively dependent attributes to separate tables
   - Ensure all non-key attributes depend only on the primary key

### Example: Library System Normalisation

**Initial Unnormalised Data:**
```
MemberID | Name    | Address       | BookID | Title          | Author     | LoanDate
---------|---------|---------------|--------|----------------|------------|----------
1        | John    | 123 Main St   | 101    | Database Design| Smith      | 2023-01-01
1        | John    | 123 Main St   | 102    | SQL Guide      | Johnson    | 2023-01-02
2        | Mary    | 456 Oak Ave   | 101    | Database Design| Smith      | 2023-01-03
```

**1NF:**
```
MemberID | Name    | Address       | BookID | Title          | Author     | LoanDate
---------|---------|---------------|--------|----------------|------------|----------
1        | John    | 123 Main St   | 101    | Database Design| Smith      | 2023-01-01
1        | John    | 123 Main St   | 102    | SQL Guide      | Johnson    | 2023-01-02
2        | Mary    | 456 Oak Ave   | 101    | Database Design| Smith      | 2023-01-03
```

**2NF:**
```
Members:
MemberID | Name    | Address
---------|---------|---------------
1        | John    | 123 Main St
2        | Mary    | 456 Oak Ave

Books:
BookID | Title          | Author
-------|----------------|-----------
101    | Database Design| Smith
102    | SQL Guide      | Johnson

Loans:
MemberID | BookID | LoanDate
---------|--------|----------
1        | 101    | 2023-01-01
1        | 102    | 2023-01-02
2        | 101    | 2023-01-03
```

**3NF:**
The tables are already in 3NF since all non-key attributes depend only on the primary key.

## Higher Normal Forms

### Boyce-Codd Normal Form (BCNF)
- Addresses anomalies not covered by 3NF
- Every determinant must be a candidate key

### Fourth Normal Form (4NF)
- Eliminates multi-valued dependencies
- Separates independent multi-valued attributes

### Fifth Normal Form (5NF)
- Deals with join dependencies
- Ensures lossless decomposition

## Practical Considerations

### Denormalisation
- **When to Denormalise**: For performance reasons in read-heavy systems
- **Trade-offs**: Increases redundancy but improves query performance
- **Examples**: Data warehouses, reporting databases

### Normalisation vs Performance
- **OLTP Systems**: Usually fully normalised for data integrity
- **OLAP Systems**: May be denormalised for query performance
- **Hybrid Approaches**: Normalised operational data, denormalised reporting data

## Common Normalisation Mistakes

### Over-Normalisation
- Creating too many tables
- Making queries complex and slow
- Losing business context

### Under-Normalisation
- Leaving redundant data
- Creating update anomalies
- Maintaining data consistency becomes difficult

### Incorrect Primary Key Selection
- Choosing inappropriate primary keys
- Leading to unnecessary complexity
- Missing important relationships

## Tools and Techniques

### Normalisation Tools
- **Database Design Software**: ERwin, Visio, MySQL Workbench
- **Analysis Scripts**: Custom scripts to detect dependencies
- **Dependency Diagrams**: Visual representation of functional dependencies

### Validation Techniques
- **Functional Dependency Analysis**: Identify all dependencies
- **Anomaly Testing**: Check for potential update/insert/delete anomalies
- **Business Rule Validation**: Ensure normalisation doesn't break business logic

## Summary

Database normalisation is a systematic approach to:
- **Eliminate Redundancy**: Remove duplicate data
- **Ensure Integrity**: Prevent data anomalies
- **Improve Efficiency**: Optimize storage and access
- **Enhance Maintainability**: Simplify database modifications

The three main normal forms (1NF, 2NF, 3NF) provide a solid foundation for most database designs. Higher normal forms address more complex scenarios but may not always be practical for every situation. The key is finding the right balance between normalisation benefits and practical constraints.
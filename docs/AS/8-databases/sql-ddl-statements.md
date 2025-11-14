# SQL DDL Statements

Data Definition Language (DDL) statements in SQL are used to define and modify the structure of database objects. This section covers the essential DDL statements for creating and managing database structures.

## CREATE DATABASE

### Purpose
Creates a new database within the database management system.

### Syntax
```sql
CREATE DATABASE database_name;
```

### Example
```sql
CREATE DATABASE SchoolManagement;
```

### Considerations
- Database name must be unique within the server
- May require administrative privileges
- Some systems allow additional options like character set and collation

## CREATE TABLE

### Purpose
Creates a new table with specified columns and constraints.

### Basic Syntax
```sql
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
    [table_constraints]
);
```

### Data Types

#### CHARACTER (CHAR)
- **Description**: Fixed-length character string
- **Syntax**: `CHAR(n)` or `CHARACTER(n)`
- **Usage**: When all values have the same length
- **Example**: `CHAR(10)` for postal codes

#### VARCHAR(n)
- **Description**: Variable-length character string
- **Syntax**: `VARCHAR(n)` or `VARCHAR2(n)`
- **Usage**: When values have varying lengths
- **Example**: `VARCHAR(50)` for names

#### BOOLEAN
- **Description**: True/false values
- **Syntax**: `BOOLEAN` or `BOOL`
- **Usage**: For yes/no, true/false fields
- **Example**: `BOOLEAN` for active status

#### INTEGER
- **Description**: Whole numbers
- **Syntax**: `INTEGER` or `INT`
- **Usage**: For counts, IDs, ages
- **Example**: `INTEGER` for student IDs

#### REAL
- **Description**: Floating-point numbers
- **Syntax**: `REAL` or `FLOAT` or `DOUBLE`
- **Usage**: For decimal values, measurements
- **Example**: `REAL` for grades or prices

#### DATE
- **Description**: Date values (year, month, day)
- **Syntax**: `DATE`
- **Usage**: For birth dates, order dates
- **Example**: `DATE` for enrollment date

#### TIME
- **Description**: Time values (hour, minute, second)
- **Syntax**: `TIME`
- **Usage**: For appointment times, timestamps
- **Example**: `TIME` for class start time

### Table Creation Examples

#### Simple Table
```sql
CREATE TABLE Students (
    StudentID INTEGER,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    Active BOOLEAN
);
```

#### Table with Constraints
```sql
CREATE TABLE Students (
    StudentID INTEGER NOT NULL,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    EnrollmentDate DATE,
    Active BOOLEAN DEFAULT TRUE
);
```

## PRIMARY KEY Constraint

### Purpose
Defines the primary key for a table, ensuring unique identification of records.

### Syntax
```sql
-- Column-level constraint
CREATE TABLE table_name (
    column_name datatype PRIMARY KEY,
    ...
);

-- Table-level constraint
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
    PRIMARY KEY (column1, column2)
);
```

### Examples

#### Single Column Primary Key
```sql
CREATE TABLE Students (
    StudentID INTEGER PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```

#### Composite Primary Key
```sql
CREATE TABLE Enrollments (
    StudentID INTEGER,
    CourseID INTEGER,
    EnrollmentDate DATE,
    PRIMARY KEY (StudentID, CourseID)
);
```

## FOREIGN KEY Constraint

### Purpose
Establishes relationships between tables by referencing primary keys of other tables.

### Syntax
```sql
-- Column-level constraint
CREATE TABLE table_name (
    column_name datatype REFERENCES parent_table(parent_column),
    ...
);

-- Table-level constraint
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
    FOREIGN KEY (column1) REFERENCES parent_table(parent_column)
);
```

### Examples

#### Simple Foreign Key
```sql
CREATE TABLE Enrollments (
    EnrollmentID INTEGER PRIMARY KEY,
    StudentID INTEGER REFERENCES Students(StudentID),
    CourseID INTEGER,
    EnrollmentDate DATE
);
```

#### Foreign Key with Multiple Columns
```sql
CREATE TABLE OrderItems (
    OrderID INTEGER,
    ProductID INTEGER,
    Quantity INTEGER,
    Price REAL,
    PRIMARY KEY (OrderID, ProductID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (ProductID) REFERENCES Products(ProductID)
);
```

## ALTER TABLE

### Purpose
Modifies the structure of an existing table.

### Common Operations

#### Adding Columns
```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype [constraints];
```

**Example:**
```sql
ALTER TABLE Students
ADD COLUMN Phone VARCHAR(20);
```

#### Modifying Columns
```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype [constraints];
```

**Example:**
```sql
ALTER TABLE Students
MODIFY COLUMN Email VARCHAR(150);
```

#### Dropping Columns
```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

**Example:**
```sql
ALTER TABLE Students
DROP COLUMN Phone;
```

#### Adding Constraints
```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name constraint_definition;
```

**Examples:**
```sql
ALTER TABLE Students
ADD CONSTRAINT pk_students PRIMARY KEY (StudentID);

ALTER TABLE Enrollments
ADD CONSTRAINT fk_student FOREIGN KEY (StudentID) REFERENCES Students(StudentID);
```

#### Dropping Constraints
```sql
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;
```

**Example:**
```sql
ALTER TABLE Students
DROP CONSTRAINT pk_students;
```

## Complete Examples

### University Database Schema

```sql
-- Create database
CREATE DATABASE UniversityDB;

-- Create Departments table
CREATE TABLE Departments (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName VARCHAR(100) NOT NULL,
    Building VARCHAR(50),
    Phone VARCHAR(20)
);

-- Create Professors table
CREATE TABLE Professors (
    ProfessorID INTEGER PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    DepartmentID INTEGER,
    HireDate DATE,
    Salary REAL,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INTEGER PRIMARY KEY,
    CourseCode VARCHAR(10) UNIQUE NOT NULL,
    CourseName VARCHAR(100) NOT NULL,
    DepartmentID INTEGER,
    Credits INTEGER,
    Description VARCHAR(500),
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);

-- Create Students table
CREATE TABLE Students (
    StudentID INTEGER PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    DateOfBirth DATE,
    EnrollmentDate DATE,
    MajorDepartmentID INTEGER,
    GPA REAL,
    Active BOOLEAN DEFAULT TRUE,
    FOREIGN KEY (MajorDepartmentID) REFERENCES Departments(DepartmentID)
);

-- Create Enrollments table
CREATE TABLE Enrollments (
    StudentID INTEGER,
    CourseID INTEGER,
    Semester VARCHAR(20),
    Year INTEGER,
    Grade VARCHAR(2),
    EnrollmentDate DATE,
    PRIMARY KEY (StudentID, CourseID, Semester, Year),
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

### Modifying Tables

```sql
-- Add new columns
ALTER TABLE Students
ADD COLUMN MiddleName VARCHAR(50);

ALTER TABLE Courses
ADD COLUMN Prerequisites VARCHAR(200);

-- Modify existing columns
ALTER TABLE Professors
MODIFY COLUMN Salary REAL NOT NULL;

-- Add new constraints
ALTER TABLE Students
ADD CONSTRAINT chk_gpa CHECK (GPA >= 0.0 AND GPA <= 4.0);

-- Create indexes for performance
CREATE INDEX idx_student_name ON Students (LastName, FirstName);
CREATE INDEX idx_course_dept ON Courses (DepartmentID);
```

## Understanding SQL Statements

### Statement Analysis
When reading SQL DDL statements, identify:

1. **Keywords**: CREATE, TABLE, ALTER, ADD, MODIFY, etc.
2. **Object Names**: Table names, column names, constraint names
3. **Data Types**: INTEGER, VARCHAR(n), DATE, etc.
4. **Constraints**: PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE
5. **References**: Which tables and columns are referenced

### Example Statement Breakdown
```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    CustomerID INTEGER NOT NULL,
    OrderDate DATE DEFAULT CURRENT_DATE,
    TotalAmount REAL,
    Status VARCHAR(20) DEFAULT 'Pending',
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

- **CREATE TABLE**: DDL command to create table
- **Orders**: Table name
- **OrderID INTEGER PRIMARY KEY**: Column with primary key constraint
- **CustomerID INTEGER NOT NULL**: Required foreign key column
- **FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)**: Relationship constraint

## Best Practices

### Naming Conventions
- Use consistent naming (PascalCase for tables, camelCase for columns)
- Use meaningful names that describe the data
- Avoid reserved words as object names

### Data Type Selection
- Choose appropriate data types for storage efficiency
- Consider future data ranges and precision needs
- Use VARCHAR instead of CHAR for variable-length text

### Constraint Design
- Always define primary keys
- Use foreign keys to maintain relationships
- Add check constraints for business rules
- Consider unique constraints for business requirements

### Performance Considerations
- Plan for indexes on frequently queried columns
- Consider table partitioning for large tables
- Use appropriate data types to minimize storage

These DDL statements form the foundation of database schema creation and management. Understanding how to read, write, and modify these statements is essential for database design and administration.
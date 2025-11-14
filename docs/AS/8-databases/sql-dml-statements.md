# SQL DML Statements

Data Manipulation Language (DML) statements in SQL are used to query and modify data in relational databases. This section covers the essential DML operations for retrieving and maintaining data.

## SELECT Statement

### Basic SELECT Syntax
```sql
SELECT column1, column2, ...
FROM table_name
[WHERE condition]
[ORDER BY column [ASC|DESC]]
[GROUP BY column]
[HAVING condition];
```

### SELECT Examples

#### Select All Columns
```sql
SELECT * FROM Students;
```

#### Select Specific Columns
```sql
SELECT FirstName, LastName, Email FROM Students;
```

#### Select with WHERE Clause
```sql
SELECT FirstName, LastName, GPA
FROM Students
WHERE GPA > 3.5;
```

#### Select with ORDER BY
```sql
SELECT FirstName, LastName, GPA
FROM Students
ORDER BY GPA DESC;
```

#### Select with Multiple Conditions
```sql
SELECT FirstName, LastName, EnrollmentDate
FROM Students
WHERE EnrollmentDate >= '2023-01-01'
  AND Active = TRUE
ORDER BY EnrollmentDate;
```

## JOIN Operations

### INNER JOIN
Combines rows from two tables based on a related column.

```sql
SELECT s.FirstName, s.LastName, c.CourseName, e.Grade
FROM Students s
INNER JOIN Enrollments e ON s.StudentID = e.StudentID
INNER JOIN Courses c ON e.CourseID = c.CourseID;
```

### Multiple Table Joins
```sql
SELECT s.FirstName, s.LastName, c.CourseName, p.FirstName as ProfFirst, p.LastName as ProfLast
FROM Students s
JOIN Enrollments e ON s.StudentID = e.StudentID
JOIN Courses c ON e.CourseID = c.CourseID
JOIN Professors p ON c.ProfessorID = p.ProfessorID
WHERE e.Grade = 'A';
```

## Aggregate Functions

### SUM, COUNT, AVG
```sql
-- Count total students
SELECT COUNT(*) as TotalStudents FROM Students;

-- Calculate average GPA
SELECT AVG(GPA) as AverageGPA FROM Students;

-- Sum of all course credits
SELECT SUM(Credits) as TotalCredits FROM Courses;
```

### GROUP BY with Aggregates
```sql
-- Students per department
SELECT d.DepartmentName, COUNT(s.StudentID) as StudentCount
FROM Departments d
LEFT JOIN Students s ON d.DepartmentID = s.MajorDepartmentID
GROUP BY d.DepartmentName;

-- Average GPA by department
SELECT d.DepartmentName, AVG(s.GPA) as AvgGPA
FROM Departments d
JOIN Students s ON d.DepartmentID = s.MajorDepartmentID
GROUP BY d.DepartmentName
ORDER BY AvgGPA DESC;
```

### GROUP BY with HAVING
```sql
-- Departments with more than 50 students
SELECT d.DepartmentName, COUNT(s.StudentID) as StudentCount
FROM Departments d
JOIN Students s ON d.DepartmentID = s.MajorDepartmentID
GROUP BY d.DepartmentName
HAVING COUNT(s.StudentID) > 50;
```

## INSERT Statement

### Basic INSERT Syntax
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### INSERT Examples

#### Insert Single Row
```sql
INSERT INTO Students (FirstName, LastName, Email, EnrollmentDate)
VALUES ('John', 'Doe', 'john.doe@university.edu', '2023-09-01');
```

#### Insert Multiple Rows
```sql
INSERT INTO Students (FirstName, LastName, Email, EnrollmentDate)
VALUES ('Jane', 'Smith', 'jane.smith@university.edu', '2023-09-01'),
       ('Bob', 'Johnson', 'bob.johnson@university.edu', '2023-09-01');
```

#### Insert with Subquery
```sql
INSERT INTO HighPerformers (StudentID, GPA)
SELECT StudentID, GPA
FROM Students
WHERE GPA >= 3.8;
```

## UPDATE Statement

### Basic UPDATE Syntax
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
[WHERE condition];
```

### UPDATE Examples

#### Update Single Column
```sql
UPDATE Students
SET GPA = 3.9
WHERE StudentID = 12345;
```

#### Update Multiple Columns
```sql
UPDATE Students
SET GPA = 4.0, Active = TRUE
WHERE StudentID = 12345;
```

#### Update with Subquery
```sql
UPDATE Students
SET GPA = (SELECT AVG(GPA) FROM Students WHERE Active = TRUE)
WHERE GPA IS NULL;
```

#### Update with JOIN
```sql
UPDATE Enrollments e
JOIN Courses c ON e.CourseID = c.CourseID
SET e.Grade = 'A+'
WHERE c.CourseName = 'Advanced Database' AND e.Grade = 'A';
```

## DELETE Statement

### Basic DELETE Syntax
```sql
DELETE FROM table_name
[WHERE condition];
```

### DELETE Examples

#### Delete Specific Records
```sql
DELETE FROM Students
WHERE StudentID = 12345;
```

#### Delete with Conditions
```sql
DELETE FROM Enrollments
WHERE Semester = 'Fall' AND Year = 2022;
```

#### Delete with Subquery
```sql
DELETE FROM Students
WHERE StudentID NOT IN (
    SELECT DISTINCT StudentID FROM Enrollments
);
```

## Complex DML Examples

### Student Enrollment Report
```sql
SELECT s.FirstName, s.LastName, COUNT(e.CourseID) as CoursesEnrolled,
       AVG(c.Credits) as AvgCredits, s.GPA
FROM Students s
LEFT JOIN Enrollments e ON s.StudentID = e.StudentID
LEFT JOIN Courses c ON e.CourseID = c.CourseID
WHERE s.Active = TRUE
GROUP BY s.StudentID, s.FirstName, s.LastName, s.GPA
HAVING COUNT(e.CourseID) > 0
ORDER BY s.GPA DESC, CoursesEnrolled DESC;
```

### Course Enrollment Statistics
```sql
SELECT c.CourseName, c.CourseCode, COUNT(e.StudentID) as EnrolledStudents,
       AVG(e.Grade) as AvgGrade, MAX(e.Grade) as BestGrade
FROM Courses c
LEFT JOIN Enrollments e ON c.CourseID = e.CourseID
WHERE e.Semester = 'Spring' AND e.Year = 2024
GROUP BY c.CourseID, c.CourseName, c.CourseCode
ORDER BY EnrolledStudents DESC;
```

### Department Performance Analysis
```sql
SELECT d.DepartmentName,
       COUNT(DISTINCT s.StudentID) as TotalStudents,
       AVG(s.GPA) as AvgDepartmentGPA,
       COUNT(DISTINCT c.CourseID) as TotalCourses,
       SUM(c.Credits) as TotalCreditsOffered
FROM Departments d
LEFT JOIN Students s ON d.DepartmentID = s.MajorDepartmentID
LEFT JOIN Courses c ON d.DepartmentID = c.DepartmentID
GROUP BY d.DepartmentID, d.DepartmentName
ORDER BY AvgDepartmentGPA DESC;
```

## Data Maintenance Scripts

### Bulk Update Student Status
```sql
-- Update inactive students (no enrollment in 2 years)
UPDATE Students
SET Active = FALSE
WHERE StudentID NOT IN (
    SELECT DISTINCT StudentID
    FROM Enrollments
    WHERE EnrollmentDate >= DATE_SUB(CURRENT_DATE, INTERVAL 2 YEAR)
);

-- Update student GPAs based on recent grades
UPDATE Students s
SET GPA = (
    SELECT AVG(GradePoint)
    FROM Enrollments e
    JOIN GradePoints gp ON e.Grade = gp.Grade
    WHERE e.StudentID = s.StudentID
      AND e.Semester = 'Spring' AND e.Year = 2024
)
WHERE EXISTS (
    SELECT 1 FROM Enrollments e
    WHERE e.StudentID = s.StudentID
      AND e.Semester = 'Spring' AND e.Year = 2024
);
```

### Clean Up Old Records
```sql
-- Archive old enrollments
INSERT INTO EnrollmentArchive
SELECT * FROM Enrollments
WHERE Year < 2020;

-- Delete archived records
DELETE FROM Enrollments
WHERE Year < 2020;

-- Remove inactive students with no recent activity
DELETE FROM Students
WHERE Active = FALSE
  AND StudentID NOT IN (
      SELECT StudentID FROM Enrollments
      WHERE EnrollmentDate >= '2020-01-01'
  );
```

## Best Practices

### Query Optimization
- Use appropriate WHERE clauses to limit result sets
- Create indexes on frequently queried columns
- Avoid SELECT * in production code
- Use JOINs instead of subqueries when possible

### Data Integrity
- Always use WHERE clauses with UPDATE and DELETE
- Test queries on sample data first
- Use transactions for multi-statement operations
- Validate data before insertion

### Performance Considerations
- Use LIMIT for large result sets
- Consider pagination for web applications
- Use EXPLAIN to analyze query execution plans
- Avoid correlated subqueries in large datasets

### Security
- Use parameterized queries to prevent SQL injection
- Grant minimal necessary permissions
- Validate user inputs before using in queries
- Use views to restrict data access

These DML statements form the core of database operations, enabling efficient data retrieval, modification, and analysis in relational database systems.
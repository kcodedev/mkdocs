# Relational Database Terminology

Relational databases use specific terminology to describe data organization, relationships, and operations. Understanding these terms is essential for designing, implementing, and working with relational database systems.

## Basic Data Structure Terms

### Entity
- **Definition**: A real-world object or concept that can be distinctly identified
- **Examples**: Customer, Product, Order, Employee, Department
- **Representation**: Becomes a table in the database
- **Characteristics**: Has attributes that describe its properties

### Table (Relation)
- **Definition**: A collection of related data organized in rows and columns
- **Synonyms**: Relation, entity set
- **Structure**: Two-dimensional structure with fixed columns and variable rows
- **Purpose**: Groups similar entities together for storage and manipulation

### Record (Tuple)
- **Definition**: A single row in a table representing one instance of an entity
- **Synonyms**: Row, tuple
- **Composition**: Contains values for each attribute of the entity
- **Uniqueness**: Each record is uniquely identified (usually by primary key)

### Field (Attribute)
- **Definition**: A single column in a table representing a characteristic of the entity
- **Synonyms**: Column, attribute
- **Properties**: Has a name, data type, and constraints
- **Domain**: Set of allowed values for the field

### Attribute
- **Definition**: A property or characteristic of an entity
- **Examples**: customer_name, product_price, order_date
- **Components**: Name, data type, size, constraints
- **Classification**: Simple vs. composite, single-valued vs. multi-valued

## Key Terms

### Primary Key
- **Definition**: A unique identifier for each record in a table
- **Requirements**: Must be unique and not null
- **Purpose**: Ensures entity integrity and provides fast access
- **Selection**: Usually the most appropriate unique identifier for the entity

### Candidate Key
- **Definition**: Any attribute or combination of attributes that could serve as a primary key
- **Characteristics**: Must be unique and minimal (no unnecessary attributes)
- **Examples**: Social Security Number, Email Address, License Plate Number
- **Selection**: One candidate key is chosen as the primary key

### Secondary Key (Alternate Key)
- **Definition**: A candidate key that was not selected as the primary key
- **Purpose**: Can be used for indexing and fast retrieval
- **Usage**: Often used in WHERE clauses for searching
- **Indexing**: Usually indexed for performance

### Foreign Key
- **Definition**: An attribute in one table that references the primary key of another table
- **Purpose**: Establishes relationships between tables
- **Constraints**: Must contain values that exist in the referenced table
- **Usage**: Enables joins and maintains referential integrity

## Relationship Terms

### Relationship Types

#### One-to-One (1:1)
- **Definition**: Each record in Table A relates to exactly one record in Table B, and vice versa
- **Examples**: Person ↔ Passport, Country ↔ Capital City
- **Implementation**: Foreign key in one table, unique constraint
- **Use Cases**: When splitting a table for security or performance reasons

#### One-to-Many (1:M)
- **Definition**: Each record in Table A can relate to multiple records in Table B, but each record in Table B relates to only one record in Table A
- **Examples**: Customer → Orders, Department → Employees
- **Implementation**: Foreign key in the "many" table
- **Most Common**: Represents hierarchical relationships

#### Many-to-Many (M:M)
- **Definition**: Each record in Table A can relate to multiple records in Table B, and vice versa
- **Examples**: Students ↔ Courses, Products ↔ Suppliers
- **Implementation**: Requires a junction/intermediate table
- **Resolution**: Split into two one-to-many relationships

### Relationship Representation
- **Entity-Relationship Diagrams**: Visual representation using crow's foot notation
- **Cardinality**: Indicates the number of related records (1:1, 1:M, M:M)
- **Participation**: Whether relationship is optional or mandatory
- **Degree**: Number of entities involved (unary, binary, ternary)

## Integrity Terms

### Referential Integrity
- **Definition**: Ensures that relationships between tables remain consistent
- **Rules**:
  - Foreign key values must exist in referenced table (no orphans)
  - Cannot delete referenced record if foreign keys exist
  - Cannot update primary key if foreign keys reference it
- **Enforcement**: Automatic by database management system
- **Importance**: Maintains data consistency across relationships

### Entity Integrity
- **Definition**: Ensures each record has a unique identifier
- **Requirements**: Primary key cannot be null, must be unique
- **Purpose**: Prevents duplicate or unidentified records
- **Enforcement**: Database constraints on primary key

### Domain Integrity
- **Definition**: Ensures data values fall within acceptable ranges
- **Methods**: Data types, check constraints, default values
- **Purpose**: Maintains data quality and consistency
- **Examples**: Age between 0-120, status in ('Active', 'Inactive')

## Performance Terms

### Indexing
- **Definition**: A data structure that improves the speed of data retrieval operations
- **Types**:
  - **Primary Index**: Automatically created on primary key
  - **Secondary Index**: Created on other attributes for fast access
  - **Composite Index**: Index on multiple columns
  - **Unique Index**: Prevents duplicate values
- **Benefits**: Faster searches, sorts, and joins
- **Trade-offs**: Slower inserts/updates, increased storage

### Index Types
- **B-Tree Index**: Balanced tree structure for range queries
- **Hash Index**: Fast exact-match lookups
- **Bitmap Index**: Efficient for low-cardinality columns
- **Full-Text Index**: For text search operations

## Schema Terms

### Logical Schema
- **Definition**: Conceptual view of database structure
- **Components**: Tables, relationships, constraints
- **Purpose**: Abstract representation independent of physical storage
- **Usage**: Database design and application development

### Physical Schema
- **Definition**: How data is actually stored on disk
- **Components**: File organization, indexing, partitioning
- **Purpose**: Optimize performance and storage efficiency
- **Usage**: Database administration and tuning

### Data Dictionary
- **Definition**: Metadata repository containing information about database objects
- **Contents**: Table definitions, column properties, relationships, constraints
- **Purpose**: Provides centralized information about database structure
- **Usage**: Application development, documentation, administration

## Query and Operation Terms

### Join
- **Definition**: Operation that combines rows from two or more tables based on related columns
- **Types**:
  - **Inner Join**: Returns matching rows from both tables
  - **Left Join**: Returns all rows from left table and matching rows from right
  - **Right Join**: Returns all rows from right table and matching rows from left
  - **Full Join**: Returns all rows from both tables
- **Purpose**: Retrieve related data across multiple tables

### View
- **Definition**: A virtual table based on the result of a SQL query
- **Purpose**: Simplify complex queries, provide security, hide complexity
- **Characteristics**: Doesn't store data, always up-to-date
- **Usage**: Data abstraction, security, query simplification

### Normalization
- **Definition**: Process of organizing data to minimize redundancy and dependency
- **Normal Forms**: 1NF, 2NF, 3NF, BCNF, 4NF, 5NF
- **Purpose**: Reduce data anomalies and improve data integrity
- **Benefits**: Easier maintenance, consistent updates

## Transaction Terms

### ACID Properties
- **Atomicity**: All operations succeed or all fail
- **Consistency**: Database remains in valid state
- **Isolation**: Transactions don't interfere with each other
- **Durability**: Changes survive system failures

### Concurrency Control
- **Locking**: Mechanisms to control access to data during transactions
- **Timestamp Ordering**: Assigns timestamps to transactions
- **Optimistic Concurrency**: Assumes conflicts are rare
- **Multiversion Concurrency**: Maintains multiple versions of data

## Summary

Mastering relational database terminology is essential for:

- **Design**: Creating effective database schemas
- **Implementation**: Building tables with proper relationships
- **Querying**: Writing efficient SQL statements
- **Maintenance**: Understanding performance and integrity issues
- **Communication**: Discussing database concepts with other professionals

These terms form the foundation of relational database theory and practice, enabling the creation of robust, efficient, and maintainable database systems.
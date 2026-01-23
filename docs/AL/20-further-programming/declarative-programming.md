# Declarative Programming

Declarative programming is a programming paradigm that expresses the logic of a computation without describing its control flow. Instead of specifying how to perform a task step by step, declarative programming focuses on what the program should accomplish.

## What is Declarative Programming?

In declarative programming, you describe the desired result rather than the steps to achieve it. The system (interpreter, compiler, or runtime) figures out how to execute the program.

### Key Characteristics

- **What, not How**: Specify what you want, not how to get it.
- **Abstraction**: Hide implementation details.
- **Optimization**: The system can optimize execution.
- **Readability**: Often more readable and maintainable.

## Types of Declarative Programming

### 1. Functional Programming

Functional programming treats computation as the evaluation of mathematical functions and avoids changing state and mutable data.

```haskell
-- Haskell example: Calculate factorial
factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Usage
result = factorial 5  -- Returns 120
```

```python
# Python functional example
from functools import reduce

def factorial(n):
    return reduce(lambda x, y: x * y, range(1, n + 1), 1)

result = factorial(5)  # Returns 120
```

### 2. Logic Programming

Logic programming uses formal logic to express programs. Prolog is a classic example.

```prolog
% Prolog example: Family relationships
parent(john, mary).
parent(mary, alice).
parent(mary, bob).

grandparent(X, Y) :- parent(X, Z), parent(Z, Y).

% Query: Who are John's grandchildren?
% ?- grandparent(john, X).
% X = alice
% X = bob
```

### 3. Database Query Languages

SQL is a declarative language for querying and manipulating databases.

```sql
-- SQL example: Find all customers who bought more than $1000
SELECT customer_name, SUM(order_amount) as total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY customer_name
HAVING SUM(order_amount) > 1000
ORDER BY total_spent DESC;
```

### 4. Markup Languages

HTML and CSS describe the structure and appearance of web pages declaratively.

```html
<!-- HTML: Structure -->
<div class="container">
  <h1>Welcome</h1>
  <p>This is a paragraph.</p>
</div>
```

```css
/* CSS: Styling */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  color: blue;
  font-size: 2em;
}
```

### 5. Configuration Languages

Languages like YAML, JSON, or XML for configuration.

```yaml
# YAML configuration
server:
  host: localhost
  port: 8080
  database:
    type: postgresql
    name: myapp
    credentials:
      username: admin
      password: secret
```

## Comparison with Imperative Programming

### Imperative Programming

```python
# Imperative: How to sum a list
def sum_list_imperative(numbers):
    total = 0
    for num in numbers:
        total += num
    return total

result = sum_list_imperative([1, 2, 3, 4, 5])  # 15
```

### Declarative Programming

```python
# Declarative: What to sum
def sum_list_declarative(numbers):
    return sum(numbers)

result = sum_list_declarative([1, 2, 3, 4, 5])  # 15
```

Or using functional approach:

```python
from functools import reduce

def sum_list_functional(numbers):
    return reduce(lambda x, y: x + y, numbers)

result = sum_list_functional([1, 2, 3, 4, 5])  # 15
```

## Advantages of Declarative Programming

1. **Conciseness**: Often requires less code to express complex operations.
2. **Readability**: Code describes intent rather than implementation details.
3. **Optimization**: The system can optimize execution automatically.
4. **Parallelization**: Easier to parallelize since dependencies are explicit.
5. **Maintainability**: Changes to implementation don't affect the declarative code.
6. **Mathematical Reasoning**: Based on mathematical principles, easier to reason about.

## Disadvantages of Declarative Programming

1. **Performance**: May have performance overhead due to abstraction layers.
2. **Debugging**: Can be harder to debug since control flow is implicit.
3. **Learning Curve**: Requires thinking in a different paradigm.
4. **Limited Control**: Less control over low-level optimizations.
5. **Tool Support**: May have less mature tools and libraries compared to imperative languages.

## Declarative Programming in Practice

### SQL for Data Manipulation

```sql
-- Create a view of high-value customers
CREATE VIEW high_value_customers AS
SELECT customer_id, customer_name, total_orders
FROM customers
WHERE total_orders > (
  SELECT AVG(total_orders)
  FROM customers
);

-- Query the view
SELECT * FROM high_value_customers
WHERE customer_name LIKE 'A%';
```

### HTML/CSS for Web Development

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .card { border: 1px solid #ccc; padding: 10px; margin: 10px; }
    .highlight { background-color: yellow; }
  </style>
</head>
<body>
  <div class="card highlight">
    <h2>Important Notice</h2>
    <p>This content is highlighted for attention.</p>
  </div>
</body>
</html>
```

### Functional Programming with JavaScript

```javascript
// Declarative data processing
const users = [
  { id: 1, name: 'Alice', age: 25, active: true },
  { id: 2, name: 'Bob', age: 30, active: false },
  { id: 3, name: 'Charlie', age: 35, active: true }
];

// Get names of active users over 25
const result = users
  .filter(user => user.active && user.age > 25)
  .map(user => user.name);

// Result: ['Charlie']
```

## Domain-Specific Languages (DSLs)

Declarative programming often involves creating DSLs for specific domains:

- **Make**: Build system declarations
- **Terraform**: Infrastructure as code
- **GraphQL**: API query language
- **Regular Expressions**: Pattern matching

```makefile
# Makefile example
CC=gcc
CFLAGS=-Wall -O2

all: program

program: main.o utils.o
	$(CC) $(CFLAGS) -o program main.o utils.o

main.o: main.c
	$(CC) $(CFLAGS) -c main.c

utils.o: utils.c
	$(CC) $(CFLAGS) -c utils.c

clean:
	rm -f *.o program
```

## When to Use Declarative Programming

1. **Data Processing**: When working with large datasets or complex queries.
2. **Configuration**: For system and application configuration.
3. **Web Development**: HTML/CSS for structure and styling.
4. **Database Operations**: SQL for data manipulation.
5. **Mathematical Computations**: Where functional approaches excel.
6. **Parallel Processing**: Where automatic optimization is beneficial.

## Conclusion

Declarative programming offers a powerful abstraction that allows developers to focus on what they want to achieve rather than how to achieve it. While it may have a steeper learning curve and potential performance trade-offs, it excels in scenarios where readability, maintainability, and automatic optimization are priorities. Understanding declarative concepts is essential in modern software development, especially in areas like web development, data processing, and configuration management.
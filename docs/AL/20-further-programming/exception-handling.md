# Exception Handling

Exception handling is a programming construct that allows programs to deal with unexpected situations (exceptions) that occur during execution. Instead of crashing when errors occur, programs can catch and handle these exceptions gracefully, improving robustness and user experience.

## What are Exceptions?

Exceptions are events that occur during program execution that disrupt the normal flow of instructions. They can be caused by:

- **Runtime errors**: Division by zero, accessing invalid memory
- **I/O errors**: File not found, network connection failed
- **Logic errors**: Invalid input, unexpected conditions
- **Resource issues**: Out of memory, disk full

## Basic Exception Handling

### Try-Except Blocks

The fundamental structure for exception handling:

```python
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Code to handle the exception
    print("Cannot divide by zero!")
```

### Multiple Except Blocks

Handle different types of exceptions separately:

```python
try:
    num = int(input("Enter a number: "))
    result = 100 / num
    print(f"Result: {result}")
except ValueError:
    print("Please enter a valid number")
except ZeroDivisionError:
    print("Cannot divide by zero")
```

### Generic Except Block

Catch any exception (use sparingly):

```python
try:
    # Risky code
    file = open("nonexistent.txt", "r")
except Exception as e:
    print(f"An error occurred: {e}")
```

## Exception Hierarchy

Exceptions form a hierarchy. In Python:

```
BaseException
├── SystemExit
├── KeyboardInterrupt
├── GeneratorExit
└── Exception
    ├── ArithmeticError
    │   ├── FloatingPointError
    │   ├── OverflowError
    │   └── ZeroDivisionError
    ├── ImportError
    │   └── ModuleNotFoundError
    ├── LookupError
    │   ├── IndexError
    │   └── KeyError
    ├── OSError
    │   ├── FileNotFoundError
    │   ├── PermissionError
    │   └── ConnectionError
    └── ValueError
        └── TypeError
```

Catch more specific exceptions before general ones.

## Raising Exceptions

### Using Raise

Manually raise exceptions when certain conditions occur:

```python
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    if age > 150:
        raise ValueError("Age seems unrealistic")

try:
    validate_age(-5)
except ValueError as e:
    print(f"Validation error: {e}")
```

### Re-raising Exceptions

Sometimes you want to catch an exception, perform some action, then re-raise it:

```python
try:
    risky_operation()
except ValueError as e:
    log_error(e)  # Log the error
    raise  # Re-raise the same exception
```

## Finally Block

Code that always executes, regardless of whether an exception occurred:

```python
file = None
try:
    file = open("example.txt", "r")
    content = file.read()
    print(content)
except FileNotFoundError:
    print("File not found")
finally:
    if file:
        file.close()
        print("File closed")
```

## Else Block

Code that executes only if no exception occurred:

```python
try:
    num = int(input("Enter a number: "))
except ValueError:
    print("Invalid input")
else:
    print(f"You entered: {num}")
    result = num * 2
    print(f"Double: {result}")
finally:
    print("Operation completed")
```

## Custom Exceptions

Create your own exception classes for specific error conditions:

```python
class InsufficientFundsError(Exception):
    """Raised when account has insufficient funds"""
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
        super().__init__(f"Insufficient funds: balance ${balance}, needed ${amount}")

class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientFundsError(self.balance, amount)
        self.balance -= amount
        return self.balance

# Usage
account = BankAccount(100)
try:
    account.withdraw(150)
except InsufficientFundsError as e:
    print(e)
```

## Exception Chaining

Link exceptions to show the chain of events:

```python
try:
    try:
        1 / 0
    except ZeroDivisionError as e:
        raise ValueError("Invalid calculation") from e
except ValueError as e:
    print(f"Final error: {e}")
    print(f"Caused by: {e.__cause__}")
```

## Context Managers and Exceptions

Context managers handle setup and cleanup automatically:

```python
class DatabaseConnection:
    def __init__(self, db_name):
        self.db_name = db_name
        self.connection = None

    def __enter__(self):
        self.connection = connect_to_database(self.db_name)
        return self.connection

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.connection:
            self.connection.close()
        if exc_type:
            print(f"Database error: {exc_val}")
        return False  # Don't suppress the exception

# Usage
with DatabaseConnection("mydb") as conn:
    # Use connection
    query_database(conn)
# Connection automatically closed
```

## Best Practices

### 1. Be Specific

Catch specific exceptions rather than using bare `except`:

```python
# Bad
try:
    # code
except:
    pass

# Good
try:
    # code
except (ValueError, TypeError) as e:
    handle_error(e)
```

### 2. Don't Suppress Exceptions

Avoid empty except blocks unless you have a good reason:

```python
# Bad
try:
    risky_operation()
except:
    pass  # Silent failure

# Better
try:
    risky_operation()
except KnownError:
    handle_gracefully()
```

### 3. Use Finally for Cleanup

Ensure resources are always cleaned up:

```python
# Good
with open("file.txt", "r") as f:
    process_file(f)

# Or manually
file = None
try:
    file = open("file.txt", "r")
    process_file(file)
finally:
    if file:
        file.close()
```

### 4. Handle Exceptions at the Right Level

Handle exceptions where you can actually do something about them:

```python
def read_config(filename):
    try:
        with open(filename, "r") as f:
            return parse_config(f.read())
    except FileNotFoundError:
        raise ConfigError(f"Configuration file {filename} not found")

def load_application():
    try:
        config = read_config("app.ini")
        initialize_app(config)
    except ConfigError as e:
        print(f"Configuration error: {e}")
        use_defaults()
```

### 5. Log Exceptions

Log exceptions for debugging, but don't expose sensitive information:

```python
import logging

try:
    risky_operation()
except Exception as e:
    logging.error(f"Operation failed: {e}", exc_info=True)
    raise
```

### 6. Use Custom Exceptions for APIs

Define custom exceptions for your libraries and APIs:

```python
class APIError(Exception):
    pass

class AuthenticationError(APIError):
    pass

class ValidationError(APIError):
    pass

def api_call():
    # API logic
    if not authenticated:
        raise AuthenticationError("Invalid credentials")
    if invalid_data:
        raise ValidationError("Invalid input data")
```

## Common Exception Patterns

### Retry Pattern

```python
import time

def retry_operation(max_attempts=3, delay=1):
    for attempt in range(max_attempts):
        try:
            return risky_operation()
        except TemporaryError as e:
            if attempt < max_attempts - 1:
                time.sleep(delay)
                continue
            else:
                raise
```

### Fallback Pattern

```python
def get_data(source):
    try:
        return get_from_primary_source(source)
    except PrimarySourceError:
        try:
            return get_from_backup_source(source)
        except BackupSourceError:
            return get_default_data()
```

### Circuit Breaker Pattern

```python
class CircuitBreaker:
    def __init__(self, failure_threshold=5):
        self.failure_threshold = failure_threshold
        self.failure_count = 0
        self.state = 'closed'

    def call(self, func, *args, **kwargs):
        if self.state == 'open':
            raise CircuitBreakerError("Circuit is open")

        try:
            result = func(*args, **kwargs)
            self.failure_count = 0  # Reset on success
            return result
        except Exception as e:
            self.failure_count += 1
            if self.failure_count >= self.failure_threshold:
                self.state = 'open'
            raise
```

## Exception Handling in Different Languages

### Java

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Division by zero: " + e.getMessage());
} finally {
    System.out.println("Always executed");
}
```

### C++

```cpp
try {
    throw std::runtime_error("Something went wrong");
} catch (const std::runtime_error& e) {
    std::cout << "Error: " << e.what() << std::endl;
}
```

### JavaScript

```javascript
try {
    throw new Error("Something went wrong");
} catch (error) {
    console.log("Error:", error.message);
} finally {
    console.log("Always executed");
}
```

## Testing Exception Handling

Write tests to ensure your exception handling works correctly:

```python
import pytest

def test_division_by_zero():
    with pytest.raises(ZeroDivisionError):
        1 / 0

def test_custom_exception():
    account = BankAccount(100)
    with pytest.raises(InsufficientFundsError):
        account.withdraw(150)
```

## Conclusion

Exception handling is crucial for writing robust, reliable software. By anticipating potential errors and handling them gracefully, you can create programs that fail safely and provide better user experiences. Remember to:

- Catch specific exceptions
- Use finally for cleanup
- Raise meaningful custom exceptions
- Log errors for debugging
- Test your exception handling code

Proper exception handling transforms fragile programs into resilient applications that can handle the unexpected gracefully.
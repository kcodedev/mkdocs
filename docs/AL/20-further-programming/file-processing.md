# File Processing

File processing is a fundamental aspect of programming that involves reading from and writing to files on disk. Files provide persistent storage for data, allowing programs to save information between executions and share data with other programs. This chapter covers the essential concepts and techniques for working with files in programming.

## File Concepts

### File Types

1. **Text Files**: Contain human-readable characters (e.g., .txt, .csv, .json)
2. **Binary Files**: Contain non-text data (e.g., .jpg, .mp3, .exe)
3. **Structured Files**: Have a specific format (e.g., .xml, .pdf)

### File Operations

- **Open**: Establish a connection to a file
- **Read**: Retrieve data from a file
- **Write**: Store data to a file
- **Close**: Terminate the connection to a file
- **Seek**: Move to a specific position in the file

## File Opening and Closing

### Opening Files

Most programming languages use a similar pattern for opening files:

```python
# Python
file = open('example.txt', 'r')  # Open for reading
```

```java
// Java
FileReader file = new FileReader("example.txt");
```

### File Modes

| Mode | Description | Python | Java |
|------|-------------|--------|------|
| Read | Open for reading | 'r' | FileReader |
| Write | Open for writing (overwrites) | 'w' | FileWriter |
| Append | Open for appending | 'a' | FileWriter (with append) |
| Read+Write | Open for both reading and writing | 'r+' | RandomAccessFile |

### Closing Files

Always close files after use to free system resources:

```python
file = open('example.txt', 'r')
# ... use file ...
file.close()
```

Or use context managers (Python):

```python
with open('example.txt', 'r') as file:
    # ... use file ...
    # File automatically closed when exiting the block
```

## Reading from Files

### Reading Entire Files

```python
# Read entire file as string
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)

# Read all lines into a list
with open('example.txt', 'r') as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())
```

### Reading Line by Line

```python
# Method 1: Using readline()
with open('example.txt', 'r') as file:
    line = file.readline()
    while line:
        print(line.strip())
        line = file.readline()

# Method 2: Iterating over file object
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())
```

### Reading Specific Amounts

```python
with open('example.txt', 'r') as file:
    # Read first 100 characters
    chunk = file.read(100)
    print(chunk)

    # Read next 50 characters
    chunk = file.read(50)
    print(chunk)
```

## Writing to Files

### Writing Text

```python
# Write a string
with open('output.txt', 'w') as file:
    file.write("Hello, World!\n")
    file.write("This is a new line.")

# Write multiple lines
lines = ["Line 1", "Line 2", "Line 3"]
with open('output.txt', 'w') as file:
    for line in lines:
        file.write(line + '\n')
```

### Appending to Files

```python
# Append to existing file
with open('output.txt', 'a') as file:
    file.write("This line will be appended.\n")
```

## File Positioning

### Seek and Tell

```python
with open('example.txt', 'r') as file:
    # Get current position
    position = file.tell()
    print(f"Current position: {position}")

    # Move to position 10
    file.seek(10)
    position = file.tell()
    print(f"New position: {position}")

    # Read from new position
    content = file.read(20)
    print(content)
```

## Working with Binary Files

### Reading Binary Data

```python
# Read binary file
with open('image.jpg', 'rb') as file:
    data = file.read()
    print(f"Read {len(data)} bytes")
```

### Writing Binary Data

```python
# Write binary data
binary_data = b'\x89PNG\r\n\x1a\n\x00\x00\x00\rIHDR'  # PNG header
with open('output.png', 'wb') as file:
    file.write(binary_data)
```

## File and Directory Operations

### Checking File Existence

```python
import os

if os.path.exists('example.txt'):
    print("File exists")
else:
    print("File does not exist")

if os.path.isfile('example.txt'):
    print("It's a file")

if os.path.isdir('mydir'):
    print("It's a directory")
```

### File Information

```python
import os

file_path = 'example.txt'

if os.path.exists(file_path):
    print(f"Size: {os.path.getsize(file_path)} bytes")
    print(f"Modified: {os.path.getmtime(file_path)}")
    print(f"Readable: {os.access(file_path, os.R_OK)}")
    print(f"Writable: {os.access(file_path, os.W_OK)}")
```

### Directory Operations

```python
import os

# Create directory
os.makedirs('new_directory', exist_ok=True)

# List directory contents
contents = os.listdir('.')
print("Directory contents:", contents)

# Change directory
os.chdir('new_directory')

# Get current working directory
cwd = os.getcwd()
print(f"Current directory: {cwd}")
```

## Error Handling in File Operations

### Common File Errors

- **FileNotFoundError**: File doesn't exist
- **PermissionError**: No permission to access file
- **IsADirectoryError**: Trying to read a directory as a file
- **FileExistsError**: Trying to create a file that already exists

### Handling Errors

```python
try:
    with open('nonexistent.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("File not found")
except PermissionError:
    print("Permission denied")
except Exception as e:
    print(f"An error occurred: {e}")
```

### Using try-except-finally

```python
file = None
try:
    file = open('example.txt', 'r')
    content = file.read()
    print(content)
except FileNotFoundError:
    print("File not found")
finally:
    if file:
        file.close()
        print("File closed")
```

## Working with CSV Files

CSV (Comma-Separated Values) files are common for data exchange.

```python
import csv

# Reading CSV
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Writing CSV
data = [
    ['Name', 'Age', 'City'],
    ['Alice', '25', 'New York'],
    ['Bob', '30', 'London']
]

with open('output.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

## Working with JSON Files

JSON is widely used for configuration and data exchange.

```python
import json

# Writing JSON
data = {
    "name": "Alice",
    "age": 25,
    "city": "New York",
    "hobbies": ["reading", "swimming"]
}

with open('data.json', 'w') as file:
    json.dump(data, file, indent=2)

# Reading JSON
with open('data.json', 'r') as file:
    loaded_data = json.load(file)
    print(loaded_data)
```

## File Encoding

### Text Encoding

```python
# Specify encoding
with open('utf8_file.txt', 'r', encoding='utf-8') as file:
    content = file.read()

# Write with specific encoding
with open('output.txt', 'w', encoding='utf-8') as file:
    file.write("Hello, 世界!")
```

## Best Practices

1. **Always use context managers** (`with` statement) to ensure files are closed
2. **Handle exceptions** appropriately for file operations
3. **Check file existence** before operations when necessary
4. **Use appropriate file modes** (read, write, append)
5. **Specify encoding** when working with text files
6. **Validate file paths** to prevent security issues
7. **Use relative paths** carefully; consider absolute paths for important files
8. **Backup important files** before overwriting
9. **Close files explicitly** if not using context managers

## Common Patterns

### Processing Large Files

```python
# Process large file line by line to save memory
def process_large_file(filename):
    with open(filename, 'r') as file:
        for line_number, line in enumerate(file, 1):
            # Process each line
            process_line(line.strip())
            if line_number % 1000 == 0:
                print(f"Processed {line_number} lines")

# Or process in chunks
def process_in_chunks(filename, chunk_size=1024):
    with open(filename, 'r') as file:
        while True:
            chunk = file.read(chunk_size)
            if not chunk:
                break
            process_chunk(chunk)
```

### File Copying

```python
def copy_file(source, destination):
    with open(source, 'rb') as src_file:
        with open(destination, 'wb') as dest_file:
            while True:
                chunk = src_file.read(4096)  # 4KB chunks
                if not chunk:
                    break
                dest_file.write(chunk)
```

## Conclusion

File processing is essential for most real-world applications. Understanding how to open, read, write, and manipulate files safely and efficiently is a core programming skill. Always consider error handling, resource management, and performance implications when working with files. The patterns and best practices covered in this chapter will help you write robust file-processing code.
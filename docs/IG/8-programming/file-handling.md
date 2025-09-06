# 📁 File Handling: Persistent Data Storage

Files allow programs to store and retrieve data permanently. This enables data to persist between program runs.

---

## 🎯 Purpose of Files

- **Persistent storage**: Data survives program termination
- **Large data sets**: Handle more data than memory allows
- **Data sharing**: Exchange information between programs
- **Backup**: Preserve important information

---

## 📂 File Operations

### Opening Files
```
OPENFILE <filename> FOR <mode>
```

**Modes:**
- **READ**: Read existing data
- **WRITE**: Create new file or overwrite existing

### Reading Data
```
READFILE <filename>, <variable>
```

### Writing Data
```
WRITEFILE <filename>, <variable>
```

### Closing Files
```
CLOSEFILE <filename>
```

---

## 📖 Reading Files

### Single Items
```
OPENFILE "data.txt" FOR READ
READFILE "data.txt", Name
READFILE "data.txt", Age
CLOSEFILE "data.txt"
```

### Lines of Text
```
OPENFILE "story.txt" FOR READ
READFILE "story.txt", Line
OUTPUT Line
CLOSEFILE "story.txt"
```

---

## ✍️ Writing Files

### Single Items
```
OPENFILE "results.txt" FOR WRITE
WRITEFILE "results.txt", Score
WRITEFILE "results.txt", Grade
CLOSEFILE "results.txt"
```

### Lines of Text
```
OPENFILE "log.txt" FOR WRITE
WRITEFILE "log.txt", "Program started"
WRITEFILE "log.txt", CurrentTime
CLOSEFILE "log.txt"
```

---

## 🔄 Complete Example

```
DECLARE Name : STRING
DECLARE Score : INTEGER

// Write data
OPENFILE "students.txt" FOR WRITE
WRITEFILE "students.txt", "Alice"
WRITEFILE "students.txt", 95
CLOSEFILE "students.txt"

// Read data
OPENFILE "students.txt" FOR READ
READFILE "students.txt", Name
READFILE "students.txt", Score
CLOSEFILE "students.txt"

OUTPUT "Student:", Name, "Score:", Score
```

---

## ⚠️ File Handling Best Practices

- **Always close files**: Prevent data corruption
- **Check file existence**: Handle missing files
- **Error handling**: Manage read/write errors
- **File paths**: Use correct paths and names
- **Permissions**: Ensure read/write access

---

## 📊 File Types

- **Text files**: Human-readable data
- **Binary files**: Machine-readable data
- **CSV files**: Comma-separated values
- **Configuration files**: Program settings

---

## 📝 **Key Points:**

- Files provide persistent data storage ✅
- Open files before use, close when done ✅
- READ mode for existing files, WRITE for new ✅
- Handle single items or lines of text ✅
- Proper error handling prevents data loss ✅

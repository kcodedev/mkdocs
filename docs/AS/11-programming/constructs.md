# Constructs 🔀

## Selection
``` plaintext
// IF Statement
IF condition THEN
    statements
ELSE
    statements
ENDIF

// Nested IF Statement
IF condition THEN
    statements
ELSE
    // IF Statement
    IF condition THEN
        statements
    ELSE
        statements
    ENDIF
ENDIF

// CASE Structure
CASE OF variable
    value1: statements
    value2: statements
    OTHERWISE: statements
ENDCASE
```


## Loops
```plaintext
// Count-Controlled Loop
FOR i ⟵ 1 TO 10
    statements
NEXT i

// Post-Condition Loop
REPEAT
    statements
UNTIL condition

// Pre-Condition Loop
WHILE condition
    statements
ENDWHILE
```

### Justifying Loop Choices 🤔

- Use count-controlled when you know the number of iterations in advance. 📊
- Use pre-condition when the loop might not execute at all (check before). 🔍
- Use post-condition when you need to execute the loop at least once (check after). 🔄

## Python Examples 🐍

```python
# IF statement
age = 18
if age >= 18:
    print("Adult")
else:
    print("Minor")

# Nested IF
if age >= 18:
    if age >= 65:
        print("Senior")
    else:
        print("Adult")
else:
    print("Minor")

# CASE (using if-elif)
grade = 'A'
if grade == 'A':
    print("Excellent")
elif grade == 'B':
    print("Good")
else:
    print("Needs improvement")

# Count-controlled loop
for i in range(1, 11):
    print(i)

# Post-condition (using while True)
total = 0
while True:
    num = int(input("Enter number (0 to stop): "))
    if num == 0:
        break
    total += num
print("Total:", total)

# Pre-condition
count = 0
while count < 5:
    print("Count:", count)
    count += 1
```
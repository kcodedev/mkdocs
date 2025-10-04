# 🔍 Debugging Algorithms

Debugging finds and fixes errors in algorithms. Systematic approach identifies issues and corrects them.

---

## 🔍 Types of Errors

- **Syntax Errors**: Incorrect language structure
- **Logic Errors**: Algorithm doesn't produce expected results
- **Runtime Errors**: Program crashes during execution

---

## 🧪 Debugging Process

1. **Reproduce the error**: Identify when/where it occurs
2. **Isolate the problem**: Narrow down the cause
3. **Analyze the code**: Check logic and calculations
4. **Fix the error**: Correct the identified issue
5. **Test the fix**: Verify the solution works

---

## 🛠️ Debugging Techniques

- **Trace tables**: Track variable values step-by-step
- **Print statements**: Output intermediate values
- **Breakpoints**: Pause execution at specific points
- **Code review**: Check logic manually
- **Test cases**: Use different input scenarios

---

## 🎯 Common Algorithm Errors

- **Off-by-one errors**: Loop runs one time too many/few
- **Infinite loops**: Conditions never become false
- **Incorrect calculations**: Wrong formulas or operations
- **Wrong variable scope**: Using variables outside their range
- **Missing conditions**: Not handling all possible cases

---

## 📋 Error Correction Methods

- **Fix logic**: Correct algorithmic thinking
- **Update conditions**: Ensure proper termination
- **Validate calculations**: Check mathematical operations
- **Handle edge cases**: Consider boundary conditions
- **Improve efficiency**: Optimize algorithm performance

---

## ✅ Verification

After fixing:
- **Re-test**: Run with original failing case
- **Test edge cases**: Check boundary conditions
- **Regression testing**: Ensure fix doesn't break other parts
- **Peer review**: Have someone else check the fix

---

## 🔍 Bug Examples

Here are practical examples of each error type in Python. Each includes a one-line description of the intended task, followed by buggy code, an explanation of the issue, and a corrected version.

### Syntax Error Example
**Intended Task:** Calculate and output the sum of numbers from 1 to 10.

**Buggy Code:**
```python
sum = 0
for i in range(1, 11):
    sum += i
print("Sum:", sum
```
**Explanation:** This is a syntax error due to the missing closing parenthesis in the print statement (`print("Sum:", sum`). Python's parser will raise a SyntaxError because the statement is incomplete. The code won't run at all.

**Corrected Code:**
```python
sum_val = 0
for i in range(1, 11):
    sum_val += i
print("Sum:", sum_val)
```

### Logic Error Example
**Intended Task:** Calculate the average of a list of numbers [1,2,3,4,5].

**Buggy Code:**
```python
# Calculate average of numbers [1,2,3,4,5]
numbers = [1,2,3,4,5]
total = 0
for i in range(len(numbers) + 1):  # Off-by-one: loops to 5, index 5 doesn't exist
    total += numbers[i]
average = total / len(numbers)
print(average)  # Outputs wrong average or crashes
```
**Explanation:** This is a logic error (off-by-one). The range is `range(6)` (0 to 5), but the list has indices 0-4, so `numbers[5]` causes an IndexError (runtime too), but if it didn't, total would include None or error. The average is incorrect. The code produces wrong output if bounds are handled, but here it crashes.

**Corrected Code:**
```python
numbers = [1,2,3,4,5]
total = 0
for i in range(len(numbers)):
    total += numbers[i]
average = total / len(numbers)
print(average)  # Outputs 3.0 correctly
```

### Runtime Error Example
**Intended Task:** Compute and output the result of each number divided by itself in the list [10, 0, 5].

**Buggy Code:**
```python
numbers = [10, 0, 5]
for i in range(len(numbers)):
    result = numbers[i] / numbers[i]  # Division by zero when i=1
    print(result)
```
**Explanation:** This causes a runtime error (ZeroDivisionError) when i=1, as `numbers[1]` is 0. The program crashes at that point without completing. Syntax and logic are fine up to execution, but the algorithm doesn't handle zero values, leading to an exception.

**Corrected Code:**
```python
numbers = [10, 0, 5]
for i in range(len(numbers)):
    if numbers[i] != 0:
        result = numbers[i] / numbers[i]
        print(result)
    else:
        print("Division by zero avoided")
```

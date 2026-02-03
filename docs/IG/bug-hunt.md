# Bug Hunt

Find the bugs in the following pseudocode examples! Each example has a problem description, buggy code, solution, and explanation.

---

## 1: Off-by-One Error in Array Sum

### Problem
Calculate the sum of all numbers in an array containing 5 elements.

### Buggy Code
```plaintext
numbers ← [3, 7, 2, 9, 5]
total ← 0
FOR i ← 0 TO LENGTH(numbers) DO
    total ← total + numbers[i]
NEXT i
OUTPUT "Total: ", total
```

### Solution
```plaintext
numbers ← [3, 7, 2, 9, 5]
total ← 0
FOR i ← 1 TO LENGTH(numbers) DO
    total ← total + numbers[i]
NEXT i
OUTPUT "Total: ", total
```

### Explanation
The bug is an **off-by-one error** caused by mixing indexing styles. If you start your loop at 0 (0-based indexing), you must end at `LENGTH(numbers) - 1`. If you start at 1 (1-based indexing), you should end at `LENGTH(numbers)`.

In the buggy code:
- The loop starts at 0 but ends at `LENGTH(numbers)` (which is 5)
- `numbers[0]` = 3 (first element, correct)
- `numbers[5]` tries to access a 6th element that doesn't exist!

The fix uses 1-based indexing consistently, ending at `LENGTH(numbers)`. Alternatively, you could keep 0-based indexing and end at `LENGTH(numbers) - 1`.

---

## 2: Infinite Loop

### Problem
Keep asking the user for a password until they enter "secret123".

### Buggy Code
```plaintext
password ← ""
WHILE password <> "secret123" DO
    OUTPUT "Enter password: "
    INPUT password
OUTPUT "Access granted!"
```

### Solution
```plaintext
password ← ""
WHILE password <> "secret123" DO
    OUTPUT "Enter password: "
    INPUT password
ENDWHILE
OUTPUT "Access granted!"
```

### Explanation
The bug is a **missing `ENDWHILE` statement**. In the buggy code, the loop never closes, which would cause the program to:
- Not execute the "Access granted!" message
- Potentially run forever or cause a syntax error

Always ensure loops have their proper closing statements (`ENDWHILE`, `NEXT i`, `UNTIL`).

---

## 3: Wrong Comparison Operator

### Problem
Check if a student's score (0-100) is passing. Passing grade is 40 or above.

### Buggy Code
```plaintext
OUTPUT "Enter your score: "
INPUT score
IF score < 40 THEN
    OUTPUT "You passed!"
ELSE
    OUTPUT "You failed."
ENDIF
```

### Solution
```plaintext
OUTPUT "Enter your score: "
INPUT score
IF score >= 40 THEN
    OUTPUT "You passed!"
ELSE
    OUTPUT "You failed."
ENDIF
```

### Explanation
The bug is using `< 40` instead of `>= 40`. The buggy code:
- Says "You passed!" when score is less than 40
- Says "You failed" when score is 40 or above

This is exactly backwards! The condition should check if the score is **greater than or equal to** 40 for passing.

---

## 4: Missing ELSE Branch

### Problem
Determine if a number is positive, negative, or zero.

### Buggy Code
```plaintext
OUTPUT "Enter a number: "
INPUT num
IF num > 0 THEN
    OUTPUT "Positive"
ENDIF
IF num < 0 THEN
    OUTPUT "Negative"
ENDIF
OUTPUT "Zero"
```

### Solution
```plaintext
OUTPUT "Enter a number: "
INPUT num
IF num > 0 THEN
    OUTPUT "Positive"
ELSE
    IF num < 0 THEN
        OUTPUT "Negative"
    ELSE
        OUTPUT "Zero"
    ENDIF
ENDIF
```

### Explanation
The buggy code has two issues:
1. Uses separate `IF` statements instead of `IF...ELSE...ENDIF`
2. Always outputs "Zero" regardless of input

If the user enters 5, the output would be:
```
Positive
Zero
```

The correct solution uses nested `IF...ELSE` statements to handle all three cases mutually exclusively.

---

## 5: Array Index Out of Bounds

### Problem
Find the largest number in an array of 4 elements.

### Buggy Code
```plaintext
numbers ← [12, 45, 7, 23]
max ← numbers[1]
FOR i ← 2 TO LENGTH(numbers) DO
    IF numbers[i] > max THEN
        max ← numbers[i]
    ENDIF
NEXT i
OUTPUT "Maximum: ", max
```

### Solution
```plaintext
numbers ← [12, 45, 7, 23]
max ← numbers[1]
FOR i ← 2 TO LENGTH(numbers) - 1 DO
    IF numbers[i] > max THEN
        max ← numbers[i]
    ENDIF
NEXT i
OUTPUT "Maximum: ", max
```

### Explanation
The bug is an **off-by-one error** when using 1-based indexing. If you're using 1-based indexing:
- The loop starts at 2 and should end at `LENGTH(numbers) - 1` (which is 3)
- `numbers[4]` in the buggy code tries to access a 5th element that doesn't exist

Using `LENGTH(numbers) - 1` makes the code work correctly for any size array and prevents "index out of bounds" errors.

---

## 6: Variable Not Initialized

### Problem
Count how many numbers in a list are greater than 10.

### Buggy Code
```plaintext
numbers ← [5, 15, 8, 22, 3]
FOR i ← 1 TO LENGTH(numbers) DO
    IF numbers[i] > 10 THEN
        count ← count + 1
    ENDIF
NEXT i
OUTPUT "Count: ", count
```

### Solution
```plaintext
numbers ← [5, 15, 8, 22, 3]
count ← 0
FOR i ← 1 TO LENGTH(numbers) DO
    IF numbers[i] > 10 THEN
        count ← count + 1
    ENDIF
NEXT i
OUTPUT "Count: ", count
```

### Explanation
The bug is using `count` without initializing it first. In the buggy code:
- `count` has no initial value (could be 0, could be random garbage)
- The first `count ← count + 1` would fail or produce wrong results

Always initialize variables before using them in calculations. Start `count` at 0.

---

## 7: CASE Without OTHERWISE

### Problem
Convert a numerical grade (1-5) to a letter grade.

### Buggy Code
```plaintext
OUTPUT "Enter grade (1-5): "
INPUT grade
CASE OF grade
    5
        OUTPUT "A*"
    4
        OUTPUT "A"
    3
        OUTPUT "B"
    2
        OUTPUT "C"
    1
        OUTPUT "D"
ENDCASE
```

### Solution
```plaintext
OUTPUT "Enter grade (1-5): "
INPUT grade
CASE OF grade
    5
        OUTPUT "A*"
    4
        OUTPUT "A"
    3
        OUTPUT "B"
    2
        OUTPUT "C"
    1
        OUTPUT "D"
    OTHERWISE
        OUTPUT "Invalid grade"
ENDCASE
```

### Explanation
The bug is missing an `OTHERWISE` clause. If the user enters:
- A number outside 1-5 (like 0 or 6)
- A non-numeric value

The program would produce no output or behave unexpectedly. The `OTHERWISE` clause handles unexpected input gracefully.

---

## 8: MOD Operator Bug

### Problem
Check if a number is divisible by 3.

### Buggy Code
```plaintext
OUTPUT "Enter a number: "
INPUT num
IF num MOD 3 = 3 THEN
    OUTPUT "Divisible by 3"
ELSE
    OUTPUT "Not divisible by 3"
ENDIF
```

### Solution
```plaintext
OUTPUT "Enter a number: "
INPUT num
IF num MOD 3 = 0 THEN
    OUTPUT "Divisible by 3"
ELSE
    OUTPUT "Not divisible by 3"
ENDIF
```

### Explanation
The bug is checking `= 3` instead of `= 0`. The modulo operator (`MOD`) returns the **remainder** after division:
- 9 MOD 3 = 0 (9 ÷ 3 = 3 with remainder 0)
- 10 MOD 3 = 1 (10 ÷ 3 = 3 with remainder 1)
- 11 MOD 3 = 2 (11 ÷ 3 = 3 with remainder 2)

A number is divisible by 3 if the remainder is 0, not 3 (remainder can never equal the divisor).

---

## 9: REPEAT UNTIL Logic Error

### Problem
Ask the user to enter a number between 1 and 10 until they do so.

### Buggy Code
```plaintext
REPEAT
    OUTPUT "Enter a number between 1 and 10: "
    INPUT num
UNTIL num >= 1 AND num <= 10
OUTPUT "Valid number entered!"
```

### Solution
```plaintext
REPEAT
    OUTPUT "Enter a number between 1 and 10: "
    INPUT num
    IF num < 1 OR num > 10 THEN
        OUTPUT "Invalid! Try again."
    ENDIF
UNTIL num >= 1 AND num <= 10
OUTPUT "Valid number entered!"
```

### Explanation
The bug isn't in the loop condition itself, but in **user experience**. The buggy code:
- Doesn't tell the user why their input was rejected
- Just keeps asking without feedback

A good program should inform the user of invalid input. The solution adds validation feedback inside the loop.

---

## 10: Inefficient Bubble Sort Passes

### Problem
Sort an array of numbers using bubble sort.

### Buggy Code
```plaintext
array ← [64, 34, 25, 12, 22, 11, 90]
FOR pass ← 1 TO 7 DO
    FOR i ← 1 TO 6 DO
        IF array[i] > array[i + 1] THEN
            temp ← array[i]
            array[i] ← array[i + 1]
            array[i + 1] ← temp
        ENDIF
    NEXT i
NEXT pass
OUTPUT "Sorted: ", array
```

### Solution
```plaintext
array ← [64, 34, 25, 12, 22, 11, 90]
last ← LENGTH(array)
REPEAT
    swapped ← FALSE
    FOR i ← 1 TO last - 1 DO
        IF array[i] > array[i + 1] THEN
            temp ← array[i]
            array[i] ← array[i + 1]
            array[i + 1] ← temp
            swapped ← TRUE
        ENDIF
    NEXT i
    last ← last - 1
UNTIL NOT swapped
OUTPUT "Sorted: ", array
```

### Explanation
The buggy code has two inefficiencies:
1. **Fixed 7 passes**: Always does 7 passes regardless of whether the array is sorted
2. **Fixed 6 comparisons per pass**: Doesn't reduce comparisons as elements get sorted

The efficient solution:
- Uses a `swapped` flag to detect when no swaps occur (array is sorted)
- Reduces the comparison range (`last`) after each pass
- Stops early if array is sorted before completing all passes

---
## 11: Linear Search with Early Exit Bug

### Problem
Search for a target value in an array and return its position (or -1 if not found).

### Buggy Code
```plaintext
FUNCTION LinearSearch(arr :ARRAY, target :INT) RETURNS INT
    FOR i ← 1 TO LENGTH(arr) DO
        IF arr[i] = target THEN
            RETURN i
        ENDIF
    NEXT i
    RETURN -1
ENDFUNCTION

// Test
numbers ← [4, 7, 2, 9, 5, 1]
result ← LinearSearch(numbers, 9)
OUTPUT "Found at position: ", result
```

### Solution
```plaintext
FUNCTION LinearSearch(arr :ARRAY, target :INT) RETURNS INT
    found ← FALSE
    position ← -1
    
    FOR i ← 1 TO LENGTH(arr) DO
        IF arr[i] = target THEN
            found ← TRUE
            position ← i
            // Bug fix: Don't return immediately if you need to count occurrences
            // For single occurrence, return i is fine
            RETURN i
        ENDIF
    NEXT i
    RETURN -1
ENDFUNCTION

// Test
numbers ← [4, 7, 2, 9, 5, 1]
result ← LinearSearch(numbers, 9)
OUTPUT "Found at position: ", result
```

### Explanation
This example shows a **subtle logical issue** with early exit in search algorithms. The code itself is mostly correct for finding a single occurrence. However, consider these scenarios:

1. **Finding all occurrences**: If you need to find ALL positions where the target appears, returning immediately would miss duplicates.
2. **Multiple targets**: The algorithm can only return the first occurrence.

For finding all occurrences, you would need:
```plaintext
FUNCTION FindAllOccurrences(arr :ARRAY, target :INT) RETURNS ARRAY
    results ← []
    FOR i ← 1 TO LENGTH(arr) DO
        IF arr[i] = target THEN
            APPEND i TO results
        ENDIF
    NEXT i
    RETURN results
ENDFUNCTION
```

The original code is correct for finding if a value exists or returning its first position - just be aware of its limitations.

---

## 12: Average Calculator with Division Bug

### Problem
Calculate the average of a list of exam scores. The average is the total divided by the count.

### Buggy Code
```plaintext
scores ← [85, 90, 78, 92, 88]
FOR i ← 1 TO LENGTH(scores) DO
    total ← total + scores[i]
NEXT i

average ← total / LENGTH(scores)
OUTPUT "Total: ", total
OUTPUT "Average: ", average

// Check if average passes (pass mark is 80)
IF average >= 80 THEN
    OUTPUT "Class passed!"
ELSE
    OUTPUT "Class failed."
ENDIF
```

### Solution
```plaintext
scores ← [85, 90, 78, 92, 88]
total ← 0
FOR i ← 1 TO LENGTH(scores) DO
    total ← total + scores[i]
NEXT i

average ← total / LENGTH(scores)
OUTPUT "Total: ", total
OUTPUT "Average: ", average

// Check if average passes (pass mark is 80)
IF average >= 80 THEN
    OUTPUT "Class passed!"
ELSE
    OUTPUT "Class failed."
ENDIF
```

### Explanation
The bug is using `total` before initializing it. In the buggy code:
- `total` has no initial value (could be 0, could be random garbage from memory)
- The first iteration adds `scores[1]` to an undefined value
- This leads to incorrect calculations or runtime errors

**Always initialize accumulators** (`total`, `count`, etc.) before using them in loops. Start `total` at 0.

**Additional consideration**: In some programming languages, integer division could cause issues. If using languages like Python 2 or some languages with floor division, you might get 86.6 as 86. For accurate averages, ensure floating-point division is used.

---

## 13: Temperature Converter with Formula Error

### Problem
Convert temperatures between Celsius and Fahrenheit.
- Celsius to Fahrenheit: F = (C × 9/5) + 32
- Fahrenheit to Celsius: C = (F - 32) × 5/9

### Buggy Code
```plaintext
OUTPUT "Temperature Converter"
OUTPUT "1. Celsius to Fahrenheit"
OUTPUT "2. Fahrenheit to Celsius"
OUTPUT "Enter choice (1 or 2): "
INPUT choice

IF choice = 1 THEN
    OUTPUT "Enter Celsius temperature: "
    INPUT celsius
    fahrenheit ← (celsius * 9/5) + 32
    OUTPUT celsius, "C = ", fahrenheit, "F"
ELSE
    OUTPUT "Enter Fahrenheit temperature: "
    INPUT fahrenheit
    celsius ← (fahrenheit - 32) * 5/9
    OUTPUT fahrenheit, "F = ", celsius, "C"
ENDIF
```

### Solution
```plaintext
OUTPUT "Temperature Converter"
OUTPUT "1. Celsius to Fahrenheit"
OUTPUT "2. Fahrenheit to Celsius"
OUTPUT "Enter choice (1 or 2): "
INPUT choice

IF choice = 1 THEN
    OUTPUT "Enter Celsius temperature: "
    INPUT celsius
    fahrenheit ← (celsius * 9/5) + 32
    OUTPUT celsius, "C = ", fahrenheit, "F"
ELSE IF choice = 2 THEN
    OUTPUT "Enter Fahrenheit temperature: "
    INPUT fahrenheit
    celsius ← (fahrenheit - 32) * 5/9
    OUTPUT fahrenheit, "F = ", celsius, "C"
ELSE
    OUTPUT "Invalid choice!"
ENDIF
```

### Explanation
The bug is in the **ELSE clause handling**. If the user enters:
- `3`, `0`, `-1`, or any number other than 1 or 2
- A non-numeric input

The buggy code will:
1. Incorrectly treat it as a Fahrenheit to Celsius conversion
2. Display a prompt for "Fahrenheit temperature" even though the user didn't choose that option
3. Produce meaningless results

The fix adds an `ELSE` clause that handles invalid input gracefully by showing an error message.

---

## 14: Grade Calculator with Boundary Error

### Problem
Calculate the grade based on marks (0-100):
- A*: 90-100
- A: 80-89
- B: 70-79
- C: 60-69
- D: 50-59
- U: Below 50

### Buggy Code
```plaintext
OUTPUT "Enter your marks (0-100): "
INPUT marks

CASE OF marks
    90 TO 100
        grade ← "A*"
    80 TO 89
        grade ← "A"
    70 TO 79
        grade ← "B"
    60 TO 69
        grade ← "C"
    50 TO 59
        grade ← "D"
ENDCASE

IF marks >= 50 THEN
    OUTPUT "Your grade: ", grade
ELSE
    OUTPUT "Your grade: U"
ENDIF
```

### Solution
```plaintext
OUTPUT "Enter your marks (0-100): "
INPUT marks

CASE OF marks
    90 TO 100
        grade ← "A*"
    80 TO 89
        grade ← "A"
    70 TO 79
        grade ← "B"
    60 TO 69
        grade ← "C"
    50 TO 59
        grade ← "D"
    OTHERWISE
        grade ← "U"
ENDCASE

OUTPUT "Your grade: ", grade
```

### Explanation
The bug is in how the U grade is handled. The buggy code has two issues:

1. **Boundary overlap**: If marks = 50, the CASE assigns grade = "D", then the IF checks `marks >= 50` and outputs "U" - this would display "Your grade: U" for 50 marks, which is wrong!

2. **Missing OTHERWISE**: The CASE doesn't have an OTHERWISE clause to handle marks outside 0-100 or invalid input.

The fix moves the U grade into an OTHERWISE clause in the CASE statement, eliminating the need for the separate IF check and ensuring all invalid marks are handled correctly.

---

## Bug Hunt Tips

1. **Read the problem first** - Understand what the code should do
2. **Trace through the code** - Follow the logic step by step
3. **Check loop boundaries** - Off-by-one errors are common
4. **Verify conditions** - Make sure comparisons are correct
5. **Look for missing pieces** - Missing ENDIF, ENDWHILE, initialization
6. **Test edge cases** - What happens with 0, negative numbers, empty arrays?

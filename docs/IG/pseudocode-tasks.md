# Pseudocode Practice Tasks

## Input and Output

### 1: Basic Input and Output
```plaintext
// get the user to input two numbers 
// calculate the sum
// output the answer with a message
```
```plaintext
OUTPUT "Enter the first number: "
INPUT num1
OUTPUT "Enter the second number: "
INPUT num2
sum ← num1 + num2
OUTPUT "The sum is: ", sum
```

### 2: String Concatenation
```
// get the user to enter their name
// give a personalized hello
// also tell them the length of their name
```
```
OUTPUT "Enter your name: "
INPUT name

name_length ← LENGTH(name)

OUTPUT "Hello, ", name, "! Your name has ", name_length, " characters."
```

### 3: Using IF Statements
```
// ask the user for today’s weather
// if it is sunny tell them to wear shades
// or if it’s rainy tell them take an umbrella
// else offer them generic advice
// an IF is an example of what programming concept?
```
```
OUTPUT "What is today's weather? (sunny/rainy/other): "
INPUT weather
IF weather = "sunny" THEN
   OUTPUT "It's sunny! Wear shades."
ELSE
   IF weather = "rainy" THEN
       OUTPUT "It's rainy! Take an umbrella."
   ELSE
       OUTPUT "Stay prepared for any weather!"
   ENDIF
ENDIF
```

### 4: Nested IF
```
// Get user to enter age
// if they are 12 or less say they are a child
// if they are 13-19 say teenager
// >19 say adult
```
```
OUTPUT "Enter your age: "
INPUT age
IF age <= 12 THEN
   OUTPUT "You are a child."
ELSE
   IF age <= 19 THEN
       OUTPUT "You are a teenager."
   ELSE
       OUTPUT "You are an adult."
   ENDIF
ENDIF
```

### 5: FOR 
FOR loops are **count-controlled** loops.
```
// Write a FOR a loop that outputs numbers 1 TO 10
// Another to output all the even numbers from 0 to 50 (inc)
// Another to Output all the odd numbers 0-50
```
```
// First loop: Outputs numbers 1 to 10
FOR i ← 1 TO 10 DO
   OUTPUT i
NEXT i

// Second loop: Outputs all even numbers from 0 to 50
FOR i ← 0 TO 50 STEP 2 DO
   OUTPUT i
NEXT i

// Third loop: Outputs all odd numbers from 1 to 50
FOR i ← 1 TO 50 STEP 2 DO
   OUTPUT i
NEXT i
```

### 6: CASE
CASE statements allow selection based on a value matching multiple options (Cambridge compliant: use CASE OF with OTHERWISE).
```
// Ask user for a score (0-100)
// Use CASE to determine grade: 90+ A, 80-89 B, 70-79 C, 60-69 D, <60 Fail
// Output the grade
```
```
OUTPUT "Enter score (0-100): "
INPUT score

CASE OF score
   90 TO 100
      OUTPUT "Grade: A"
   80 TO 89
      OUTPUT "Grade: B"
   70 TO 79
      OUTPUT "Grade: C"
   60 TO 69
      OUTPUT "Grade: D"
   OTHERWISE
      OUTPUT "Grade: Fail"
ENDCASE
```

### 7: Using MOD
```
// Write a FOR that loops 50 times 1 TO 50
// Checks if a number is even or odd
// If even outputs “2 EVEN” for example
// If odd outputs “7 ODD” for example
// With an arrow label the type of loop
```
```
FOR count ← 1 TO 50 DO
   IF count MOD 2 = 0 THEN
       OUTPUT count, " EVEN"
   ELSE
       OUTPUT count, " ODD"
   ENDIF
NEXT count
```

### 8: WHILE 
While loops are **pre-condition loops**.
```
// Ask the user repeatedly:
// "What is the capital of Thailand?" until they answer correctly
// Use a while loop
// With an arrow label the type of loop
```
```
correct_answer ← "Bangkok"
guess ← ""

WHILE guess <> correct_answer DO
   OUTPUT "What is the capital of Thailand?"
   INPUT guess
ENDWHILE

OUTPUT "Correct! The capital of Thailand is Bangkok."
```

### 9: REPEAT UNTIL 
REPEAT UNTIL is a **post-condition-loop**,.
```
// Ask the user repeatedly 
// "Capital of Thailand?" until they answer correctly
// Use a repeat until loop
// With an arrow label the type of loop
```
```
correct_answer ← "Bangkok"

REPEAT
   OUTPUT "Capital of Thailand?"
   INPUT guess
UNTIL guess = correct_answer

OUTPUT "Correct! The capital of Thailand is Bangkok."
```

### 10: Array Processing
```
// Loop through an array of 5 scores
// numbers ← [5, 6, 11, 3, 5]
// Calculate the total and average score
// Use a count controlled loop
```
```
total ← 0
num_items ← 5
numbers ← [5, 6, 11, 3, 5]
FOR i ← 0 TO num_items - 1 DO
   total ← total + numbers[i]
NEXT i

average ← total / num_items
OUTPUT "Total: ", total
OUTPUT "Average: ", average
```

### 11: PROCEDURE 1
```
// Define a cats meowing procedure (subroutine)
// no parameters, no loops
// call the procedure after defining it
```
```
PROCEDURE CatMeow()
   OUTPUT "Meow!"
ENDPROCEDURE

// Call the procedure
CALL CatMeow()
```

### 12: PROCEDURE 2
```
// Define a custom cat meowing procedure (subroutine)
// It receives num, an INT, as a parameter 
// Loop that many times and “meow”
// Call the procedure and give it a number
```
```
PROCEDURE CatMeow(num :INT)
   FOR i ← 1 TO num DO
       OUTPUT "Meow!"
   NEXT i
ENDPROCEDURE

CALL CatMeow(3)
```

### 13: FUNCTION
```
// Write a function (subroutine) to 
// find the max number in a list
// return the max number from the function
// Example list you could use: nums = [3,6,4,9,2] 
```
```
FUNCTION FindMax(my_list : ARRAY INT)
   max ← my_list[0]  // Assume first num is the max
   FOR i ← 1 TO LENGTH(my_list) - 1 DO
       IF my_list[i] > max THEN
           max ← my_list[i]
       ENDIF
   NEXT i
   RETURN max
ENDFUNCTION
max_value ← FindMax([3, 7, 2, 9, 5])
OUTPUT "The maximum value is: ", max_value
```

### 14: Linear Search
```
// Search for a target value in an array using linear search
// Example array: numbers = [5, 3, 8, 1, 4]
// Target: 8
// Output if found (position) or not found
// Linear search is sequential from start to end
```
```
numbers ← [5, 3, 8, 1, 4]
found ← FALSE
position ← -1
OUTPUT "Enter an item to search for: "
INPUT target
FOR i ← 0 TO LENGTH(numbers) - 1 DO
   IF numbers[i] = target THEN
      found ← TRUE
      position ← i
      EXIT  // Optional: stop once found
   ENDIF
NEXT i
IF found THEN
   OUTPUT "Target ", target, " found at position ", position
ELSE
   OUTPUT "Target not found"
ENDIF
```

### 15: Variable Swapping
```
// Write code to swap two variables x and y. 
// x ← 2
// y ← 5
```
```
x ← 2
y ← 5
temp ← x
x ← y
y ← temp

OUTPUT "x: ", x
OUTPUT "y: ", y
```

### 16: Efficient Bubble Sort
```
// Write the code for bubble sort
// The efficient version that uses a flag
```
```
last ← LENGTH(array)
first ← 1    // Start at index 1 for 1-based indexing
REPEAT
   swap ← FALSE   // Reset swapped flag for each pass
   FOR counter ← first TO last - 1 DO
       IF array[counter] > array[counter + 1] THEN
           temp ← array[counter]
           array[counter] ← array[counter + 1]
           array[counter + 1] ← temp        
           swap ← TRUE   // Mark that a swap has occurred
       ENDIF
   NEXT counter
   last ← last - 1  // Decrease the range of comparison as elements are sorted
UNTIL NOT swap OR last = first  // Continue until no swaps or sorted
```

### 17: 2D Array Processing
```plaintext
// A 2d array stores teams, wins, points. 
// Currently all points are set to 0. 
// Write code to update points to be wins times 3.
```
```plaintext
League ← [['Man U', 4, 0], ['Man C', 3, 0], ['Liverpool', 2, 0], ['Gooners', 1, 0], ['Chelsea', 0, 0]]
FOR i ← 0 TO LENGTH(League) - 1 DO
    League[i][2] ← League[i][1] * 3
NEXT i
// Optionally output the updated league
FOR i ← 0 TO LENGTH(League) - 1 DO
    OUTPUT League[i][0], " has ", League[i][2], " points"
NEXT i
```
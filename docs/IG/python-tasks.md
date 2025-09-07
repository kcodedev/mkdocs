# Python Practice Tasks

## Input and Output

### 1: Basic Input and Output
```python
# get the user to input two numbers
# calculate the sum
# output the answer with a message
```
```python
print("Enter the first number: ")
num1 = int(input())
print("Enter the second number: ")
num2 = int(input())
sum_val = num1 + num2
print("The sum is:", sum_val)
```

### 2: String Concatenation
```python
# get the user to enter their name
# give a personalized hello
# also tell them the length of their name
```
```python
print("Enter your name: ")
name = input()
name_length = len(name)
print("Hello,", name + "! Your name has", name_length, "characters.")
```

### 3: Using IF Statements
```python
# ask the user for today's weather
# if it is sunny tell them to wear shades
# or if it's rainy tell them take an umbrella
# else offer them generic advice
# an IF is an example of what programming concept?
```
```python
print("What is today's weather? (sunny/rainy/other): ")
weather = input()
if weather == "sunny":
    print("It's sunny! Wear shades.")
elif weather == "rainy":
    print("It's rainy! Take an umbrella.")
else:
    print("Stay prepared for any weather!")
```

### 4: Nested IF
```python
# Get user to enter age
# if they are 12 or less say they are a child
# if they are 13-19 say teenager
# >19 say adult
```
```python
print("Enter your age: ")
age = int(input())
if age <= 12:
    print("You are a child.")
elif age <= 19:
    print("You are a teenager.")
else:
    print("You are an adult.")
```

### 5: FOR
FOR loops are **count-controlled** loops.
```python
# Write a FOR a loop that outputs numbers 1 TO 10
# Another to output all the even numbers from 0 to 50 (inc)
# Another to Output all the odd numbers 0-50
```
```python
# First loop: Outputs numbers 1 to 10
for i in range(1, 11):
    print(i)

# Second loop: Outputs all even numbers from 0 to 50
for i in range(0, 51, 2):
    print(i)

# Third loop: Outputs all odd numbers from 1 to 50
for i in range(1, 51, 2):
    print(i)
```

### 6: Using MOD
```python
# Write a FOR that loops 50 times 1 TO 50
# Checks if a number is even or odd
# If even outputs "2 EVEN" for example
# If odd outputs "7 ODD" for example
# With an arrow label the type of loop
```
```python
for count in range(1, 51):
    if count % 2 == 0:
        print(count, "EVEN")
    else:
        print(count, "ODD")
```

### 7: WHILE
While loops are **pre-condition loops**.
```python
# Ask the user repeatedly:
# "What is the capital of Thailand?" until they answer correctly
# Use a while loop
# With an arrow label the type of loop
```
```python
correct_answer = "Bangkok"
guess = ""
while guess != correct_answer:
    print("What is the capital of Thailand?")
    guess = input()
print("Correct! The capital of Thailand is Bangkok.")
```

### 8: REPEAT UNTIL
REPEAT UNTIL is a **post-condition-loop**.
```python
# Ask the user repeatedly
# "Capital of Thailand?" until they answer correctly
# Use a repeat until loop
# With an arrow label the type of loop
```
```python
correct_answer = "Bangkok"
while True:
    print("Capital of Thailand?")
    guess = input()
    if guess == correct_answer:
        break
print("Correct! The capital of Thailand is Bangkok.")
```

### 9: Array Processing
```python
# Loop through an array of 5 scores
# numbers ← [5, 6, 11, 3, 5]
# Calculate the total and average score
# Use a count controlled loop
```
```python
total = 0
num_items = 5
numbers = [5, 6, 11, 3, 5]
for i in range(num_items):
    total += numbers[i]
average = total / num_items
print("Total:", total)
print("Average:", average)
```

### 10: PROCEDURE 1
```python
# Define a cats meowing procedure (subroutine)
# no parameters, no loops
# call the procedure after defining it
```
```python
def CatMeow():
    print("Meow!")

# Call the procedure
CatMeow()
```

### 11: PROCEDURE 2
```python
# Define a custom cat meowing procedure (subroutine)
# It receives num, an INT, as a parameter
# Loop that many times and "meow"
# Call the procedure and give it a number
```
```python
def CatMeow(num):
    for i in range(num):
        print("Meow!")

CatMeow(3)
```

### 12: FUNCTION
```python
# Write a function (subroutine) to
# find the max number in a list
# return the max number from the function
# Example list you could use: nums = [3,6,4,9,2]
```
```python
def FindMax(my_list):
    max_val = my_list[0]  # Assume first num is the max
    for i in range(1, len(my_list)):
        if my_list[i] > max_val:
            max_val = my_list[i]
    return max_val

max_value = FindMax([3, 7, 2, 9, 5])
print("The maximum value is:", max_value)
```

### 13: Variable Swapping
```python
# Write code to swap two variables x and y.
x = 2
y = 5
```
```python
temp = x
x = y
y = temp
print("x:", x)
print("y:", y)
```

### 14: Efficient Bubble Sort
```python
# Write the code for bubble sort
# The efficient version that uses a flag
```
```python
last = len(array)
first = 0
while True:
    swap = False  # Reset swapped flag for each pass
    for counter in range(first, last - 1):
        if array[counter] > array[counter + 1]:
            temp = array[counter]
            array[counter] = array[counter + 1]
            array[counter + 1] = temp
            swap = True
    last -= 1
    if not swap or last == first:
        break
```
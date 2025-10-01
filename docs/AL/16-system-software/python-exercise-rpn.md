# Reverse Polish Notation Calculator Problem 🐍

**Task:**  
Write a Python program to evaluate Reverse Polish Notation (RPN) expressions.

Your program should:

1. Take an RPN expression as input (a string like "3 4 +").
2. Use a stack to evaluate the expression.
3. Support basic arithmetic operators: +, -, *, /
4. Output the final result.

Assume the input is a valid RPN expression with space-separated tokens.

---

## Step-by-Step Guidance

### Step 1 — Set up the stack
- Use a Python list as your stack.
- Initialize an empty list: `stack = []`

### Step 2 — Process the input
- Split the input string into tokens using `split()`.
- Loop through each token in the list.

### Step 3 — Handle numbers and operators
- If the token is a number (use `isdigit()` or try-except for int conversion):
  - Convert to integer and push onto the stack (`stack.append(int(token))`).
- If the token is an operator:
  - Pop two operands from the stack (right operand first, then left).
  - Apply the operation.
  - Push the result back onto the stack.

### Step 4 — Get the result
- After processing all tokens, the stack should contain exactly one element.
- Pop and return that element as the result.

---

**Example to test:**  
Input: `3 4 +`

- Push 3: stack = [3]
- Push 4: stack = [3, 4]
- +: pop 4 and 3, compute 3 + 4 = 7, push 7: stack = [7]

Result: 7

**Another example:**  
Input: `5 1 2 + 4 * + 3 -`

This evaluates to ((5 + ((1 + 2) * 4)) - 3) = 14

- Push 5: [5]
- Push 1: [5, 1]
- Push 2: [5, 1, 2]
- +: pop 2 and 1, 1+2=3, push 3: [5, 3]
- Push 4: [5, 3, 4]
- *: pop 4 and 3, 3*4=12, push 12: [5, 12]
- +: pop 12 and 5, 5+12=17, push 17: [17]
- Push 3: [17, 3]
- -: pop 3 and 17, 17-3=14, push 14: [14]

Result: 14
# Reverse Polish Notation (RPN)

## Introduction

Reverse Polish Notation (RPN), also known as postfix notation, is a mathematical notation where operators follow their operands. Unlike the more common infix notation (e.g., `3 + 4`), RPN places the operator after the values it operates on (e.g., `3 4 +`). This eliminates the need for parentheses to indicate precedence, making it easier for computers to parse and evaluate expressions.

RPN is used in some calculators (like Hewlett-Packard calculators) and in stack-based programming languages or compilers for expression evaluation.

## Evaluating Expressions with RPN

RPN expressions are evaluated using a stack data structure. The process involves:

1. **Scanning the expression** from left to right.
2. **Pushing operands** (numbers) onto the stack.
3. **When an operator is encountered**, popping the required number of operands from the stack, performing the operation, and pushing the result back onto the stack.
4. **At the end**, the stack should contain a single value, which is the result.

### Example: Simple Addition

Evaluate `3 4 +`:

- Push 3 onto the stack: [3]
- Push 4 onto the stack: [3, 4]
- Encounter `+`: Pop 4 and 3, compute 3 + 4 = 7, push 7: [7]

Result: 7

### Example: More Complex Expression

Evaluate `5 1 2 + 4 * + 3 -` (equivalent to infix `5 + ((1 + 2) * 4) - 3`):

1. Push 5: [5]
2. Push 1: [5, 1]
3. Push 2: [5, 1, 2]
4. `+`: Pop 2 and 1, 1 + 2 = 3, push 3: [5, 3]
5. Push 4: [5, 3, 4]
6. `*`: Pop 4 and 3, 3 * 4 = 12, push 12: [5, 12]
7. `+`: Pop 12 and 5, 5 + 12 = 17, push 17: [17]
8. Push 3: [17, 3]
9. `-`: Pop 3 and 17, 17 - 3 = 14, push 14: [14]

Result: 14

### Algorithm for Evaluation

To evaluate an RPN expression:

- Initialize an empty stack.
- For each token in the expression:
  - If token is a number, push it onto the stack.
  - If token is an operator:
    - Pop the required operands (usually 2 for binary operators).
    - Apply the operation.
    - Push the result onto the stack.
- After processing all tokens, the stack should have one element, the result.

This method avoids the need for parsing precedence rules, as the order of operations is implicit in the postfix arrangement.

## Advantages of RPN

- **No parentheses needed**: Precedence is handled by the order.
- **Efficient evaluation**: Stack-based processing is fast and straightforward for computers.
- **Reduced ambiguity**: Eliminates issues with operator precedence in complex expressions.

RPN is particularly useful in compiler design for generating intermediate code or in calculators for quick computation without ambiguity.
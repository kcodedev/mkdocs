# Stack Unwinding in Recursion

Stack unwinding is the process that occurs when a recursive function reaches its base case and begins returning values back up the call stack. Each recursive call adds a new frame to the stack, and when the base case is hit, the stack "unwinds" as each frame returns its result to the caller.

## How It Works

1. **Building the Stack**: Each recursive call pushes a new stack frame onto the call stack.
2. **Base Case**: When the base case is reached, the function returns a value.
3. **Unwinding**: The returned value propagates back through the stack, with each frame computing its result and returning it to the previous frame.

Let's visualize this with an example.

## Example: Factorial with Stack Unwinding

Consider the recursive factorial function:

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)
```

When we call `factorial(3)`, here's what happens step by step:

### Step 1: Initial Call - factorial(3)
The stack starts with the call to factorial(3).

| Stack Frame | n | Operation |
|-------------|---|-----------|
| factorial(3) | 3 | Waiting for factorial(2) |

### Step 2: Recursive Call - factorial(2)
factorial(3) calls factorial(2), adding it to the stack.

| Stack Frame | n | Operation |
|-------------|---|-----------|
| factorial(3) | 3 | Waiting for factorial(2) |
| factorial(2) | 2 | Waiting for factorial(1) |

### Step 3: Recursive Call - factorial(1)
factorial(2) calls factorial(1), adding it to the stack.

| Stack Frame | n | Operation |
|-------------|---|-----------|
| factorial(3) | 3 | Waiting for factorial(2) |
| factorial(2) | 2 | Waiting for factorial(1) |
| factorial(1) | 1 | Base case reached, return 1 |

### Step 4: Unwinding - factorial(1) returns 1
factorial(1) returns 1 to factorial(2).

| Stack Frame | n | Operation |
|-------------|---|-----------|
| factorial(3) | 3 | Waiting for factorial(2) |
| factorial(2) | 2 | Compute 2 * 1 = 2, return 2 |

### Step 5: Unwinding - factorial(2) returns 2
factorial(2) returns 2 to factorial(3).

| Stack Frame | n | Operation |
|-------------|---|-----------|
| factorial(3) | 3 | Compute 3 * 2 = 6, return 6 |

### Step 6: Final Return
factorial(3) returns 6, and the stack is empty.

The final result is 6.

## Another Example: Fibonacci

Let's look at the Fibonacci function:

```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)
```

For `fibonacci(3)`:

### Building the Stack
- fibonacci(3) calls fibonacci(2) and fibonacci(1)
- fibonacci(2) calls fibonacci(1) and fibonacci(0)

The stack gets more complex due to multiple recursive calls.

| Stack Frame | n | Operation |
|-------------|---|-----------|
| fibonacci(3) | 3 | Waiting for fibonacci(2) + fibonacci(1) |
| fibonacci(2) | 2 | Waiting for fibonacci(1) + fibonacci(0) |
| fibonacci(1) | 1 | Base case, return 1 |
| fibonacci(0) | 0 | Base case, return 0 |

### Unwinding
- fibonacci(0) returns 0
- fibonacci(1) returns 1
- fibonacci(2) computes 1 + 0 = 1, returns 1
- fibonacci(3) computes 1 + 1 = 2, returns 2

This shows how the stack builds and unwinds, with each frame contributing to the final result.

## Key Points

- The stack grows with each recursive call.
- Unwinding happens when base cases are reached.
- Each return value is used by the calling frame.
- Deep recursion can lead to stack overflow if the stack limit is exceeded.

Understanding stack unwinding helps in debugging recursive functions and optimizing them.
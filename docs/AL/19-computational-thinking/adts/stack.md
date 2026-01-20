# 📚 Stack Tutorial

## 📚 What is a Stack?

A stack is a linear data structure that follows the Last In, First Out (LIFO) principle. This means that the last item added to the stack is the first one to be removed. Think of it like a stack of plates in a cafeteria - you add plates to the top and remove plates from the top.

Stacks are commonly used in programming for tasks like:
- Function call management (call stack)
- Undo operations in text editors
- Expression evaluation and syntax parsing
- Browser back button functionality

---

## 📋 Stack Operations

### Basic Operations

1. **Push**: Add an item to the top of the stack
2. **Pop**: Remove and return the item from the top of the stack
3. **Peek/Top**: Look at the top item without removing it
4. **Is Empty**: Check if the stack has no items
5. **Size**: Get the number of items in the stack

### Stack Properties

- **Limited Size**: Our stack will have a maximum capacity of 8 items
- **LIFO Order**: Last item pushed is first item popped
- **Underflow**: Attempting to pop from an empty stack
- **Overflow**: Attempting to push onto a full stack

---

## 👁️ Visual Example

Let's simulate a stack with maximum size 8. We'll start with an empty stack and perform some operations:

```
Initial Stack: [] (empty, size 0/8)

Push(5): [5] (size 1/8)
Push(3): [5, 3] (size 2/8)
Push(8): [5, 3, 8] (size 3/8)

Pop(): Returns 8, Stack now: [5, 3] (size 2/8)
Pop(): Returns 3, Stack now: [5] (size 1/8)

Push(2): [5, 2] (size 2/8)
Push(7): [5, 2, 7] (size 3/8)
Push(1): [5, 2, 7, 1] (size 4/8)
```

---

## 🐍 Building the Python Solution

### Stack Implementation with Limited Size

We'll implement the stack using a Python list with a fixed size of 8, initialized with `None` values. We'll write functions to perform stack operations on this list.

```python
# Initialize stack with fixed size of 8, all None
MAX_SIZE = 8
stack = [None] * MAX_SIZE
top = -1

def push(item):
    """
    Add an item to the top of the stack
    Returns True if successful, False if stack is full
    """
    global top
    if top >= MAX_SIZE - 1:
        print("Stack Overflow - Cannot push, stack is full")
        return False
    top += 1
    stack[top] = item
    return True

def pop():
    """
    Remove and return the top item from the stack
    Returns None if stack is empty
    """
    global top
    if top == -1:
        print("Stack Underflow - Cannot pop, stack is empty")
        return None
    item = stack[top]
    stack[top] = None  # Clear the position
    top -= 1
    return item

def peek():
    """
    Return the top item without removing it
    Returns None if stack is empty
    """
    if top == -1:
        return None
    return stack[top]

def is_empty():
    """
    Check if the stack is empty
    """
    return top == -1

def size():
    """
    Return the current number of items in the stack
    """
    return top + 1

def display_stack():
    """
    Display the current state of the stack
    """
    print(f"Stack: {stack} (size {size()}/{MAX_SIZE})")

# Test the stack implementation
print("Initial stack:")
display_stack()

push(5)
print("After push(5):")
display_stack()

push(3)
push(8)
print("After push(3), push(8):")
display_stack()

popped = pop()
print(f"Popped: {popped}")
display_stack()

push(2)
push(7)
push(1)
print("After more pushes:")
display_stack()
```

## 💪 Practice Exercises

### Exercise 1: Implement the Push Function

Implement the `push` function for a stack with limited size. The function should:

- Check if the stack is full (top >= MAX_SIZE - 1)
- If full, print "Stack Overflow - Cannot push" and return False
- If not full, increment top, set stack[top] = item, and return True

```python
# Global variables
MAX_SIZE = 8
stack = [None] * MAX_SIZE
top = -1

def push(item):
    # Your implementation here
    pass

# Test your implementation
push(1)
push(2)
print(f"Stack: {stack}")  # Should show [1, 2, None, None, None, None, None, None]
print(f"Top: {top}")  # Should be 1
```

**Reveal Answer** (don't peek until you've tried!)

```python
def push(item):
    global top
    if top >= MAX_SIZE - 1:
        print("Stack Overflow - Cannot push")
        return False
    top += 1
    stack[top] = item
    return True
```

### Exercise 2: Implement the Pop Function

Implement the `pop` function. It should:

- Check if the stack is empty (top == -1)
- If empty, print "Stack Underflow - Cannot pop" and return None
- If not empty, get the item, set stack[top] = None, decrement top, and return the item

```python
# Global variables
MAX_SIZE = 8
stack = [None] * MAX_SIZE
top = -1

def pop():
    # Your implementation here
    pass

# Test your implementation
stack[0] = 5
stack[1] = 10
top = 1
popped = pop()
print(f"Popped: {popped}")  # Should be 10
print(f"Stack: {stack}")  # Should show [5, None, None, None, None, None, None, None]
print(f"Top: {top}")  # Should be 0
```

**Reveal Answer**

```python
def pop():
    global top
    if top == -1:
        print("Stack Underflow - Cannot pop")
        return None
    item = stack[top]
    stack[top] = None
    top -= 1
    return item
```

### Exercise 3: Complete Stack Implementation

Put it all together! Create all the stack functions we've discussed. Test it with various operations including trying to push onto a full stack and pop from an empty stack.

```python
# Global variables
MAX_SIZE = 3  # Small stack for testing limits
stack = [None] * MAX_SIZE
top = -1

# Your complete implementation here
def push(item):
    pass

def pop():
    pass

def peek():
    pass

def is_empty():
    pass

def size():
    pass

def display_stack():
    pass

# Test your complete implementation
push(1)
push(2)
push(3)
display_stack()

# Test overflow
push(4)  # Should fail
display_stack()

# Test normal pops
print("Pop:", pop())
print("Pop:", pop())
display_stack()

# Test underflow
print("Pop:", pop())
print("Pop:", pop())  # Should fail
display_stack()
```

**Reveal Complete Answer**

```python
def push(item):
    global top
    if top >= MAX_SIZE - 1:
        print("Stack Overflow - Cannot push")
        return False
    top += 1
    stack[top] = item
    return True

def pop():
    global top
    if top == -1:
        print("Stack Underflow - Cannot pop")
        return None
    item = stack[top]
    stack[top] = None
    top -= 1
    return item

def peek():
    if top == -1:
        return None
    return stack[top]

def is_empty():
    return top == -1

def size():
    return top + 1

def display_stack():
    print(f"Stack: {stack} (size {size()}/{MAX_SIZE})")
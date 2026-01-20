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

## 🧠 Pseudocode for Stack Operations

### Push Operation

```
PROCEDURE Push(item)
    IF stack is full THEN
        OUTPUT "Stack Overflow - Cannot push"
        RETURN
    ENDIF
    Add item to top of stack
ENDPROCEDURE
```

### Pop Operation

```
FUNCTION Pop()
    IF stack is empty THEN
        OUTPUT "Stack Underflow - Cannot pop"
        RETURN null
    ENDIF
    item ← top item from stack
    Remove top item from stack
    RETURN item
ENDFUNCTION
```

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

```python
class LimitedStack:
    """
    A stack implementation with a maximum size limit of 8 items
    Uses a Python list as the underlying data structure
    """
    
    def __init__(self, max_size=8):
        self.stack = []
        self.max_size = max_size
    
    def push(self, item):
        """
        Add an item to the top of the stack
        Returns True if successful, False if stack is full
        """
        if len(self.stack) >= self.max_size:
            print("Stack Overflow - Cannot push, stack is full")
            return False
        self.stack.append(item)
        return True
    
    def pop(self):
        """
        Remove and return the top item from the stack
        Returns None if stack is empty
        """
        if not self.stack:
            print("Stack Underflow - Cannot pop, stack is empty")
            return None
        return self.stack.pop()
    
    def peek(self):
        """
        Return the top item without removing it
        Returns None if stack is empty
        """
        if not self.stack:
            return None
        return self.stack[-1]
    
    def is_empty(self):
        """
        Check if the stack is empty
        """
        return len(self.stack) == 0
    
    def size(self):
        """
        Return the current number of items in the stack
        """
        return len(self.stack)
    
    def __str__(self):
        """
        String representation of the stack
        """
        return f"Stack: {self.stack} (size {self.size()}/{self.max_size})"

# Test the stack implementation
stack = LimitedStack()

print("Initial:", stack)

stack.push(5)
print("After push(5):", stack)

stack.push(3)
stack.push(8)
print("After push(3), push(8):", stack)

popped = stack.pop()
print(f"Popped: {popped}, Stack now:", stack)

stack.push(2)
stack.push(7)
stack.push(1)
print("After more pushes:", stack)
```

---

## 💪 Practice Exercises

### Exercise 1: Convert Push Pseudocode to Python

Based on the pseudocode above, implement the `push` method for our `LimitedStack` class. The method should:

- Check if the stack is full (size >= max_size)
- If full, print "Stack Overflow - Cannot push" and return False
- If not full, add the item to the stack and return True


```python
class LimitedStack:
    def __init__(self, max_size=8):
        self.stack = []
        self.max_size = max_size
    
    def push(self, item):
        # Your implementation here
        pass
    
    # ... other methods ...

# Test your implementation
stack = LimitedStack()
stack.push(1)
stack.push(2)
print(stack)  # Should show [1, 2]
```

**Reveal Answer** (don't peek until you've tried!)

```python
def push(self, item):
    if len(self.stack) >= self.max_size:
        print("Stack Overflow - Cannot push")
        return False
    self.stack.append(item)
    return True
```

### Exercise 2: Convert Pop Pseudocode to Python

Now implement the `pop` method. It should:

- Check if the stack is empty
- If empty, print "Stack Underflow - Cannot pop" and return None
- If not empty, remove and return the top item


```python
class LimitedStack:
    def __init__(self, max_size=8):
        self.stack = []
        self.max_size = max_size
    
    def pop(self):
        # Your implementation here
        pass
    
    # ... other methods ...

# Test your implementation
stack = LimitedStack()
stack.push(5)
stack.push(10)
popped = stack.pop()
print(f"Popped: {popped}")  # Should be 10
print(stack)  # Should show [5]
```

**Reveal Answer**

```python
def pop(self):
    if not self.stack:
        print("Stack Underflow - Cannot pop")
        return None
    return self.stack.pop()
```

### Exercise 3: Complete Stack Class

Put it all together! Create a complete `LimitedStack` class with all the methods we've discussed. Test it with various operations including trying to push onto a full stack and pop from an empty stack.

```python
class LimitedStack:
    # Your complete implementation here
    pass

# Test your complete implementation
stack = LimitedStack(3)  # Small stack for testing limits

# Test normal operations
stack.push(1)
stack.push(2)
stack.push(3)
print("After pushes:", stack)

# Test overflow
stack.push(4)  # Should fail
print("After overflow attempt:", stack)

# Test normal pops
print("Pop:", stack.pop())
print("Pop:", stack.pop())
print("Stack now:", stack)

# Test underflow
print("Pop:", stack.pop())
print("Pop:", stack.pop())  # Should fail
print("Final stack:", stack)
```

**Reveal Complete Answer**

```python
class LimitedStack:
    def __init__(self, max_size=8):
        self.stack = []
        self.max_size = max_size
    
    def push(self, item):
        if len(self.stack) >= self.max_size:
            print("Stack Overflow - Cannot push")
            return False
        self.stack.append(item)
        return True
    
    def pop(self):
        if not self.stack:
            print("Stack Underflow - Cannot pop")
            return None
        return self.stack.pop()
    
    def peek(self):
        if not self.stack:
            return None
        return self.stack[-1]
    
    def is_empty(self):
        return len(self.stack) == 0
    
    def size(self):
        return len(self.stack)
    
    def __str__(self):
        return f"Stack: {self.stack} (size {self.size()}/{self.max_size})"
```
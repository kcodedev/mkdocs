# 📚 Queue Tutorial

## 📚 What is a Queue?

A queue is a linear data structure that follows the First In, First Out (FIFO) principle. This means that the first item added to the queue is the first one to be removed. Think of it like a line of people waiting at a ticket counter - the person who arrives first gets served first.

Queues are commonly used in programming for tasks like:
- Task scheduling in operating systems
- Print job management
- Breadth-first search algorithms
- Message queues in networking

---

## 📋 Queue Operations

### Basic Operations

1. **Enqueue**: Add an item to the rear (back) of the queue
2. **Dequeue**: Remove and return the item from the front of the queue
3. **Peek/Front**: Look at the front item without removing it
4. **Is Empty**: Check if the queue has no items
5. **Size**: Get the number of items in the queue

### Queue Properties

- **Limited Size**: Our queue will have a maximum capacity of 8 items
- **FIFO Order**: First item enqueued is first item dequeued
- **Underflow**: Attempting to dequeue from an empty queue
- **Overflow**: Attempting to enqueue onto a full queue

---

## 👁️ Visual Example

Let's simulate a queue with maximum size 8. We'll start with an empty queue and perform some operations:

```
Initial Queue: [] (empty, size 0/8)

Enqueue(5): [5] (size 1/8)
Enqueue(3): [5, 3] (size 2/8)
Enqueue(8): [5, 3, 8] (size 3/8)

Dequeue(): Returns 5, Queue now: [3, 8] (size 2/8)
Dequeue(): Returns 3, Queue now: [8] (size 1/8)

Enqueue(2): [8, 2] (size 2/8)
Enqueue(7): [8, 2, 7] (size 3/8)
Enqueue(1): [8, 2, 7, 1] (size 4/8)
```

---

## 🐍 Building the Python Solution

### Simple Queue Implementation with Limited Size

We'll start with a simple queue implementation using a Python list with a fixed size of 8, initialized with `None` values. We'll use front and rear indices to track the queue.

```python
# Initialize queue with fixed size of 8, all None
MAX_SIZE = 8
queue = [None] * MAX_SIZE
front = 0
rear = -1
count = 0

def enqueue(item):
    """
    Add an item to the rear of the queue
    Returns True if successful, False if queue is full
    """
    global rear, count
    if count >= MAX_SIZE:
        print("Queue Overflow - Cannot enqueue, queue is full")
        return False
    rear = (rear + 1) % MAX_SIZE
    queue[rear] = item
    count += 1
    return True

def dequeue():
    """
    Remove and return the front item from the queue
    Returns None if queue is empty
    """
    global front, count
    if count == 0:
        print("Queue Underflow - Cannot dequeue, queue is empty")
        return None
    item = queue[front]
    queue[front] = None
    front = (front + 1) % MAX_SIZE
    count -= 1
    return item

def peek():
    """
    Return the front item without removing it
    Returns None if queue is empty
    """
    if count == 0:
        return None
    return queue[front]

def is_empty():
    """
    Check if the queue is empty
    """
    return count == 0

def size():
    """
    Return the current number of items in the queue
    """
    return count

def display_queue():
    """
    Display the current state of the queue
    """
    print(f"Queue: {queue} (size {size()}/{MAX_SIZE})")

# Test the simple queue implementation
print("Initial queue:")
display_queue()

enqueue(5)
print("After enqueue(5):")
display_queue()

enqueue(3)
enqueue(8)
print("After enqueue(3), enqueue(8):")
display_queue()

dequeued = dequeue()
print(f"Dequeued: {dequeued}")
display_queue()

enqueue(2)
enqueue(7)
enqueue(1)
print("After more enqueues:")
display_queue()
```

### Circular Queue Implementation

The simple implementation above works, but it wastes space when items are dequeued from the front. A circular queue reuses the space by wrapping around. The implementation above is already circular because we use modulo for front and rear!

The code above is actually a circular queue implementation. It efficiently uses the fixed-size array by wrapping indices around.

---

## 💪 Practice Exercises

### Exercise 1: Implement the Enqueue Function

Implement the `enqueue` function for a queue with limited size. The function should:

- Check if the queue is full (count >= MAX_SIZE)
- If full, print "Queue Overflow - Cannot enqueue" and return False
- If not full, update rear with modulo, set queue[rear] = item, increment count, and return True

```python
# Global variables
MAX_SIZE = 8
queue = [None] * MAX_SIZE
front = 0
rear = -1
count = 0

def enqueue(item):
    # Your implementation here
    pass

# Test your implementation
enqueue(1)
enqueue(2)
print(f"Queue: {queue}")  # Should show [1, 2, None, None, None, None, None, None]
print(f"Count: {count}")  # Should be 2
```

**Reveal Answer** (don't peek until you've tried!)

```python
def enqueue(item):
    global rear, count
    if count >= MAX_SIZE:
        print("Queue Overflow - Cannot enqueue")
        return False
    rear = (rear + 1) % MAX_SIZE
    queue[rear] = item
    count += 1
    return True
```

### Exercise 2: Implement the Dequeue Function

Implement the `dequeue` function. It should:

- Check if the queue is empty (count == 0)
- If empty, print "Queue Underflow - Cannot dequeue" and return None
- If not empty, get the item, set queue[front] = None, update front with modulo, decrement count, and return the item

```python
# Global variables
MAX_SIZE = 8
queue = [None] * MAX_SIZE
front = 0
rear = -1
count = 0

def dequeue():
    # Your implementation here
    pass

# Test your implementation
queue[0] = 5
queue[1] = 10
rear = 1
count = 2
dequeued = dequeue()
print(f"Dequeued: {dequeued}")  # Should be 5
print(f"Queue: {queue}")  # Should show [None, 10, None, None, None, None, None, None]
print(f"Count: {count}")  # Should be 1
```

**Reveal Answer**

```python
def dequeue():
    global front, count
    if count == 0:
        print("Queue Underflow - Cannot dequeue")
        return None
    item = queue[front]
    queue[front] = None
    front = (front + 1) % MAX_SIZE
    count -= 1
    return item
```

### Exercise 3: Complete Circular Queue Implementation

Put it all together! Create all the queue functions we've discussed. Test it with various operations including trying to enqueue onto a full queue and dequeue from an empty queue. Demonstrate the circular nature by filling, partially emptying, and refilling.

```python
# Global variables
MAX_SIZE = 4  # Small queue for testing circular behavior
queue = [None] * MAX_SIZE
front = 0
rear = -1
count = 0

# Your complete implementation here
def enqueue(item):
    pass

def dequeue():
    pass

def peek():
    pass

def is_empty():
    pass

def size():
    pass

def display_queue():
    pass

# Test your complete implementation
enqueue(1)
enqueue(2)
enqueue(3)
enqueue(4)
display_queue()

# Test overflow
enqueue(5)  # Should fail
display_queue()

# Test normal dequeues
print("Dequeue:", dequeue())
print("Dequeue:", dequeue())
display_queue()

# Test circular enqueue (should reuse space)
enqueue(6)
enqueue(7)
display_queue()

# Test underflow
print("Dequeue:", dequeue())
print("Dequeue:", dequeue())
print("Dequeue:", dequeue())
print("Dequeue:", dequeue())  # Should fail
display_queue()
```

**Reveal Complete Answer**

```python
def enqueue(item):
    global rear, count
    if count >= MAX_SIZE:
        print("Queue Overflow - Cannot enqueue")
        return False
    rear = (rear + 1) % MAX_SIZE
    queue[rear] = item
    count += 1
    return True

def dequeue():
    global front, count
    if count == 0:
        print("Queue Underflow - Cannot dequeue")
        return None
    item = queue[front]
    queue[front] = None
    front = (front + 1) % MAX_SIZE
    count -= 1
    return item

def peek():
    if count == 0:
        return None
    return queue[front]

def is_empty():
    return count == 0

def size():
    return count

def display_queue():
    print(f"Queue: {queue} (size {size()}/{MAX_SIZE})")
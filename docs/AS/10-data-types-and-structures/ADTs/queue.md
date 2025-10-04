# 🔄 Queue: First In, First Out (FIFO)

Picture waiting in line at a coffee shop ☕ – the first person in line gets served first. That's the essence of a **queue**! It's a crucial Abstract Data Type (ADT) in programming for handling data in sequential order, like managing tasks or messages.

---

## 🧠 What is a Queue?

A **queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle. Elements are added at the **rear** (end) and removed from the **front** (beginning).

**Key Features:**

- **FIFO Order**: The first element added is the first one removed.
- **Ordered Access**: Elements maintain their insertion order.
- **Dynamic Size**: Can expand or contract as items are enqueued or dequeued.

> Analogy: Like a line of people waiting for a bus 🚌 – no cutting in line, and the front person boards first.

---

## ⚙️ Operations on a Queue

Queues support essential operations to add, edit, and delete data:

- **Enqueue**: Add an element to the rear of the queue.
- **Dequeue**: Remove and return the front element.
- **Peek (or Front)**: View the front element without removing it.
- **Is Empty**: Check if the queue has no elements.
- **Size**: Get the number of elements in the queue.

---

## 💡 When to Use a Queue?

Queues are perfect for **sequential processing** where order of arrival matters:

**Common Use Cases:**

- **Print Queues**: In printers, jobs are processed in the order they arrive.
- **Task Scheduling**: Operating systems use queues for CPU time allocation.
- **Message Buffering**: In networking, handle incoming data packets.

**Justification:** Choose queues for scenarios needing fair treatment of requests, preventing later arrivals from overtaking earlier ones.

---

## 🔧 Implementing a Queue with Arrays

A queue can be implemented using an **array** with two pointers: **front** (points to first element) and **rear** (points to last element).

**How it Works:**

- Initialize front = -1, rear = -1 (empty).
- **Enqueue**: Add at array[rear+1], increment rear.
- **Dequeue**: Return array[front], increment front.
- **Full/Empty Check**: Rear == array size -1 (full) or front > rear (empty).

**Benefits:**

- Efficient O(1) time for enqueue/dequeue.
- Simple memory management in contiguous space.

**Limitations:**

- Fixed arrays lead to overflow; circular queues (wrapping around) or dynamic arrays solve inefficiency in linear implementation.
## 🔄 Circular Queue Tables

To avoid wasting space in fixed arrays after dequeues, a **circular queue** treats the array as a circle: rear (ep) and front (fp) pointers wrap around using modulo (% size).

#### Step 1: Initial
| fp | - | ep | - | - |
| --- | --- | --- | --- | --- |
| 4 | 2 | 3 | - | - |

#### Step 2: Enqueue 5
| fp | - | - | ep | - |
| --- | --- | --- | --- | --- |
| 4 | 2 | 3 | 5 | - |

#### Step 3: Dequeue
| - | fp | - | ep | - |
| --- | --- | --- | --- | --- |
| (unused) | 2 | 3 | 5 | - |

#### Step 4: Enqueue 6
| - | fp | - | - | ep |
| --- | --- | --- | --- | --- |
| (unused) | 2 | 3 | 5 | 6 |

#### Step 5: Enqueue 7 (ep wrap)
| ep | fp | - | - | - |
| --- | --- | --- | --- | --- |
| 7 | 2 | 3 | 5 | 6 |

#### Step 6: Dequeue
| ep | - | fp | - | - |
| --- | --- | --- | --- | --- |
| 7 | (unused) | 3 | 5 | 6 |

**Note:** After Step 5, queue full (next enqueue (0+1)%5=1 == fp=1). Step 6 frees space. This visual shows pointer movements and data changes clearly.
## ✅ Summary

- **Queue = FIFO Structure** for ordered, sequential data processing.
- **Operations**: Enqueue (add rear), Dequeue (remove front), Peek (view front).
- **Uses**: Scheduling, BFS, buffering – ideal for "first come, first served" tasks.
- **Array Implementation**: Use front/rear pointers for quick access.

Mastering queues will help you handle real-world scenarios like traffic management or online ordering systems. Stay in line with your learning! 🚀
# 🔄 Stack: Last In, First Out (LIFO)

Imagine stacking plates in a cafeteria 🥞 – you add a new plate to the top and remove from the top. That's exactly how a **stack** works! It's a fundamental Abstract Data Type (ADT) used in programming to manage data in a specific order.

---

## 🧠 What is a Stack?

A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle. Elements are added and removed only from one end called the **top** of the stack.

**Key Features:**

- **LIFO Order**: The last element added is the first one removed.
- **Limited Access**: Only the top element is accessible at any time.
- **Dynamic Size**: Can grow or shrink as elements are added or removed.

> Analogy: Like a stack of books 📚 – you can only add or take from the top without disturbing the others below.

---

## ⚙️ Operations on a Stack

Stacks support basic operations to add, edit, and delete data:

- **Push**: Add an element to the top of the stack.
- **Pop**: Remove and return the top element.
- **Peek (or Top)**: View the top element without removing it.
- **Is Empty**: Check if the stack has no elements.
- **Size**: Get the number of elements in the stack.

---

## 🚫 Stack Overflow

**Fixed Array Size: 5 (Max capacity: 5 elements, indices 0-4)**

### Initial Empty Stack
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | -     | -1  |
| 1           | -     |     |
| 2           | -     |     |
| 3           | -     |     |
| 4           | -     |     |

### After Push(10)
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | 10    | 0   |
| 1           | -     |     |
| 2           | -     |     |
| 3           | -     |     |
| 4           | -     |     |

### After Push(20)
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | 10    | 1   |
| 1           | 20    |     |
| 2           | -     |     |
| 3           | -     |     |
| 4           | -     |     |

### After Push(30)
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | 10    | 2   |
| 1           | 20    |     |
| 2           | 30    |     |
| 3           | -     |     |
| 4           | -     |     |

### Full Stack After Push(40) and Push(50)
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | 10    | 4   |
| 1           | 20    |     |
| 2           | 30    |     |
| 3           | 40    |     |
| 4           | 50    |     |

**Attempt Push(60) when Full:** Stack Overflow! Cannot add more elements (top == 4).

### After Pop() (removes 50)
| Array Index | Value | Top |
|-------------|-------|-----|
| 0           | 10    | 3   |
| 1           | 20    |     |
| 2           | 30    |     |
| 3           | 40    |     |
| 4           | 50    |     |

**Note:** The stack uses a fixed array of size 5. It grows from bottom (index 0) to top (up to index 4). Push increments top and adds at array[top]. Pop returns array[top] and decrements top. When top == max_size - 1, it's full; when top == -1, it's empty. Values remain in array but are no longer part of the stack after pop.

## 💡 When to Use a Stack?

Stacks are ideal for situations requiring **reversible actions** or **nested processing**:

**Common Use Cases:**

- **Undo/Redo Functionality**: In text editors or games – push states and pop to undo.
- **Function Call Management**: In programming, stacks track function calls and returns.
- **Expression Evaluation**: Parsing mathematical expressions (e.g., balancing parentheses).
- **Browser History**: Back button navigation – pop previous pages.

**Justification:** Use stacks when order matters and you need to reverse recent actions efficiently, avoiding the need to search through all data.

---

## ✅ Summary

- **Stack = LIFO Structure** for ordered, reversible data handling.
- **Operations**: Push (add), Pop (delete), Peek (view top).
- **Uses**: Undo features, recursion, parsing – perfect for "last action first" scenarios.
- **Array Implementation**: Track top index for efficient access.

Understanding stacks helps you solve problems like managing history or processing nested data. Keep stacking up your knowledge! 🚀
# Stack Data Structure

## 1. What is a Stack?

A **Stack** is a linear data structure that follows the **LIFO (Last In First Out)** principle.

> **LIFO Principle:** The element that is inserted last is the first one to be removed.

---

## 2. Basic Operations

A Stack supports the following fundamental operations:

*   **push(value):** Adds an element to the top of the stack.
*   **pop():** Removes and returns the top element from the stack.
*   **peek():** Returns the top element without removing it.
*   **isEmpty():** Checks whether the stack is empty.
*   **size():** Returns the number of elements present in the stack.

---

## 3. Step-by-Step Example

### Pushing Elements
*   **push(10)**  -> Stack: [10]
*   **push(20)**  -> Stack: [10, 20]
*   **push(30)**  -> Stack: [10, 20, 30]

### Performing Operations
*   **pop()**  -> Removes 30. Remaining elements: [10, 20]
*   **peek()** -> Returns 20. Remaining elements: [10, 20]

---

## 4. Simple Python Implementation (Using Lists)

```python
stack = []

# Push elements
stack.append(10)
stack.append(20)
stack.append(30)

print(stack)  # Output: [10, 20, 30]

# Peek element
print("Top element =", stack[-1])  # Output: 30

# Pop element
removed = stack.pop()
print(removed)  # Output: 30

print("stack after pop =", stack)  # Output: [10, 20]
```

---

## 5. Structured Function-Based Implementation

```python
stack = []

def push(value):
    stack.append(value)
    print(value, "pushed")

def pop():
    if len(stack) == 0:
        print("stack underflow")
    else:
        value = stack.pop()
        print(value, "popped")

def peek():
    if len(stack) == 0:
        print("stack is empty")
    else:
        print("Top element =", stack[-1])

def display():
    if len(stack) == 0:
        print("stack is empty")
    else:
        print("stack =", stack)

# Testing the Stack operations
push(10)
push(20)
push(30)

display()
peek()
pop()
display()
```

### Program Output

```text
10 pushed
20 pushed
30 pushed
stack = [10, 20, 30]
Top element = 30
30 popped
stack = [10, 20]
```

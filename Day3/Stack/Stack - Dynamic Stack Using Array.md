# Day 2 — Stack — Dynamic Stack Using Array

## 1. What is a Stack?

A **Stack** is a linear data structure that follows the:

```text
LIFO
Last In → First Out
```

This means the element inserted last will be removed first.

### Real-Life Example

Think about a stack of plates:

```text
        30  ← Top
        20
        10
```

If we remove a plate, we remove `30` first.

So:

```text
Last plate inserted
        ↓
First plate removed
```

---

# 2. Basic Stack Operations

A Stack mainly provides the following operations:

| Operation   | Description                                 |
| ----------- | ------------------------------------------- |
| `push()`    | Adds an element to the stack                |
| `pop()`     | Removes the top element                     |
| `peek()`    | Returns the top element without removing it |
| `isEmpty()` | Checks whether the stack is empty           |
| `size()`    | Returns the number of elements              |

---

# 3. Push Operation

The `push()` operation adds an element to the top of the stack.

Example:

```text
push(10)

10
```

Then:

```text
push(20)

20 ← Top
10
```

Then:

```text
push(30)

30 ← Top
20
10
```

---

# 4. Pop Operation

The `pop()` operation removes the element from the top.

Before:

```text
30 ← Top
20
10
```

After:

```text
20 ← Top
10
```

The removed element is:

```text
30
```

---

# 5. Peek Operation

The `peek()` operation returns the top element without removing it.

Stack:

```text
30 ← Top
20
10
```

```python
peek()
```

Output:

```text
30
```

The stack remains:

```text
30 ← Top
20
10
```

---

# 6. What is a Static Stack?

A static stack uses an array with a fixed capacity.

For example:

```python
stack = [0] * 5
```

Capacity:

```text
5
```

The stack can store only 5 elements.

Example:

```text
[10, 20, 30, 40, 50]
```

If we try:

```python
push(60)
```

there is no free position.

This results in a **stack overflow** if the implementation does not provide a way to increase the capacity.

---

# 7. What is a Dynamic Stack?

A **dynamic stack** can increase its capacity when the existing storage becomes full.

Instead of stopping when the stack is full, we:

1. Detect that the stack is full.
2. Create a larger array.
3. Copy the existing elements.
4. Replace the old array.
5. Insert the new element.

In our implementation, the capacity is **doubled**.

Example:

```text
Initial capacity = 5

After expansion:

5 × 2 = 10
```

---

# 8. Dynamic Stack Example

Initially:

```text
Capacity = 5

[10, 20, 30, 40, 50]
```

The stack is full.

Now we execute:

```python
push(65)
```

The stack detects:

```text
top == capacity
```

So it calls:

```python
expand()
```

A new array is created:

```text
Capacity = 10

[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

The old elements are copied:

```text
[10, 20, 30, 40, 50, 0, 0, 0, 0, 0]
```

Then `65` is inserted:

```text
[10, 20, 30, 40, 50, 65, 0, 0, 0, 0]
```

---

# 9. Understanding `top`

In this implementation:

```python
self.top = 0
```

`top` represents the **next available position** for inserting an element.

Initially:

```text
top = 0
```

After:

```python
push(10)
```

```text
top = 1
```

After:

```python
push(20)
```

```text
top = 2
```

After:

```python
push(30)
```

```text
top = 3
```

Example:

```text
Index:   0    1    2    3    4
        -------------------------
Stack:  10   20   30    0    0
                     ↑
                    top
```

So:

```text
top = 3
```

means there are currently 3 elements.

---

# 10. Why `top == capacity`?

Suppose:

```text
capacity = 5
```

After inserting five elements:

```text
top = 5
```

The valid indexes are:

```text
0  1  2  3  4
```

There is no index `5` available.

Therefore:

```python
if self.top == self.capacity:
    self.expand()
```

checks whether the stack is full before inserting a new element.

---

# 11. Expand Operation

The `expand()` operation increases the stack capacity.

### Step 1 — Get Current Size

```python
length = self.size()
```

For example:

```text
length = 5
```

### Step 2 — Create a New Array

```python
newStack = [0] * (self.capacity * 2)
```

If:

```text
capacity = 5
```

then:

```text
new capacity = 10
```

### Step 3 — Copy Existing Elements

```python
for i in range(length):
    newStack[i] = self.stack[i]
```

### Step 4 — Replace Old Stack

```python
self.stack = newStack
```

### Step 5 — Update Capacity

```python
self.capacity *= 2
```

---

# 12. Dynamic Stack Algorithm

## Push Algorithm

```text
push(element)

1. Check whether stack is full.
2. If stack is full:
       expand the stack.
3. Insert element at top.
4. Increment top.
```

---

## Pop Algorithm

```text
pop()

1. Check whether stack is empty.
2. If empty:
       display "Stack is empty".
3. Otherwise:
       decrement top.
4. Get element from stack[top].
5. Return element.
```

---

## Peek Algorithm

```text
peek()

1. Check whether stack is empty.
2. If empty:
       display "Stack is empty".
3. Otherwise:
       return stack[top - 1].
```

---

# 13. Python Implementation — Dynamic Stack

```python
class StackDP:

    def __init__(self):

        # Initial capacity
        self.capacity = 5

        # Create stack with initial capacity
        self.stack = [0] * self.capacity

        # top represents the next available position
        self.top = 0


    def push(self, no):

        # Check whether stack is full
        if self.top == self.capacity:
            self.expand()

        # Insert element at top position
        self.stack[self.top] = no

        # Move top to next position
        self.top += 1


    def expand(self):

        # Get current number of elements
        length = self.size()

        # Create new array with double capacity
        newStack = [0] * (self.capacity * 2)

        # Copy old elements
        for i in range(length):
            newStack[i] = self.stack[i]

        # Replace old stack with new stack
        self.stack = newStack

        # Double the capacity
        self.capacity *= 2


    def size(self):

        return self.top


    def display(self):

        for i in range(self.top):
            print(self.stack[i], end=" ")


    def pop(self):

        # Check whether stack is empty
        if self.isEmpty():
            print("Stack is empty")
            return -1

        # Move top one position backward
        self.top -= 1

        # Get the top element
        data = self.stack[self.top]

        return data


    def isEmpty(self):

        return self.top == 0


    def peek(self):

        # Check whether stack is empty
        if self.isEmpty():
            print("Stack is empty")
            return -1

        # Top element is at top - 1
        return self.stack[self.top - 1]
```

---

# 14. Creating the Stack

```python
s = StackDP()
```

Initially:

```text
capacity = 5
top = 0
```

Stack:

```text
[0, 0, 0, 0, 0]
```

---

# 15. Push Elements

```python
s.push(10)
s.push(20)
s.push(30)
s.push(40)
s.push(50)
```

Stack:

```text
[10, 20, 30, 40, 50]
```

Now:

```text
size = 5
capacity = 5
top = 5
```

The stack is full.

---

# 16. Dynamic Expansion

Now execute:

```python
s.push(65)
```

Before inserting `65`:

```python
if self.top == self.capacity:
    self.expand()
```

Condition:

```text
5 == 5
```

So:

```python
self.expand()
```

is executed.

Capacity changes:

```text
5 → 10
```

Stack becomes:

```text
[10, 20, 30, 40, 50, 0, 0, 0, 0, 0]
```

Then `65` is inserted:

```text
[10, 20, 30, 40, 50, 65, 0, 0, 0, 0]
```

---

# 17. Complete Program

```python
class StackDP:

    def __init__(self):
        self.capacity = 5
        self.stack = [0] * self.capacity
        self.top = 0


    def push(self, no):

        if self.top == self.capacity:
            self.expand()

        self.stack[self.top] = no
        self.top += 1


    def expand(self):

        length = self.size()

        # Create new array with double capacity
        newStack = [0] * (self.capacity * 2)

        # Copy existing elements
        for i in range(length):
            newStack[i] = self.stack[i]

        # Replace old stack
        self.stack = newStack

        # Update capacity
        self.capacity *= 2


    def size(self):
        return self.top


    def display(self):

        for i in range(self.top):
            print(self.stack[i], end=" ")


    def pop(self):

        if self.isEmpty():
            print("Stack is empty")
            return -1

        self.top -= 1

        data = self.stack[self.top]

        return data


    def isEmpty(self):
        return self.top == 0


    def peek(self):

        if self.isEmpty():
            print("Stack is empty")
            return -1

        return self.stack[self.top - 1]


# Create stack
s = StackDP()

# Push elements
s.push(10)
s.push(20)
s.push(30)
s.push(40)
s.push(50)

print("Size =", s.size())

s.display()

# Stack is full.
# This push automatically expands the stack.
s.push(65)

print("\nSize =", s.size())

s.display()

# Pop
print("\n\nPopped element =", s.pop())

# Peek
print("\nPeek element =", s.peek())

# Display stack
print("\nStack:")
s.display()
```

---

# 18. Expected Output

```text
Size = 5
10 20 30 40 50

Size = 6
10 20 30 40 50 65

Popped element = 65

Peek element = 50

Stack:
10 20 30 40 50
```

---

# 19. Dry Run

### Initially

```text
capacity = 5
top = 0

[]
```

### Push 10

```text
[10]
top = 1
```

### Push 20

```text
[10, 20]
top = 2
```

### Push 30

```text
[10, 20, 30]
top = 3
```

### Push 40

```text
[10, 20, 30, 40]
top = 4
```

### Push 50

```text
[10, 20, 30, 40, 50]
top = 5
```

Stack is full.

### Push 65

```text
top == capacity
5 == 5
```

Therefore:

```text
expand()
```

Capacity:

```text
5 → 10
```

After copying:

```text
[10, 20, 30, 40, 50, 0, 0, 0, 0, 0]
```

Insert `65`:

```text
[10, 20, 30, 40, 50, 65, 0, 0, 0, 0]
```

Now:

```text
top = 6
capacity = 10
```

---

# 20. Stack After Pop

Before pop:

```text
[10, 20, 30, 40, 50, 65]
                         ↑
                        top
```

`65` is the top element.

After:

```python
s.pop()
```

`top` is decreased:

```text
top = 5
```

Returned element:

```text
65
```

Logical stack:

```text
[10, 20, 30, 40, 50]
```

---

# 21. Stack After Peek

Current stack:

```text
10  20  30  40  50
                    ↑
                   Top
```

```python
s.peek()
```

returns:

```text
50
```

But it does **not remove** `50`.

The stack remains:

```text
10  20  30  40  50
```

---

# 22. Important Concepts

### Stack follows LIFO

```text
Last In → First Out
```

### Push

```text
Add element
```

### Pop

```text
Remove top element
```

### Peek

```text
Read top element without removing it
```

### Dynamic Stack

```text
Stack Full
    ↓
Double Capacity
    ↓
Create New Array
    ↓
Copy Existing Elements
    ↓
Replace Old Array
    ↓
Insert New Element
```

---

# 23. Key Points for Interview

* A Stack follows **LIFO**.
* `push()` adds an element.
* `pop()` removes the top element.
* `peek()` returns the top element without removing it.
* `top` keeps track of the next available position in this implementation.
* `top == capacity` means the array-based stack is full.
* A dynamic stack can increase its capacity when it becomes full.
* In this implementation, capacity is doubled.
* `minIndex` is not related to Stack; for Selection Sort, use `minIndex` to track the smallest element found so far.

---

# 24. Quick Revision

```text
                STACK
                  |
          -----------------
          |       |       |
        Push     Pop     Peek
          |       |       |
         Add    Remove    Read
          |
        Top
```

### Dynamic Array Stack

```text
Initial Capacity
       ↓
    Push Data
       ↓
Stack Full?
   /       \
 No        Yes
 |          |
Push      Expand
            ↓
      Double Capacity
            ↓
      Copy Elements
            ↓
        Push Data
```

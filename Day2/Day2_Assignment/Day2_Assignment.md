# Day 2 — DSA Interview Assignment

## Instructions

* Solve each problem using Python.
* First write the **Logic / Algorithm**.
* Then write the **Code**.
* Mention **Time Complexity** and **Space Complexity**.
* Do not use built-in shortcuts such as `sort()`, `max()`, `min()`, `reverse()`, etc., unless specifically allowed.
* Focus on understanding the approach, not just getting the output.

---

# Part A — Arrays

## 1. Find Maximum and Minimum

Given an array of integers, find both the maximum and minimum element.

**Example:**

```text
Input:  [20, 5, 40, 10, 80, 15]
Output: Maximum = 80, Minimum = 5
```

**Requirement:** Solve in one traversal.

```python
Algorithm:

1. Take the first element as the maximum.
2. Take the first element as the minimum.
3. Traverse the array from beginning to end.
4. Compare each element with the current maximum.
5. If the element is greater, update maximum.
6. Compare each element with the current minimum.
7. If the element is smaller, update minimum.
8. Continue until the end of the array.
9. Print maximum and minimum.
```

```python
For every element:
    Check whether it is greater than maximum
        If yes → update maximum

    Check whether it is smaller than minimum
        If yes → update minimum
```

```python
arr = [20, 5, 40, 10, 80, 15]

max_num = arr[0]
min_num = arr[0]

for i in range(len(arr)):
    if arr[i] > max_num:
        max_num = arr[i]

    if arr[i] < min_num:
        min_num = arr[i]

print("Max ele of Array", max_num)
print("Min ele of Array", min_num)
```

---

## 2. Find the Second Largest Element

Find the **second largest distinct element** without sorting.

**Example:**

```text
Input:  [10, 5, 20, 8, 20, 15]
Output: 15
```

**Follow-up:** What if there is no second-largest distinct element?

---

## 3. Move All Zeros to the End

Move all zeros to the end while maintaining the relative order of non-zero elements.

**Example:**

```text
Input:  [0, 1, 0, 3, 12]
Output: [1, 3, 12, 0, 0]
```

**Requirement:** Do it in-place without creating another array.

---

## 4. Remove Duplicates from Sorted Array

Given a sorted array, remove duplicate elements in-place and return the number of unique elements.

**Example:**

```text
Input:  [1, 1, 2, 2, 3, 4, 4]
Output: 4

Array: [1, 2, 3, 4, ...]
```

**Interview Concept:** Two Pointers.

---

## 5. Reverse an Array In-Place

Reverse an array without using another array.

**Example:**

```text
Input:  [10, 20, 30, 40, 50]
Output: [50, 40, 30, 20, 10]
```

**Requirement:** Use the two-pointer approach.

---

# Part B — Searching

## 6. Linear Search

Given an array and a target value, return the index of the first occurrence.

**Example:**

```text
Input:  [10, 20, 30, 40, 50], target = 30
Output: 2
```

If not found, return `-1`.

---

## 7. Binary Search

Given a sorted array, find the index of the target using Binary Search.

**Example:**

```text
Input:  [10, 20, 30, 40, 50, 60], target = 40
Output: 3
```

**Requirement:** Do not use `in` or `index()`.

**Follow-up:** Why does Binary Search require a sorted array?

---

# Part C — Important Array Interview Problems

## 8. Two Sum

Given an array and a target, find two elements whose sum equals the target.

**Example:**

```text
Input:  nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
```

**Tasks:**

1. Solve using brute force `O(n²)`.
2. Solve using a dictionary in `O(n)`.

---

## 9. Best Time to Buy and Sell Stock

Given daily stock prices, find the maximum profit by buying on one day and selling on a later day.

**Example:**

```text
Input:  [7, 1, 5, 3, 6, 4]
Output: 5
```

**Requirement:** Solve in `O(n)` time.

---

## 10. Maximum Subarray

Find the contiguous subarray having the maximum sum.

**Example:**

```text
Input:  [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
```

Because:

```text
[4, -1, 2, 1] → Sum = 6
```

**Interview Concept:** Kadane's Algorithm.

---

# Part D — Stack

## 11. Implement Stack

Implement a Stack with:

```text
push()
pop()
peek()
is_empty()
```

**Example:**

```text
push(10)
push(20)
push(30)

peek() → 30
pop()  → 30
peek() → 20
```

---

## 12. Valid Parentheses

Given a string containing `()`, `{}`, and `[]`, determine whether the brackets are balanced.

**Example:**

```text
Input:  "{[()]}"
Output: True

Input:  "{[(])}"
Output: False
```

**Interview Concept:** Stack.

---

## 13. Min Stack

Design a Stack supporting:

```text
push()
pop()
top()
get_min()
```

`get_min()` must return the minimum element in `O(1)` time.

**Follow-up:** Implement using two stacks.

---

# Part E — Queue

## 14. Implement Queue

Implement a Queue with:

```text
enqueue()
dequeue()
front()
is_empty()
```

**Example:**

```text
enqueue(10)
enqueue(20)
enqueue(30)

dequeue() → 10
front()   → 20
```

Explain why Queue follows FIFO.

---

## 15. Implement Queue Using Two Stacks

Implement a Queue using two Stacks.

Support:

```text
enqueue()
dequeue()
```

**Example:**

```text
enqueue(10)
enqueue(20)
enqueue(30)

dequeue() → 10
dequeue() → 20
```

**Interview Concept:** Combining data structures to implement an ADT.

---

# Part F — Linked List

## 16. Create a Singly Linked List

Create a `Node` containing:

```text
data
next
```

Create:

```text
10 → 20 → 30 → 40 → NULL
```

Implement:

```text
insert_at_beginning()
insert_at_end()
display()
```

---

## 17. Reverse a Linked List

Reverse:

```text
10 → 20 → 30 → 40 → NULL
```

into:

```text
40 → 30 → 20 → 10 → NULL
```

**Requirement:** Solve iteratively.

**Hint:** Understand `prev`, `current`, and `next`.

---

## 18. Find Middle of Linked List

Given:

```text
10 → 20 → 30 → 40 → 50
```

Return:

```text
30
```

**Requirement:** Use slow and fast pointers.

**Follow-up:** What happens when the list has an even number of nodes?

---

## 19. Detect Cycle in Linked List

Determine whether a linked list contains a cycle.

**Example:**

```text
10 → 20 → 30 → 40
          ↑     ↓
          ← ← ←
```

Output:

```text
True
```

**Interview Concept:** Floyd's Cycle Detection Algorithm.

---

# Part G — Choose the Data Structure

## 20. Select the Appropriate Data Structure

Choose the most appropriate data structure and explain why.

1. Browser Back button → ?
2. People waiting at a bank counter → ?
3. Company organizational hierarchy → ?
4. Google Maps city connections → ?
5. Fast index-based access → ?
6. `employee_id → employee_name` → ?

Possible structures:

```text
Array
Stack
Queue
Linked List
Tree
Graph
Hash Map / Dictionary
```

---

# Part H — Time and Space Complexity

## 21. Find Time and Space Complexity

### A

```python
for i in range(n):
    print(i)
```

### B

```python
for i in range(n):
    for j in range(n):
        print(i, j)
```

### C

```python
i = 1

while i < n:
    print(i)
    i = i * 2
```

### D

```python
for i in range(n):
    for j in range(i):
        print(i, j)
```

### E

```python
arr = [1, 2, 3, 4, 5]

for i in arr:
    print(i)

for i in arr:
    print(i)
```

For each, identify:

```text
Time Complexity = ?
Space Complexity = ?
```

---

# Part I — Conceptual Interview Questions

## 22. Array vs Linked List

Compare Array and Linked List for:

```text
Access by index
Search
Insert at beginning
Delete from beginning
Memory usage
```

Explain why their complexities are different.

---

## 23. Stack vs Queue

Explain the difference between Stack and Queue.

Identify which one is appropriate for:

1. Browser Back
2. Printer Jobs
3. Undo Operation
4. BFS Traversal
5. Function Call Management

---

# Part J — FAANG-Style Challenges

## 24. Product of Array Except Self

For every element, return the product of all other elements.

**Example:**

```text
Input:  [1, 2, 3, 4]
Output: [24, 12, 8, 6]
```

**Requirements:**

* Do not use division.
* Solve in `O(n)`.
* Try to achieve `O(1)` extra space excluding the output array.

---

## 25. Trapping Rain Water

Given an array representing elevation heights, calculate how much rainwater can be trapped.

**Example:**

```text
Input:
[0,1,0,2,1,0,1,3,2,1,2,1]

Output:
6
```

**Tasks:**

1. First solve using brute force.
2. Optimize using the two-pointer approach.
3. Compare both approaches.

---

# Interview Problem-Solving Format

For **every coding problem**, follow this format:

```text
1. Understand the Problem
        ↓
2. Identify Input and Output
        ↓
3. Think of Brute Force
        ↓
4. Optimize the Approach
        ↓
5. Write Logic / Algorithm
        ↓
6. Write Code
        ↓
7. Dry Run with Example
        ↓
8. Check Edge Cases
        ↓
9. Time Complexity
        ↓
10. Space Complexity
```

# Priority Problems

## Must Solve

```text
1. Find Maximum and Minimum
2. Second Largest
3. Move Zeros
4. Remove Duplicates
5. Reverse Array
6. Binary Search
7. Two Sum
8. Best Time to Buy and Sell Stock
9. Maximum Subarray
10. Valid Parentheses
11. Reverse Linked List
12. Middle of Linked List
13. Detect Cycle
14. Product of Array Except Self
```

## Challenge

```text
15. Min Stack
16. Queue Using Two Stacks
17. Trapping Rain Water
```

# Submission Requirements

For each problem submit:

```text
Problem Statement
↓
Logic / Algorithm
↓
Python Code
↓
Example Dry Run
↓
Time Complexity
↓
Space Complexity
↓
Edge Cases
```

**Goal:** Do not memorize solutions. Learn to identify the **pattern**, choose the correct **data structure**, optimize the **algorithm**, and explain the **complexity** clearly.

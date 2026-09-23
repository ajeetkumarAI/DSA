# DSA — Array Theory Notes

## 1. What is an Array?

An **Array** is a linear data structure used to store a collection of elements of the **same data type** in **contiguous memory locations**.

Example:

```text
Index:    0    1    2    3    4
          ↓    ↓    ↓    ↓    ↓
Value:   12   24   36   48   60
```

The elements are stored next to each other in memory.

```text
Memory:

1000 → 12
1004 → 24
1008 → 36
1012 → 48
1016 → 60
```

Because the elements are stored contiguously, the address of an element can be calculated using its index.

---

## 2. Why is Array Important in DSA?

Array is one of the most fundamental data structures in DSA.

Many other data structures and algorithms are built around the concept of arrays.

Arrays are commonly used for:

- Storing multiple values
- Searching
- Sorting
- Traversing
- Updating elements
- Finding maximum and minimum values
- Frequency counting
- Two-pointer problems
- Sliding-window problems
- Prefix-sum problems
- Matrix problems
- Dynamic programming

A large number of coding-interview problems are based on arrays.

---

## 3. Characteristics of an Array

### 3.1 Homogeneous

Elements in a traditional array are generally of the same data type.

```text
12, 24, 36, 48, 60
```

All elements are integers.

### 3.2 Contiguous Memory

Elements are stored next to each other in memory.

```text
[12][24][36][48][60]
```

### 3.3 Indexed

Each element has an index.

```text
Index:    0   1   2   3   4
Value:   12  24  36  48  60
```

### 3.4 Random Access

We can directly access an element using its index.

```python
arr[3]
```

Output:

```text
48
```

Accessing an element by index is generally:

```text
O(1)
```

---

## 4. What is an Index?

An **index** represents the position of an element in an array.

In most programming languages, indexing starts from `0`.

```text
Array:    [12, 24, 36, 48, 60]

Index:      0   1   2   3   4
```

Therefore:

```python
arr[0]  # 12
arr[1]  # 24
arr[2]  # 36
arr[3]  # 48
arr[4]  # 60
```

---

## 5. Why is Array Access O(1)?

Suppose we have:

```text
[12][24][36][48][60]
```

and want the element at index `3`.

The computer can calculate the location of index `3` using the starting address, index, and size of each element.

Conceptually:

```text
Address of arr[i]

= Base Address + (i × Size of each element)
```

Therefore, accessing an element by index takes constant time.

```text
Access by index → O(1)
```

---

# 6. Python List vs Array

Python provides a built-in `list`, while NumPy provides an array structure.

## Python List

A Python list is a general-purpose, dynamic sequence.

```python
li = [12, 24, 36, 48, 60]
```

A Python list can contain different types of objects:

```python
li = [10, 20.5, "Hello", True]
```

Python lists are implemented using a dynamic array-like structure.

A Python list is **not a linked list**.

## Array

A traditional array stores elements of the same type in contiguous memory.

Example using NumPy:

```python
import numpy as np

arr = np.array([12, 24, 36, 48, 60])
```

Accessing an element:

```python
print(arr[3])
```

Output:

```text
48
```

---

## 7. Python List vs Array Comparison

| Feature | Python List | Array |
|---|---|---|
| Data type | Can contain different types | Usually same type |
| Size | Dynamic | Typically fixed-size |
| Memory layout | Array-like storage | Contiguous elements |
| Indexing | Yes | Yes |
| Index access | O(1) | O(1) |
| Insert in middle | O(n) | O(n) |
| Delete from middle | O(n) | O(n) |
| Linear search | O(n) | O(n) |
| Binary search | O(log n) if sorted | O(log n) if sorted |
| Random access | Fast | Fast |
| Main advantage | Flexible and convenient | Efficient typed storage |

---

# 8. Searching in an Array

Searching means finding whether a particular value exists in the array and, if required, finding its position.

Consider:

```text
[12, 24, 36, 48, 60]
```

## Linear Search

In linear search, elements are checked one by one.

To find `60`:

```text
12 → 24 → 36 → 48 → 60
```

Worst-case time complexity:

```text
O(n)
```

### Important

**Searching is not O(1).**

Accessing an element using its index is O(1), but searching for an unknown value is generally O(n).

---

## Binary Search

If the array is sorted, we can use binary search.

Example:

```text
[12, 24, 36, 48, 60, 72, 84]
```

Binary search repeatedly divides the search space into half.

Time complexity:

```text
O(log n)
```

Binary search requires sorted data.

---

# 9. Access vs Search

This distinction is very important in DSA.

### Access

If we know the index:

```python
arr[3]
```

Complexity:

```text
O(1)
```

### Search

If we only know the value:

```text
Find 48
```

We may need to check multiple elements.

Linear search complexity:

```text
O(n)
```

Therefore:

```text
Access by index     → O(1)
Linear Search       → O(n)
Binary Search       → O(log n), sorted data
```

---

# 10. Insertion and Deletion

Consider:

```text
[10, 20, 30, 40, 50]
```

Suppose we insert `25` at index `2`.

Before:

```text
[10, 20, 30, 40, 50]
```

After:

```text
[10, 20, 25, 30, 40, 50]
```

The elements after index `2` need to be shifted.

Therefore:

```text
Insertion in middle → O(n)
```

Similarly, deleting an element from the middle requires shifting elements.

```text
Deletion from middle → O(n)
```

The exact complexity of insertion/deletion at the end depends on the array implementation.

---

# 11. Random Access

One of the biggest advantages of an array is **random access**.

Suppose:

```python
arr = [10, 20, 30, 40, 50]
```

We want:

```python
arr[4]
```

The computer can directly calculate the location of index `4`.

Therefore:

```text
arr[4] → O(1)
```

This is called **Random Access**.

---

# 12. Static Array and Dynamic Array

## Static Array

A static array has a fixed size.

Conceptually:

```text
Size = 5

[10][20][30][40][50]
```

The size cannot normally be changed directly.

If more space is required, a new larger array may need to be created and the elements copied.

## Dynamic Array

A dynamic array can grow when more elements are added.

Python's `list` behaves like a dynamic array.

Example:

```python
li = []

li.append(10)
li.append(20)
li.append(30)
```

Python manages the underlying storage automatically.

---

# 13. Array Operations and Complexity

For a typical array:

| Operation | Complexity |
|---|---:|
| Access by index | O(1) |
| Update by index | O(1) |
| Linear search | O(n) |
| Binary search | O(log n) |
| Insert at beginning | O(n) |
| Insert in middle | O(n) |
| Delete from beginning | O(n) |
| Delete from middle | O(n) |
| Traverse | O(n) |

For insertion and deletion at the end, the exact complexity depends on whether the array is fixed-size, dynamic, or on the particular implementation.

---

# 14. Array in Python

Python's main built-in sequence type is `list`.

For DSA learning, arrays can also be represented using libraries such as NumPy.

### Python List

```python
arr = [10, 20, 30, 40, 50]
```

### NumPy Array

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])
```

NumPy arrays are particularly useful for numerical and scientific computing.

---

# 15. Python List vs NumPy Array

Consider:

```python
li = [12, 24, 36, 48, 60]

arr = np.array([12, 24, 36, 48, 60])
```

## Python List

Python lists are general-purpose collections.

They can contain different types:

```python
li = [10, "Hello", 20.5, True]
```

## NumPy Array

NumPy arrays are designed mainly for numerical and scientific computing.

```python
arr = np.array([10, 20, 30, 40])
```

Elements are stored using a NumPy data type.

NumPy also supports vectorized mathematical operations.

Example:

```python
arr = np.array([10, 20, 30])

print(arr * 2)
```

Output:

```text
[20 40 60]
```

With a normal Python list:

```python
li = [10, 20, 30]

print(li * 2)
```

Output:

```text
[10, 20, 30, 10, 20, 30]
```

---

# 16. Simple NumPy Array Example

```python
import numpy as np

arr = np.array([12, 24, 36, 48, 60])

# Access
print(arr[3])

# Update
arr[3] = 100

print(arr)

# Traverse
for value in arr:
    print(value)
```

Output:

```text
48

[ 12  24  36 100  60]

12
24
36
100
60
```

---

# 17. Important Concepts to Remember

```text
ARRAY
  |
  |-- Collection of elements
  |
  |-- Usually same data type
  |
  |-- Contiguous memory
  |
  |-- Index based
  |
  |-- Fast random access
  |
  |-- Access → O(1)
  |
  |-- Linear Search → O(n)
  |
  |-- Binary Search → O(log n) on sorted data
  |
  |-- Insert/Delete in middle → O(n)
  |
  |-- Traverse → O(n)
```

---

# 18. Quick Revision

### Array

A collection of elements stored in an indexed structure, traditionally with elements of the same type and contiguous memory.

### Index

The position of an element.

```text
[10, 20, 30, 40]

 0   1   2   3
```

### Random Access

Directly accessing an element using its index.

```python
arr[2]
```

Complexity:

```text
O(1)
```

### Linear Search

Checking elements one by one.

Complexity:

```text
O(n)
```

### Binary Search

Searching by repeatedly dividing a sorted search space into half.

Complexity:

```text
O(log n)
```

### Traversal

Visiting every element.

Complexity:

```text
O(n)
```

### Insertion/Deletion

Adding or removing elements from the beginning or middle may require shifting elements.

Typical complexity:

```text
O(n)
```

---

# 19. Key Difference to Remember

```text
Python List
    ↓
Dynamic, general-purpose collection
    ↓
Can store different types
    ↓
Dynamic size

Array
    ↓
Indexed data structure
    ↓
Typically same-type elements
    ↓
Contiguous memory
    ↓
Fast random access
```

**Most important DSA point:**

```text
Access by index → O(1)
Search          → O(n)
Binary Search   → O(log n) when sorted
Traversal       → O(n)
Middle Insert   → O(n)
Middle Delete   → O(n)
```

# Array Hands-On Practice Problems

## General Rule

Do not use another list/array, set, dictionary, sorting, or built-in shortcuts that defeat the purpose of the exercise.

The goal is to practice **array traversal, indexing, comparisons, and in-place operations**.

---

## 1. Find the Maximum Element

Given an integer array, find the largest element without using `max()`.

```python
arr = [12, 45, 7, 89, 34, 67]

# Output:
# 89
```

```python
arr = [12, 45, 7, 89, 34, 67]
largest_num = arr[0]
for num in arr:
  if num > largest_num:
    largest_num = num

print(largest_num)
```

```python
arr = [12, 45, 7, 89, 34, 67]
largest_num = arr[0]
for i in range(1,len(array)):
  if arr[i] > largest_num:
    largest_num = arr[i]

print(largest_num)
```
---

## 2. Find the Minimum Element

Find the smallest element without using `min()`.

```python
arr = [12, 45, 7, 89, 34, 67]

# Output:
# 7
```
```python
arr = [12, 45, 7, 89, 34, 67]
smallest_num = arr[0]
for x in arr:
  if x < smallest_num:
    smallest_num = x

print(smallest_num)
```

```python
arr = [12, 45, 7, 89, 34, 67]
smallest_num = arr[0]
for i in range(1,len(arr)):
  if arr[i] < smallest_num:
    smallest_num = arr[i]

print(smallest_num)
```

---

## 3. Find Maximum and Minimum Together

Find both the maximum and minimum values in a **single traversal**.

```python
arr = [20, 5, 40, 10, 80, 15]

# Maximum: 80
# Minimum: 5
```

```python
arr = [20, 5, 40, 10, 80, 15]
max_value = arr[0]
min_value = arr[0]
for x in arr:
  if x > max_value:
    max_value = x
  if x < min_value:
    min_value = x

print(max_value)
print(max_value)
```
```python
arr = [20, 5, 40, 10, 80, 15]
max_value = arr[0]
min_value = arr[0]
for i in range(1,len(arr)):
  if arr[i] > max_value:
    max_value = arr[i]
  if arr[i] < min_value:
    min_value = arr[i]

print(max_value)
print(max_value)
```

---

## 4. Calculate Sum of Array

Find the sum without using `sum()`.

```python
arr = [10, 20, 30, 40]

# Output:
# 100
```

---

## 5. Calculate Average

Calculate the average without using `sum()`.

```python
arr = [10, 20, 30, 40, 50]

# Output:
# 30
```

---

## 6. Count Even Numbers

Count how many elements in the array are even.

```python
arr = [10, 15, 22, 33, 40, 51]

# Output:
# 3
```

---

## 7. Count Positive, Negative and Zero Values

Count the number of positive values, negative values, and zeros.

```python
arr = [-5, 10, 0, -3, 8, 0, 7]

# Positive: 3
# Negative: 2
# Zero: 2
```

---

## 8. Linear Search

Find the index of a target value.

Return `-1` if the target does not exist.

```python
arr = [10, 30, 50, 70, 90]
target = 70

# Output:
# 3
```

---

## 9. Reverse an Array In-Place

Reverse the original array **without creating another array**.

```python
arr = [10, 20, 30, 40, 50]

# Output:
# [50, 40, 30, 20, 10]
```

### Requirement

Perform the reversal **in-place**.

Do not create a second array.

---

## 10. Check Whether an Array Is Sorted

Check whether the array is sorted in ascending order.

### Example 1

```python
arr = [10, 20, 30, 40, 50]

# Output:
# True
```

### Example 2

```python
arr = [10, 30, 20, 40]

# Output:
# False
```

---

## 11. Find the Second Largest Element

Find the **second largest distinct value** without sorting.

```python
arr = [10, 40, 20, 50, 30]

# Output:
# 40
```

### Requirement

Do not use sorting.

---

## 12. Find the Second Smallest Element

Find the **second smallest distinct value** without sorting.

```python
arr = [20, 5, 10, 40, 15]

# Output:
# 10
```

### Requirement

Do not use sorting.

---

## 13. Move All Zeros to the End In-Place

Move all zeros to the end of the array while keeping the relative order of the non-zero elements.

```python
arr = [0, 1, 0, 3, 12]

# Output:
# [1, 3, 12, 0, 0]
```

### Requirements

- Modify the original array.
- Do not create another array.
- Preserve the relative order of non-zero elements.

---

## 14. Move All Negative Numbers to the Beginning In-Place

Rearrange the array so that negative numbers appear before non-negative numbers.

The relative order does **not** need to be preserved.

```python
arr = [10, -2, 5, -7, 8, -1]

# One valid result:
# [-1, -2, -7, 5, 8, 10]
```

### Requirements

- Perform the operation in-place.
- Do not create another array.
- Any valid arrangement is acceptable as long as all negative numbers appear before non-negative numbers.

---

## 15. Remove Duplicates from a Sorted Array In-Place

Given a **sorted array**, remove duplicate values in-place.

Return the number of unique elements and place those unique elements at the beginning of the array.

```python
arr = [1, 1, 2, 2, 3, 3, 4]

# First part of array:
# [1, 2, 3, 4, ...]

# Output:
# 4
```

### Expected Result

After the operation:

```text
Unique elements = 4

First 4 positions:
[1, 2, 3, 4]
```

### Requirements

- The input array is already sorted.
- Modify the original array.
- Do not create another array.
- Do not use `set()`.
- Return the number of unique elements.

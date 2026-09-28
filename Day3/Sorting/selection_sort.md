# Day 3 — Selection Sort

## 1. What is Selection Sort?

**Selection Sort** is a simple sorting algorithm that repeatedly selects the smallest element from the unsorted part of an array and places it at the correct position.

### Basic Idea

```text
Find the smallest element
        ↓
Place it at the correct position
        ↓
Repeat for the remaining elements
```

---

## 2. Example — Sort Marks from Lowest to Highest

Suppose student marks are:

```text
45   20   35   10   50
```

### Pass 1

Find the smallest element:

```text
45   20   35   10   50
             ↑
            min
```

Smallest value:

```text
10
```

Swap `45` and `10`:

```text
10   20   35   45   50
```

### Pass 2

Now consider the remaining unsorted part:

```text
20   35   45   50
```

The smallest value is:

```text
20
```

It is already in the correct position:

```text
10   20   35   45   50
```

Continue the same process until all elements are sorted.

### Final Result

```text
10   20   35   45   50
```

---

## 3. Selection Sort Algorithm

### Steps

1. Start.
2. Set the current position `i`.
3. Find the smallest element from index `i` to `n-1`.
4. Store its index in `minIndex`.
5. Swap `A[i]` with `A[minIndex]`.
6. Increment `i`.
7. Repeat steps 3–6 until `i < n-1`.
8. Stop.

---

## 4. Selection Sort Example

Consider:

```text
64   25   12   22   11
```

### Pass 1

Find the minimum from:

```text
64   25   12   22   11
```

Minimum:

```text
11
```

Swap `64` and `11`:

```text
11   25   12   22   64
```

The first position is now sorted.

---

### Pass 2

Remaining unsorted elements:

```text
25   12   22   64
```

Minimum:

```text
12
```

Swap `25` and `12`:

```text
11   12   25   22   64
```

The first two positions are now sorted.

---

### Pass 3

Remaining unsorted elements:

```text
25   22   64
```

Minimum:

```text
22
```

Swap `25` and `22`:

```text
11   12   22   25   64
```

---

### Pass 4

Remaining elements:

```text
25   64
```

Minimum:

```text
25
```

No change is required.

### Final Result

```text
11   12   22   25   64
```

---

## 5. Selection Sort Pseudocode

```text
SelectionSort(A, n)

for i = 0 to n - 2

    minIndex = i

    for j = i + 1 to n - 1

        if A[j] < A[minIndex]

            minIndex = j

    swap A[i] and A[minIndex]

End
```

---

## 6. Important Part of Selection Sort

The most important logic is:

```text
minIndex = i
```

Then compare every remaining element with the **minimum found so far**:

```text
if A[j] < A[minIndex]
    minIndex = j
```

### Important

The comparison should be:

```python
arr[j] < arr[min_index]
```

and **not**:

```python
arr[j] < arr[i]
```

### Why?

Because `minIndex` changes whenever we find a smaller element.

For example:

```text
64   25   12   22   11
```

Initially:

```text
minIndex = 0
minimum = 64
```

Compare `25`:

```text
25 < 64
```

Update:

```text
minIndex = 1
minimum = 25
```

Compare `12`:

```text
12 < 25
```

Update:

```text
minIndex = 2
minimum = 12
```

Compare `22`:

```text
22 < 12
```

No update.

Compare `11`:

```text
11 < 12
```

Update:

```text
minIndex = 4
minimum = 11
```

Finally, swap:

```text
64 ↔ 11
```

Result:

```text
11   25   12   22   64
```

---

## 7. Python Implementation

```python
def selection_sort(arr):

    for i in range(len(arr) - 1):

        min_index = i

        for j in range(i + 1, len(arr)):

            if arr[j] < arr[min_index]:
                min_index = j

        arr[i], arr[min_index] = arr[min_index], arr[i]

    return arr
```

### Example

```python
arr = [64, 25, 12, 22, 11]

result = selection_sort(arr)

print(result)
```

### Output

```text
[11, 12, 22, 25, 64]
```

---

## 8. Understanding the Nested Loops

The outer loop selects the position where the minimum element should be placed.

```python
for i in range(len(arr) - 1):
```

The inner loop searches for the smallest element in the remaining unsorted portion.

```python
for j in range(i + 1, len(arr)):
```

### Why `i + 1`?

Because `i` is already being treated as the current minimum position.

Therefore, we start comparing from the next element:

```text
i + 1
```

### Example

```text
Index:  0   1   2   3   4
Array: 64  25  12  22  11
        ↑
        i
```

When:

```text
i = 0
```

The inner loop checks:

```text
j = 1, 2, 3, 4
```

---

## 9. Selection Sort Pass Structure

For:

```text
64   25   12   22   11
```

### Pass 1

```text
64   25   12   22   11
↓
11   25   12   22   64
```

### Pass 2

```text
11   25   12   22   64
    ↓
11   12   25   22   64
```

### Pass 3

```text
11   12   25   22   64
        ↓
11   12   22   25   64
```

### Pass 4

```text
11   12   22   25   64
            ↓
11   12   22   25   64
```

### Final Result

```text
11   12   22   25   64
```

---

## 10. Sorted Part vs Unsorted Part

Selection Sort divides the array into two parts:

```text
Sorted Part | Unsorted Part
```

Initially:

```text
Sorted | 64  25  12  22  11
```

After Pass 1:

```text
11 | 25  12  22  64
```

After Pass 2:

```text
11  12 | 25  22  64
```

After Pass 3:

```text
11  12  22 | 25  64
```

After Pass 4:

```text
11  12  22  25 | 64
```

Finally:

```text
11  12  22  25  64
```

---

## 11. Important Points

* Selection Sort repeatedly finds the smallest element.
* The minimum element is placed at the current position.
* `minIndex` stores the position of the smallest element found so far.
* The inner loop searches the remaining unsorted part.
* The array is sorted using swaps.
* The sorted portion grows after every pass.
* The important comparison is:

```python
arr[j] < arr[min_index]
```

* Do not compare every element only with `arr[i]`.
* Always compare with the **minimum found so far** using `min_index`.

---

## 12. Common Mistake

### Incorrect

```python
if arr[j] < arr[i]:
    min_index = j
```

This compares every element with the original value at `arr[i]`.

### Correct

```python
if arr[j] < arr[min_index]:
    min_index = j
```

This compares every new element with the **smallest element found so far**.

### Remember

```text
minIndex = current position

        ↓

Compare next element with arr[minIndex]

        ↓

If smaller

        ↓

Update minIndex
```

---

## 13. Quick Revision

### Selection Sort

```text
Start
  ↓
Select current position
  ↓
Find minimum in unsorted part
  ↓
Store minimum index
  ↓
Swap with current position
  ↓
Move to next position
  ↓
Repeat
  ↓
Sorted Array
```

### Core Logic

```python
for i in range(len(arr) - 1):

    min_index = i

    for j in range(i + 1, len(arr)):

        if arr[j] < arr[min_index]:
            min_index = j

    arr[i], arr[min_index] = arr[min_index], arr[i]
```

### Remember

```text
Selection Sort
      ↓
Find Minimum
      ↓
Select Minimum
      ↓
Swap
      ↓
Repeat
```

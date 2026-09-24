# Array Hands-On Practice Problems

---

# 1. Find the Maximum Element

### Problem

Given an integer array, find the largest element without using the built-in `max()` function.

### Example

```python
arr = [12, 45, 7, 89, 34, 67]

# Output:
# 89
```

### Logic / Algorithm

1. Take the first element of the array and assume it is the largest.
2. Store it in a variable called `largest_num`.
3. Start traversing the array from index `1`.
4. Compare the current element with `largest_num`.
5. If the current element is greater than `largest_num`, update `largest_num`.
6. Continue until the end of the array.
7. Print `largest_num`.

### Step-by-Step Example

```text
arr = [12, 45, 7, 89, 34, 67]

largest_num = 12

45 > 12  → largest_num = 45
7  > 45  → No
89 > 45  → largest_num = 89
34 > 89  → No
67 > 89  → No

Maximum = 89
```

### Code

```python
arr = [12, 45, 7, 89, 34, 67]

largest_num = arr[0]

for i in range(1, len(arr)):

    if arr[i] > largest_num:
        largest_num = arr[i]

print(largest_num)
```

---

# 2. Find the Minimum Element

### Problem

Given an integer array, find the smallest element without using the built-in `min()` function.

### Example

```python
arr = [12, 45, 7, 89, 34, 67]

# Output:
# 7
```

### Logic / Algorithm

1. Take the first element of the array and assume it is the smallest.
2. Store it in a variable called `smallest_num`.
3. Start traversing the array from index `1`.
4. Compare the current element with `smallest_num`.
5. If the current element is smaller than `smallest_num`, update `smallest_num`.
6. Continue until the end of the array.
7. Print `smallest_num`.

### Step-by-Step Example

```text
arr = [12, 45, 7, 89, 34, 67]

smallest_num = 12

45 < 12  → No
7  < 12  → smallest_num = 7
89 < 7   → No
34 < 7   → No
67 < 7   → No

Minimum = 7
```

### Code

```python
arr = [12, 45, 7, 89, 34, 67]

smallest_num = arr[0]

for i in range(1, len(arr)):

    if arr[i] < smallest_num:
        smallest_num = arr[i]

print(smallest_num)
```

---

# 3. Find Maximum and Minimum Together

### Problem

Find both the maximum and minimum elements in a single traversal of the array.

### Example

```python
arr = [20, 5, 40, 10, 80, 15]

# Maximum = 80
# Minimum = 5
```

### Logic / Algorithm

1. Take the first element as both maximum and minimum.
2. Store it in `max_value`.
3. Store it in `min_value`.
4. Start traversing from index `1`.
5. If the current element is greater than `max_value`, update maximum.
6. If the current element is smaller than `min_value`, update minimum.
7. Continue until the end of the array.
8. Print maximum and minimum.

### Step-by-Step Example

```text
arr = [20, 5, 40, 10, 80, 15]

max_value = 20
min_value = 20

5:
5 > 20 → No
5 < 20 → min_value = 5

40:
40 > 20 → max_value = 40
40 < 5  → No

10:
10 > 40 → No
10 < 5  → No

80:
80 > 40 → max_value = 80
80 < 5  → No

15:
15 > 80 → No
15 < 5  → No

Maximum = 80
Minimum = 5
```

### Code

```python
arr = [20, 5, 40, 10, 80, 15]

max_value = arr[0]
min_value = arr[0]

for i in range(1, len(arr)):

    if arr[i] > max_value:
        max_value = arr[i]

    if arr[i] < min_value:
        min_value = arr[i]

print("Maximum:", max_value)
print("Minimum:", min_value)
```

---

# 4. Calculate Sum of Array

### Problem

Calculate the sum of all elements without using the built-in `sum()` function.

### Example

```python
arr = [10, 20, 30, 40]

# Output:
# 100
```

### Logic / Algorithm

1. Create a variable `total`.
2. Initialize `total = 0`.
3. Traverse every element of the array.
4. Add the current element to `total`.
5. Continue until the end of the array.
6. Print `total`.

### Step-by-Step Example

```text
arr = [10, 20, 30, 40]

total = 0

10 → total = 0 + 10  = 10
20 → total = 10 + 20 = 30
30 → total = 30 + 30 = 60
40 → total = 60 + 40 = 100

Sum = 100
```

### Code

```python
arr = [10, 20, 30, 40]

total = 0

for i in range(len(arr)):

    total += arr[i]

print(total)
```

---

# 5. Calculate Average

### Problem

Calculate the average of all elements without using the built-in `sum()` function.

### Example

```python
arr = [10, 20, 30, 40, 50]

# Output:
# 30.0
```

### Logic / Algorithm

1. Create a variable `total`.
2. Initialize `total = 0`.
3. Traverse every element of the array.
4. Add every element to `total`.
5. After traversal, divide `total` by the number of elements.
6. Store the result in `average`.
7. Print `average`.

### Formula

```text
Average = Total / Number of Elements
```

### Step-by-Step Example

```text
arr = [10, 20, 30, 40, 50]

total = 0

10 → total = 10
20 → total = 30
30 → total = 60
40 → total = 100
50 → total = 150

Number of elements = 5

Average = 150 / 5
Average = 30
```

### Code

```python
arr = [10, 20, 30, 40, 50]

total = 0

for i in range(len(arr)):

    total += arr[i]

average = total / len(arr)

print(average)
```

---

# 6. Count Even Numbers

### Problem

Count how many even numbers are present in the array.

### Example

```python
arr = [10, 15, 22, 33, 40, 51]

# Output:
# 3
```

### Logic / Algorithm

1. Create a variable `count`.
2. Initialize `count = 0`.
3. Traverse every element of the array.
4. Check whether the current element is divisible by `2`.
5. If `arr[i] % 2 == 0`, the number is even.
6. Increase `count` by `1`.
7. Continue until the end.
8. Print `count`.

### Step-by-Step Example

```text
arr = [10, 15, 22, 33, 40, 51]

count = 0

10 % 2 == 0 → Even → count = 1
15 % 2 == 0 → No
22 % 2 == 0 → Even → count = 2
33 % 2 == 0 → No
40 % 2 == 0 → Even → count = 3
51 % 2 == 0 → No

Even numbers = 3
```

### Code

```python
arr = [10, 15, 22, 33, 40, 51]

count = 0

for i in range(len(arr)):

    if arr[i] % 2 == 0:
        count += 1

print(count)
```

---

# 7. Count Positive, Negative and Zero

### Problem

Count the number of positive numbers, negative numbers, and zeros in the array.

### Example

```python
arr = [-5, 10, 0, -3, 8, 0, 7]

# Positive = 3
# Negative = 2
# Zero = 2
```

### Logic / Algorithm

1. Create three counters:
   - `positive_count`
   - `negative_count`
   - `zero_count`
2. Initialize all counters to `0`.
3. Traverse every element of the array.
4. If the element is less than `0`, increase `negative_count`.
5. If the element is equal to `0`, increase `zero_count`.
6. Otherwise, the element is positive, so increase `positive_count`.
7. Continue until the end.
8. Print all three counts.

### Step-by-Step Example

```text
arr = [-5, 10, 0, -3, 8, 0, 7]

-5 → Negative → negative_count = 1
10 → Positive → positive_count = 1
0  → Zero     → zero_count = 1
-3 → Negative → negative_count = 2
8  → Positive → positive_count = 2
0  → Zero     → zero_count = 2
7  → Positive → positive_count = 3

Positive = 3
Negative = 2
Zero = 2
```

### Code

```python
arr = [-5, 10, 0, -3, 8, 0, 7]

positive_count = 0
negative_count = 0
zero_count = 0

for i in range(len(arr)):

    if arr[i] < 0:
        negative_count += 1

    elif arr[i] == 0:
        zero_count += 1

    else:
        positive_count += 1

print("Positive:", positive_count)
print("Negative:", negative_count)
print("Zero:", zero_count)
```

---

# 8. Linear Search

### Problem

Search for a given element in an array and return its index.

If the element is not found, return `-1`.

### Example

```python
arr = [10, 30, 50, 70, 90]
target = 70

# Output:
# 3
```

### Logic / Algorithm

1. Start from index `0`.
2. Traverse the array one element at a time.
3. Compare the current element with `target`.
4. If the current element is equal to `target`, return its index.
5. If the target is not found after checking all elements, return `-1`.

### Step-by-Step Example

```text
arr = [10, 30, 50, 70, 90]
target = 70

Index 0 → 10 == 70 → No
Index 1 → 30 == 70 → No
Index 2 → 50 == 70 → No
Index 3 → 70 == 70 → Yes

Return index 3
```

### Code

```python
def find_index(arr, target):

    for i in range(len(arr)):

        if arr[i] == target:
            return i

    return -1


arr = [10, 30, 50, 70, 90]
target = 70

print(find_index(arr, target))
```

---

# 9. Reverse an Array In-Place

### Problem

Reverse the array without creating another array.

### Example

```python
arr = [10, 20, 30, 40, 50]

# Output:
# [50, 40, 30, 20, 10]
```

### Requirements

- Do not create another array.
- Modify the original array.
- Use two pointers.

### Logic / Algorithm

1. Create two pointers:
   - `left = 0`
   - `right = len(arr) - 1`
2. Compare `left` and `right`.
3. While `left < right`, swap the elements.
4. Move `left` one position forward.
5. Move `right` one position backward.
6. Continue until both pointers meet.

### Step-by-Step Example

```text
Initial:
[10, 20, 30, 40, 50]
 ↑              ↑
left           right

Swap:
[50, 20, 30, 40, 10]

Move pointers:
   ↑           ↑
  left       right

Swap:
[50, 40, 30, 20, 10]

Pointers meet.

Final:
[50, 40, 30, 20, 10]
```

### Code

```python
arr = [10, 20, 30, 40, 50]

left = 0
right = len(arr) - 1

while left < right:

    arr[left], arr[right] = arr[right], arr[left]

    left += 1
    right -= 1

print(arr)
```

---

# 10. Check Whether Array Is Sorted

### Problem

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

### Logic / Algorithm

1. Start from index `0`.
2. Compare the current element with the next element.
3. Check whether `arr[i] > arr[i + 1]`.
4. If this condition is true, the array is not sorted.
5. Return `False`.
6. If all adjacent elements are in ascending order, return `True`.

### Step-by-Step Example

```text
arr = [10, 20, 30, 40, 50]

10 > 20 → No
20 > 30 → No
30 > 40 → No
40 > 50 → No

No problem found.

Array is sorted → True
```

### Code

```python
def is_sorted(arr):

    for i in range(len(arr) - 1):

        if arr[i] > arr[i + 1]:
            return False

    return True


arr = [10, 20, 30, 40, 50]

print(is_sorted(arr))
```

---

# 11. Find the Second Largest Element

### Problem

Find the second largest **distinct** element without sorting the array.

### Example

```python
arr = [10, 40, 20, 50, 30]

# Output:
# 40
```

### Requirements

- Do not use sorting.
- The second largest value must be distinct.

### Logic / Algorithm

1. Create two variables:
   - `largest`
   - `second_largest`
2. Initialize both using negative infinity.
3. Traverse the array.
4. If the current element is greater than `largest`:
   - Move the current `largest` into `second_largest`.
   - Update `largest` with the current element.
5. Otherwise, check whether the current element is greater than `second_largest`.
6. Also make sure the current element is not equal to `largest`.
7. If both conditions are true, update `second_largest`.
8. Continue until the end.
9. `second_largest` will contain the answer.

### Step-by-Step Example

```text
arr = [10, 40, 20, 50, 30]

largest = -infinity
second_largest = -infinity

10:
10 > largest
second_largest = -infinity
largest = 10

40:
40 > 10
second_largest = 10
largest = 40

20:
20 > 40 → No
20 > 10 → Yes
second_largest = 20

50:
50 > 40
second_largest = 40
largest = 50

30:
30 > 50 → No
30 > 40 → No

Second Largest = 40
```

### Code

```python
arr = [10, 40, 20, 50, 30]

largest = float('-inf')
second_largest = float('-inf')

for i in range(len(arr)):

    if arr[i] > largest:

        second_largest = largest
        largest = arr[i]

    elif arr[i] > second_largest and arr[i] != largest:

        second_largest = arr[i]

if second_largest == float('-inf'):

    print("No second largest element found")

else:

    print("Second Largest:", second_largest)
```

---

# 12. Find the Second Smallest Element

### Problem

Find the second smallest **distinct** element without sorting the array.

### Example

```python
arr = [20, 5, 10, 40, 15]

# Output:
# 10
```

### Requirements

- Do not use sorting.
- The second smallest value must be distinct.

### Logic / Algorithm

1. Create two variables:
   - `smallest`
   - `second_smallest`
2. Initialize both using positive infinity.
3. Traverse the array.
4. If the current element is smaller than `smallest`:
   - Move the current `smallest` into `second_smallest`.
   - Update `smallest`.
5. Otherwise, check whether the current element is smaller than `second_smallest`.
6. Also make sure it is not equal to `smallest`.
7. If both conditions are true, update `second_smallest`.
8. Continue until the end.
9. `second_smallest` will contain the answer.

### Step-by-Step Example

```text
arr = [20, 5, 10, 40, 15]

smallest = infinity
second_smallest = infinity

20:
20 < infinity
second_smallest = infinity
smallest = 20

5:
5 < 20
second_smallest = 20
smallest = 5

10:
10 < 5 → No
10 < 20 → Yes
second_smallest = 10

40:
40 < 5 → No
40 < 10 → No

15:
15 < 5 → No
15 < 10 → No

Second Smallest = 10
```

### Code

```python
arr = [20, 5, 10, 40, 15]

smallest = float('inf')
second_smallest = float('inf')

for i in range(len(arr)):

    if arr[i] < smallest:

        second_smallest = smallest
        smallest = arr[i]

    elif arr[i] < second_smallest and arr[i] != smallest:

        second_smallest = arr[i]

if second_smallest == float('inf'):

    print("No second smallest element found")

else:

    print("Second Smallest:", second_smallest)
```

---

# 13. Move All Zeros to the End

### Problem

Move all zeros to the end of the array while preserving the relative order of non-zero elements.

### Example

```python
arr = [0, 1, 0, 3, 12]

# Output:
# [1, 3, 12, 0, 0]
```

### Requirements

- Modify the original array.
- Do not create another array.
- Preserve the relative order of non-zero elements.

### Logic / Algorithm

1. Create a variable `position = 0`.
2. Traverse the array from left to right.
3. Check whether the current element is non-zero.
4. If the current element is zero, skip it.
5. If the current element is non-zero:
   - Swap it with `arr[position]`.
   - Increase `position`.
6. Continue until the end.
7. All non-zero elements will be placed at the beginning.
8. Zeros will automatically move to the end.

### Step-by-Step Example

```text
Initial:
[0, 1, 0, 3, 12]
 position = 0

i = 0
arr[0] = 0
0 == 0 → Skip

Array:
[0, 1, 0, 3, 12]

i = 1
arr[1] = 1
1 != 0 → Swap arr[position] and arr[i]

0,1 = 1,0

[1, 0, 0, 3, 12]

position = 1


i = 2
arr[2] = 0
0 == 0 → Skip


i = 3
arr[3] = 3
3 != 0 → Swap

0,3 = 3,0

[1, 3, 0, 0, 12]

position = 2


i = 4
arr[4] = 12
12 != 0 → Swap

0,12 = 12,0

[1, 3, 12, 0, 0]

position = 3
```

### Code

```python
arr = [0, 1, 0, 3, 12]

position = 0

for i in range(len(arr)):

    if arr[i] != 0:

        arr[position], arr[i] = arr[i], arr[position]

        # 0,1 = 1,0
        # [1,0,0,3,12]

        # 0,3 = 3,0
        # [1,3,0,0,12]

        # 0,12 = 12,0
        # [1,3,12,0,0]

        position += 1

print(arr)
```

---

# 14. Move All Negative Numbers to the Beginning

### Problem

Move all negative numbers to the beginning of the array.

The relative order of elements does not need to be preserved.

### Example

```python
arr = [10, -2, 5, -7, 8, -1]

# One possible output:
# [-1, -2, -7, 5, 8, 10]
```

### Requirements

- Modify the original array.
- Do not create another array.
- All negative numbers should come before non-negative numbers.
- Relative order is not required.

### Logic / Algorithm

1. Create two pointers:
   - `start = 0`
   - `end = len(arr) - 1`
2. `start` moves from left to right.
3. `end` moves from right to left.
4. If `arr[start]` is already negative, move `start` forward.
5. If `arr[end]` is non-negative, move `end` backward.
6. If `arr[start]` is non-negative and `arr[end]` is negative:
   - Swap both elements.
   - Move both pointers.
7. Continue until `start` and `end` meet.

### Important

Do not compare the values like:

```python
arr[start] > arr[end]
```

The comparison should be based on whether the numbers are **negative or non-negative**.

### Step-by-Step Example

```text
Initial:

[10, -2, 5, -7, 8, -1]
 ↑                    ↑
start                end

arr[start] = 10
10 is non-negative

arr[end] = -1
-1 is negative

Swap:

[-1, -2, 5, -7, 8, 10]

Move pointers:

   ↑              ↑
 start            end


arr[start] = -2
Already negative
Move start


arr[end] = 8
Non-negative
Move end


arr[start] = 5
Non-negative

arr[end] = -7
Negative

Swap:

[-1, -2, -7, 5, 8, 10]
```

### Code

```python
arr = [10, -2, 5, -7, 8, -1]

start = 0
end = len(arr) - 1

while start < end:

    if arr[start] < 0:

        # Already negative
        start += 1

    elif arr[end] >= 0:

        # Already non-negative
        end -= 1

    else:

        # arr[start] = non-negative
        # arr[end] = negative
        # Swap them

        arr[start], arr[end] = arr[end], arr[start]

        # [10,-2,5,-7,8,-1]
        #  ↑              ↑
        # start          end
        #
        # [-1,-2,5,-7,8,10]

        start += 1
        end -= 1

print(arr)
```

---

# 15. Remove Duplicates from a Sorted Array

### Problem

Given a sorted array, remove duplicate elements in-place.

Return the number of unique elements.

### Example

```python
arr = [1, 1, 2, 2, 3, 3, 4]

# Unique elements:
# [1, 2, 3, 4]

# Unique count:
# 4
```

### Requirements

- The array must already be sorted.
- Modify the original array.
- Do not create another array.
- Do not use `set()`.
- Do not use sorting.
- The first `position` elements should contain the unique values.
- `position` represents the number of unique elements.

### Logic / Algorithm

1. The first element is always unique.
2. Set `position = 1`.
3. Start traversing from index `1`.
4. Compare the current element with the previous element.
5. If both elements are the same:
   - It is a duplicate.
   - Skip it.
6. If the elements are different:
   - It is a new unique element.
   - Store it at `arr[position]`.
   - Increase `position`.
7. Continue until the end.
8. At the end, `position` represents the number of unique elements.
9. The first `position` elements contain the unique values.

### Step-by-Step Example

```text
arr = [1, 1, 2, 2, 3, 3, 4]

position = 1

i = 1
arr[1] = 1
arr[0] = 1

1 == 1
Duplicate → Skip


i = 2
arr[2] = 2
arr[1] = 1

2 != 1
New unique element

arr[position] = arr[i]

arr[1] = 2

Array:
[1, 2, 2, 2, 3, 3, 4]

position = 2


i = 3
arr[3] = 2
arr[2] = 2

2 == 2
Duplicate → Skip


i = 4
arr[4] = 3
arr[3] = 2

3 != 2
New unique element

arr[2] = 3

Array:
[1, 2, 3, 2, 3, 3, 4]

position = 3


i = 5
arr[5] = 3
arr[4] = 3

3 == 3
Duplicate → Skip


i = 6
arr[6] = 4
arr[5] = 3

4 != 3
New unique element

arr[3] = 4

Array:
[1, 2, 3, 4, 3, 3, 4]

position = 4
```

### Final Result

```text
First 4 elements:

[1, 2, 3, 4]

Number of unique elements:

4
```

### Code

```python
arr = [1, 1, 2, 2, 3, 3, 4]

position = 1

for i in range(1, len(arr)):

    if arr[i] != arr[i - 1]:

        arr[position] = arr[i]

        # 2 → arr[1] = 2
        # [1,2,2,2,3,3,4]

        # 3 → arr[2] = 3
        # [1,2,3,2,3,3,4]

        # 4 → arr[3] = 4
        # [1,2,3,4,3,3,4]

        position += 1

print(arr)
print(position)

# Output:
# [1,2,3,4,3,3,4]
# 4
```

---

# Summary of Concepts Practiced

| No. | Problem | Main Concept |
|---|---|---|
| 1 | Maximum Element | Traversal + Comparison |
| 2 | Minimum Element | Traversal + Comparison |
| 3 | Maximum and Minimum | Single Traversal |
| 4 | Sum | Accumulator |
| 5 | Average | Accumulator + Formula |
| 6 | Count Even Numbers | Modulus `%` |
| 7 | Positive/Negative/Zero | Conditional Statements |
| 8 | Linear Search | Searching |
| 9 | Reverse Array | Two Pointers + Swap |
| 10 | Check Sorted | Adjacent Comparison |
| 11 | Second Largest | Two Variables + Traversal |
| 12 | Second Smallest | Two Variables + Traversal |
| 13 | Move Zeros | Two Pointers + In-Place |
| 14 | Move Negatives | Two Pointers + In-Place |
| 15 | Remove Duplicates | Two Pointers + In-Place |

---

# Important Array Patterns

## 1. Traversal

```python
for i in range(len(arr)):
    print(arr[i])
```

Used when we need to visit every element.

---

## 2. Accumulator

```python
total = 0

for i in range(len(arr)):
    total += arr[i]
```

Used for:

- Sum
- Average
- Counting

---

## 3. Comparison

```python
if arr[i] > largest:
    largest = arr[i]
```

Used for:

- Maximum
- Minimum
- Second largest
- Second smallest

---

## 4. Two Pointers

```python
left = 0
right = len(arr) - 1

while left < right:
    ...
    left += 1
    right -= 1
```

Used for:

- Reverse array
- Moving negative numbers
- Partitioning problems

---

## 5. In-Place Modification

In-place means modifying the original array without creating another array.

Example:

```python
arr[position], arr[i] = arr[i], arr[position]
```

Used in:

- Move zeros
- Move negative numbers
- Remove duplicates
- Reverse array

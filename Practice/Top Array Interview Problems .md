# Top Array Interview Problems (Google, Meta, Amazon, Microsoft, etc.)

Each problem has: **Question → Brute Force → Optimal → Complexity**. Code is in Python.

---

## Quick Summary Table

| # | Problem | Brute Force | Optimal | Pattern |
|---|---------|-------------|---------|---------|
| 1 | Two Sum | O(n²) / O(1) | O(n) / O(n) | Hash Map |
| 2 | Best Time to Buy & Sell Stock | O(n²) / O(1) | O(n) / O(1) | Track min |
| 3 | Maximum Subarray | O(n²) / O(1) | O(n) / O(1) | Kadane |
| 4 | Contains Duplicate | O(n²) / O(1) | O(n) / O(n) | Hash Set |
| 5 | Product of Array Except Self | O(n²) / O(1) | O(n) / O(1) | Prefix/Suffix |
| 6 | Move Zeroes | O(n) / O(n) | O(n) / O(1) | Two Pointers |
| 7 | Merge Intervals | O(n²) / O(n) | O(n log n) / O(n) | Sort |
| 8 | 3Sum | O(n³) / O(1) | O(n²) / O(1) | Sort + Two Pointers |
| 9 | Container With Most Water | O(n²) / O(1) | O(n) / O(1) | Two Pointers |
| 10 | Trapping Rain Water | O(n²) / O(1) | O(n) / O(1) | Two Pointers |
| 11 | Subarray Sum Equals K | O(n²) / O(1) | O(n) / O(n) | Prefix Sum + Hash |
| 12 | Rotate Array | O(n·k) / O(1) | O(n) / O(1) | Reverse trick |
| 13 | Missing Number | O(n²) / O(1) | O(n) / O(1) | Sum / XOR |
| 14 | Majority Element | O(n²) / O(1) | O(n) / O(1) | Boyer-Moore |
| 15 | Longest Consecutive Sequence | O(n²) / O(1) | O(n) / O(n) | Hash Set |
| 16 | Sort Colors | O(n log n) / O(1) | O(n) / O(1) | Dutch Flag |
| 17 | Maximum Product Subarray | O(n²) / O(1) | O(n) / O(1) | Track min & max |
| 18 | Search in Rotated Sorted Array | O(n) / O(1) | O(log n) / O(1) | Binary Search |
| 19 | First Missing Positive | O(n²) / O(1) | O(n) / O(1) | Cyclic Placement |
| 20 | Sliding Window Maximum | O(n·k) / O(1) | O(n) / O(k) | Monotonic Deque |
| 21 | Remove Duplicates from Sorted Array | O(n) / O(n) | O(n) / O(1) | Two Pointers |
| 22 | Find Duplicate Number | O(n²) / O(1) | O(n) / O(1) | Floyd Cycle |

(Format: Time / Space)

---

## 1. Two Sum

**Question:** Given an array `nums` and a `target`, return indices of the two numbers that add up to `target`. Exactly one solution exists.

### Brute Force
Check every pair.
```python
def two_sum(nums, target):
    n = len(nums)
    for i in range(n):
        for j in range(i + 1, n):
            if nums[i] + nums[j] == target:
                return [i, j]
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal (Hash Map)
For each number, check if `target - num` was already seen.
```python
def two_sum(nums, target):
    seen = {}  # value -> index
    for i, x in enumerate(nums):
        if target - x in seen:
            return [seen[target - x], i]
        seen[x] = i
```
- **Time:** O(n)  **Space:** O(n)

---

## 2. Best Time to Buy and Sell Stock

**Question:** `prices[i]` is the price on day i. Buy once, sell once later. Return max profit (0 if none).

### Brute Force
Try every buy/sell pair.
```python
def max_profit(prices):
    best = 0
    for i in range(len(prices)):
        for j in range(i + 1, len(prices)):
            best = max(best, prices[j] - prices[i])
    return best
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal
Keep the minimum price so far; profit if sold today = `price - min_so_far`.
```python
def max_profit(prices):
    min_price, best = float('inf'), 0
    for p in prices:
        min_price = min(min_price, p)
        best = max(best, p - min_price)
    return best
```
- **Time:** O(n)  **Space:** O(1)

---

## 3. Maximum Subarray (Kadane's Algorithm)

**Question:** Find the contiguous subarray with the largest sum.

### Brute Force
Check every subarray.
```python
def max_subarray(nums):
    best = float('-inf')
    for i in range(len(nums)):
        total = 0
        for j in range(i, len(nums)):
            total += nums[j]
            best = max(best, total)
    return best
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal (Kadane)
At each element: extend the current subarray or start fresh.
```python
def max_subarray(nums):
    cur = best = nums[0]
    for x in nums[1:]:
        cur = max(x, cur + x)
        best = max(best, cur)
    return best
```
- **Time:** O(n)  **Space:** O(1)

---

## 4. Contains Duplicate

**Question:** Return `True` if any value appears at least twice.

### Brute Force
```python
def contains_duplicate(nums):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] == nums[j]:
                return True
    return False
```
- **Time:** O(n²)  **Space:** O(1)

### Better (Sorting)
Sort, then compare neighbours. Time O(n log n), Space O(1) (in-place sort).

### Optimal (Hash Set)
```python
def contains_duplicate(nums):
    seen = set()
    for x in nums:
        if x in seen:
            return True
        seen.add(x)
    return False
```
- **Time:** O(n)  **Space:** O(n)

---

## 5. Product of Array Except Self

**Question:** Return `answer` where `answer[i]` = product of all elements except `nums[i]`. **Do not use division**, O(n) time.

### Brute Force
```python
def product_except_self(nums):
    n = len(nums)
    res = [1] * n
    for i in range(n):
        for j in range(n):
            if i != j:
                res[i] *= nums[j]
    return res
```
- **Time:** O(n²)  **Space:** O(1) extra

### Optimal (Prefix & Suffix)
First pass stores product of everything to the left; second pass multiplies by everything to the right.
```python
def product_except_self(nums):
    n = len(nums)
    res = [1] * n
    prefix = 1
    for i in range(n):
        res[i] = prefix
        prefix *= nums[i]
    suffix = 1
    for i in range(n - 1, -1, -1):
        res[i] *= suffix
        suffix *= nums[i]
    return res
```
- **Time:** O(n)  **Space:** O(1) extra (output array not counted)

---

## 6. Move Zeroes

**Question:** Move all `0`s to the end in-place, keeping the order of non-zero elements.

### Brute Force (extra array)
```python
def move_zeroes(nums):
    non_zero = [x for x in nums if x != 0]
    zeros = [0] * (len(nums) - len(non_zero))
    nums[:] = non_zero + zeros
```
- **Time:** O(n)  **Space:** O(n)

### Optimal (Two Pointers)
`j` marks where the next non-zero should go.
```python
def move_zeroes(nums):
    j = 0
    for i in range(len(nums)):
        if nums[i] != 0:
            nums[i], nums[j] = nums[j], nums[i]
            j += 1
```
- **Time:** O(n)  **Space:** O(1)

---

## 7. Merge Intervals

**Question:** Given `intervals[i] = [start, end]`, merge all overlapping intervals.

### Brute Force
Repeatedly scan and merge any overlapping pair until nothing changes.
- **Time:** O(n²) or worse  **Space:** O(n)

### Optimal (Sort by start)
```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    res = [intervals[0]]
    for start, end in intervals[1:]:
        if start <= res[-1][1]:          # overlap
            res[-1][1] = max(res[-1][1], end)
        else:
            res.append([start, end])
    return res
```
- **Time:** O(n log n)  **Space:** O(n)

---

## 8. 3Sum

**Question:** Find all unique triplets that sum to 0.

### Brute Force
```python
def three_sum(nums):
    n = len(nums)
    res = set()
    for i in range(n):
        for j in range(i + 1, n):
            for k in range(j + 1, n):
                if nums[i] + nums[j] + nums[k] == 0:
                    res.add(tuple(sorted((nums[i], nums[j], nums[k]))))
    return [list(t) for t in res]
```
- **Time:** O(n³)  **Space:** O(n) for the set

### Optimal (Sort + Two Pointers)
```python
def three_sum(nums):
    nums.sort()
    res = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue                      # skip duplicate anchor
        l, r = i + 1, len(nums) - 1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s < 0:
                l += 1
            elif s > 0:
                r -= 1
            else:
                res.append([nums[i], nums[l], nums[r]])
                l += 1
                while l < r and nums[l] == nums[l - 1]:
                    l += 1
    return res
```
- **Time:** O(n²)  **Space:** O(1) (ignoring output / sort)

---

## 9. Container With Most Water

**Question:** `height[i]` is a vertical line. Pick two lines that, with the x-axis, hold the most water.

### Brute Force
```python
def max_area(height):
    best = 0
    for i in range(len(height)):
        for j in range(i + 1, len(height)):
            best = max(best, min(height[i], height[j]) * (j - i))
    return best
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal (Two Pointers)
Always move the pointer at the shorter line (moving the taller one can't help).
```python
def max_area(height):
    l, r, best = 0, len(height) - 1, 0
    while l < r:
        best = max(best, min(height[l], height[r]) * (r - l))
        if height[l] < height[r]:
            l += 1
        else:
            r -= 1
    return best
```
- **Time:** O(n)  **Space:** O(1)

---

## 10. Trapping Rain Water

**Question:** Given elevation heights, compute how much water is trapped after rain.

### Brute Force
Water above `i` = `min(max_left, max_right) - height[i]`.
```python
def trap(height):
    n, total = len(height), 0
    for i in range(n):
        left_max = max(height[:i + 1])
        right_max = max(height[i:])
        total += min(left_max, right_max) - height[i]
    return total
```
- **Time:** O(n²)  **Space:** O(1)

### Better (Prefix/Suffix arrays)
Precompute `left_max[]` and `right_max[]`. Time O(n), Space O(n).

### Optimal (Two Pointers)
```python
def trap(height):
    l, r = 0, len(height) - 1
    left_max = right_max = total = 0
    while l < r:
        if height[l] < height[r]:
            left_max = max(left_max, height[l])
            total += left_max - height[l]
            l += 1
        else:
            right_max = max(right_max, height[r])
            total += right_max - height[r]
            r -= 1
    return total
```
- **Time:** O(n)  **Space:** O(1)

---

## 11. Subarray Sum Equals K

**Question:** Count contiguous subarrays whose sum equals `k` (array may have negatives).

### Brute Force
```python
def subarray_sum(nums, k):
    count = 0
    for i in range(len(nums)):
        total = 0
        for j in range(i, len(nums)):
            total += nums[j]
            if total == k:
                count += 1
    return count
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal (Prefix Sum + Hash Map)
If `prefix - k` was seen before, a subarray summing to `k` ends here.
```python
def subarray_sum(nums, k):
    count, prefix = 0, 0
    freq = {0: 1}
    for x in nums:
        prefix += x
        count += freq.get(prefix - k, 0)
        freq[prefix] = freq.get(prefix, 0) + 1
    return count
```
- **Time:** O(n)  **Space:** O(n)

---

## 12. Rotate Array

**Question:** Rotate the array to the right by `k` steps, in-place.

### Brute Force
Rotate by one position, `k` times.
```python
def rotate(nums, k):
    n = len(nums)
    k %= n
    for _ in range(k):
        last = nums[-1]
        for i in range(n - 1, 0, -1):
            nums[i] = nums[i - 1]
        nums[0] = last
```
- **Time:** O(n·k)  **Space:** O(1)

### Optimal (Reverse trick)
Reverse whole array → reverse first `k` → reverse the rest.
```python
def rotate(nums, k):
    n = len(nums)
    k %= n

    def reverse(l, r):
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l += 1
            r -= 1

    reverse(0, n - 1)
    reverse(0, k - 1)
    reverse(k, n - 1)
```
- **Time:** O(n)  **Space:** O(1)

---

## 13. Missing Number

**Question:** Array has `n` distinct numbers from `0..n`. Find the one missing.

### Brute Force
```python
def missing_number(nums):
    for i in range(len(nums) + 1):
        if i not in nums:       # `in` on a list is O(n)
            return i
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal (Sum formula)
```python
def missing_number(nums):
    n = len(nums)
    return n * (n + 1) // 2 - sum(nums)
```
(XOR of all indices and values also works and avoids overflow in other languages.)
- **Time:** O(n)  **Space:** O(1)

---

## 14. Majority Element

**Question:** Find the element that appears more than `n/2` times (guaranteed to exist).

### Brute Force
```python
def majority_element(nums):
    n = len(nums)
    for x in nums:
        if nums.count(x) > n // 2:
            return x
```
- **Time:** O(n²)  **Space:** O(1)

### Better (Hash Map)
Count frequencies. Time O(n), Space O(n).

### Optimal (Boyer-Moore Voting)
```python
def majority_element(nums):
    candidate, count = None, 0
    for x in nums:
        if count == 0:
            candidate = x
        count += 1 if x == candidate else -1
    return candidate
```
- **Time:** O(n)  **Space:** O(1)

---

## 15. Longest Consecutive Sequence

**Question:** Length of the longest run of consecutive integers (unsorted array). Must be O(n).

### Brute Force
For each number, keep checking `num+1, num+2, ...` using a linear search.
```python
def longest_consecutive(nums):
    best = 0
    for x in nums:
        cur, length = x, 1
        while cur + 1 in nums:      # list lookup is O(n)
            cur += 1
            length += 1
        best = max(best, length)
    return best
```
- **Time:** O(n²) or O(n³)  **Space:** O(1)

### Better (Sort)
Sort and count runs. Time O(n log n), Space O(1).

### Optimal (Hash Set)
Only start counting from numbers that are the **start** of a sequence.
```python
def longest_consecutive(nums):
    s = set(nums)
    best = 0
    for x in s:
        if x - 1 not in s:          # start of a sequence
            cur, length = x, 1
            while cur + 1 in s:
                cur += 1
                length += 1
            best = max(best, length)
    return best
```
- **Time:** O(n)  **Space:** O(n)

---

## 16. Sort Colors (Dutch National Flag)

**Question:** Array has only `0`, `1`, `2`. Sort in-place without using the library sort.

### Brute Force / Better
- Sort: O(n log n)
- Counting sort (count 0s, 1s, 2s then overwrite): O(n) time, O(1) space, **two passes**

### Optimal (One pass, 3 pointers)
```python
def sort_colors(nums):
    low, mid, high = 0, 0, len(nums) - 1
    while mid <= high:
        if nums[mid] == 0:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == 1:
            mid += 1
        else:
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
```
- **Time:** O(n) single pass  **Space:** O(1)

---

## 17. Maximum Product Subarray

**Question:** Find the contiguous subarray with the largest product.

### Brute Force
```python
def max_product(nums):
    best = float('-inf')
    for i in range(len(nums)):
        prod = 1
        for j in range(i, len(nums)):
            prod *= nums[j]
            best = max(best, prod)
    return best
```
- **Time:** O(n²)  **Space:** O(1)

### Optimal
Track both max and min product ending here (a negative can flip min into max).
```python
def max_product(nums):
    cur_max = cur_min = best = nums[0]
    for x in nums[1:]:
        candidates = (x, cur_max * x, cur_min * x)
        cur_max, cur_min = max(candidates), min(candidates)
        best = max(best, cur_max)
    return best
```
- **Time:** O(n)  **Space:** O(1)

---

## 18. Search in Rotated Sorted Array

**Question:** A sorted array was rotated at an unknown pivot (e.g. `[4,5,6,7,0,1,2]`). Find `target`'s index or `-1`. Must be O(log n).

### Brute Force
```python
def search(nums, target):
    for i, x in enumerate(nums):
        if x == target:
            return i
    return -1
```
- **Time:** O(n)  **Space:** O(1)

### Optimal (Modified Binary Search)
One half is always sorted. Decide which half the target lies in.
```python
def search(nums, target):
    l, r = 0, len(nums) - 1
    while l <= r:
        mid = (l + r) // 2
        if nums[mid] == target:
            return mid
        if nums[l] <= nums[mid]:                  # left half sorted
            if nums[l] <= target < nums[mid]:
                r = mid - 1
            else:
                l = mid + 1
        else:                                     # right half sorted
            if nums[mid] < target <= nums[r]:
                l = mid + 1
            else:
                r = mid - 1
    return -1
```
- **Time:** O(log n)  **Space:** O(1)

---

## 19. First Missing Positive

**Question:** Find the smallest missing positive integer in an unsorted array. Must run in O(n) time and O(1) extra space.

### Brute Force
```python
def first_missing_positive(nums):
    i = 1
    while i in nums:        # list lookup is O(n)
        i += 1
    return i
```
- **Time:** O(n²)  **Space:** O(1)

### Better (Hash Set)
Put all in a set, then check 1, 2, 3... Time O(n), Space O(n).

### Optimal (Cyclic Placement)
Place each value `x` (where `1 <= x <= n`) at index `x-1`.
```python
def first_missing_positive(nums):
    n = len(nums)
    for i in range(n):
        while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
            j = nums[i] - 1
            nums[i], nums[j] = nums[j], nums[i]
    for i in range(n):
        if nums[i] != i + 1:
            return i + 1
    return n + 1
```
- **Time:** O(n)  **Space:** O(1)

---

## 20. Sliding Window Maximum

**Question:** For every window of size `k`, return the maximum.

### Brute Force
```python
def max_sliding_window(nums, k):
    return [max(nums[i:i + k]) for i in range(len(nums) - k + 1)]
```
- **Time:** O(n·k)  **Space:** O(1) extra

### Optimal (Monotonic Deque)
Deque stores indices with decreasing values; front is always the window max.
```python
from collections import deque

def max_sliding_window(nums, k):
    dq, res = deque(), []
    for i, x in enumerate(nums):
        while dq and nums[dq[-1]] <= x:     # remove smaller elements
            dq.pop()
        dq.append(i)
        if dq[0] <= i - k:                  # out of window
            dq.popleft()
        if i >= k - 1:
            res.append(nums[dq[0]])
    return res
```
- **Time:** O(n)  **Space:** O(k)

---

## 21. Remove Duplicates from Sorted Array

**Question:** Remove duplicates in-place from a sorted array; return the new length.

### Brute Force (extra memory)
```python
def remove_duplicates(nums):
    unique = sorted(set(nums))
    nums[:len(unique)] = unique
    return len(unique)
```
- **Time:** O(n log n) (with sorted) / O(n)  **Space:** O(n)

### Optimal (Two Pointers)
```python
def remove_duplicates(nums):
    j = 1
    for i in range(1, len(nums)):
        if nums[i] != nums[i - 1]:
            nums[j] = nums[i]
            j += 1
    return j
```
- **Time:** O(n)  **Space:** O(1)

---

## 22. Find the Duplicate Number

**Question:** Array of `n+1` integers in range `[1, n]` has exactly one repeated number. Find it **without modifying** the array and using O(1) space.

### Brute Force
```python
def find_duplicate(nums):
    for i in range(len(nums)):
        for j in range(i + 1, len(nums)):
            if nums[i] == nums[j]:
                return nums[i]
```
- **Time:** O(n²)  **Space:** O(1)

### Better
- Sort: O(n log n) time, modifies array
- Hash set: O(n) time, O(n) space

### Optimal (Floyd's Cycle Detection)
Treat `nums[i]` as a "next pointer"; the duplicate is the cycle entry.
```python
def find_duplicate(nums):
    slow = fast = nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```
- **Time:** O(n)  **Space:** O(1)

---

## Pattern Cheat Sheet (How to Recognize Which Technique)

| If the problem says... | Think... |
|------------------------|----------|
| Pair/target sum, "seen before" | **Hash Map** |
| Sorted array, pair/triplet, palindrome-like | **Two Pointers** |
| Contiguous subarray, max/min sum | **Kadane / Sliding Window** |
| Subarray sum equals K (with negatives) | **Prefix Sum + Hash Map** |
| Fixed-size window max/min | **Monotonic Deque** |
| Sorted / rotated sorted, O(log n) | **Binary Search** |
| Values in range `1..n`, find missing/duplicate | **Cyclic Sort / Index as hash / Floyd** |
| Overlapping ranges | **Sort + Merge** |
| In-place, O(1) space | **Two Pointers / Swapping / Reverse trick** |
| Only 0/1/2 values | **Dutch National Flag** |
| Majority element | **Boyer-Moore Voting** |

---

## Interview Tips

1. **Always start with brute force**, state its complexity, then optimize. Interviewers want to see your thought process.
2. **Clarify first:** Are there negatives? Duplicates? Is it sorted? Can I modify the input?
3. **Think of edge cases:** empty array, single element, all same elements, all negative.
4. **Dry run** your code with a small example before saying "done".
5. **State time & space complexity** at the end without being asked.

### Bonus problems to practice next
- Next Permutation
- Set Matrix Zeroes
- Spiral Matrix
- Find Minimum in Rotated Sorted Array
- Maximum Sum Circular Subarray
- Minimum Size Subarray Sum
- Longest Subarray with Sum K
- Kth Largest Element in an Array
- Top K Frequent Elements
- Merge Sorted Array
- Count Inversions
- Find All Duplicates in an Array

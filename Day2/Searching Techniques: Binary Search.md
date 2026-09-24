# Searching Techniques: Binary Search

## 1. Introduction to Binary Search

**Binary Search** is an efficient algorithm for finding an element in a **sorted list or array**.

Unlike Linear Search, which checks elements one by one sequentially, Binary Search uses the **Divide and Conquer** technique. It repeatedly divides the search interval in half until the target element is found or the search space becomes empty.

> **Prerequisite:** The input array **MUST** be sorted before performing Binary Search.

---

## 2. What is Binary Search?

Binary Search compares the target element (**key**) with the middle element of the array:

- If the key equals the middle element, the search is complete.
- If the key is **greater** than the middle element, search the **right half** (ignore the left half).
- If the key is **smaller** than the middle element, search the **left half** (ignore the right half).

By eliminating half of the remaining search space at every step, Binary Search achieves a logarithmic time complexity of $O(\log N)$.

---

## 3. Real-Life Analogy: Looking Up a Word in a Dictionary

Imagine searching for the word **"School"** in a dictionary.

```text
[ A - D ]  [ E - H ]  [ I - L ]  [ M - P ]  [ Q - T ]  [ U - Z ]
```

1. You open the dictionary near the middle (e.g., at words starting with **M**).
2. Since **"S"** comes after **"M"**, you discard the entire left half (**A–M**).
3. You open the middle of the remaining right half (**N–Z**).
4. You repeat this process until you land on the page for **"School"**.

You do **not** turn pages one by one from the letter A. That is the power of Binary Search.

---

## 4. Step-by-Step Visualization

Consider the following sorted array:

```text
Index:    0    1    2    3    4    5    6
Value:   10   20   30   40   50   60   70
```

### Problem
Search for `key = 60`.

---

### Step 1
Initialize pointers:
```text
low  = 0
high = 7 - 1 = 6
```

Calculate middle index:
$$\text{mid} = \left\lfloor \frac{0 + 6}{2} \right\rfloor = 3$$

Value at `mid` (index 3) is **40**.

Compare `key` with `arr[mid]`:
$$60 > 40 \quad (\text{True})$$

Since $60 > 40$, ignore the left half (`0` to `3`).

Update search range for the right half:
```text
low = mid + 1 = 4
```

---

### Step 2
Current range: `[50, 60, 70]` at indices `4` to `6`.

```text
low  = 4
high = 6
```

Calculate new middle index:
$$\text{mid} = \left\lfloor \frac{4 + 6}{2} \right\rfloor = 5$$

Value at `mid` (index 5) is **60**.

Compare `key` with `arr[mid]`:
$$60 == 60 \quad (\text{True})$$

**Result:** Element found at index `5`!

---

## 5. Binary Search Algorithm

### Algorithm Steps

1. **Make sure the array is sorted.**
2. Set `low = 0` and `high = length(arr) - 1`.
3. Loop while `low <= high`:
   - Calculate middle index: `mid = low + (high - low) // 2`.
   - Compare `arr[mid]` with `key`:
     - **If `arr[mid] == key`:** Target found, return `mid`.
     - **If `key > arr[mid]`:** Target is in the right half $\rightarrow$ set `low = mid + 1`.
     - **If `key < arr[mid]`:** Target is in the left half $\rightarrow$ set `high = mid - 1`.
4. If `low > high`, the element is not present in the array $\rightarrow$ return `-1`.

> **Note on Mid Calculation:**  
> Using `mid = low + (high - low) // 2` instead of `mid = (low + high) // 2` prevents potential integer overflow errors in languages like Java or C++ when dealing with very large indices.

---

## 6. Pseudocode

```text
function binarySearch(arr, key):
    low = 0
    high = length(arr) - 1

    while low <= high:
        mid = low + (high - low) / 2

        if arr[mid] == key:
            return mid
        else if key > arr[mid]:
            low = mid + 1
        else:
            high = mid - 1

    return -1
```

---

## 7. Python Implementation

```python
def binary_search(arr, key):
    low = 0
    high = len(arr) - 1

    while low <= high:
        # Calculate middle index safely
        mid = low + (high - low) // 2

        # Check if key is present at mid
        if arr[mid] == key:
            return mid

        # If key is greater, ignore left half
        elif key > arr[mid]:
            low = mid + 1

        # If key is smaller, ignore right half
        else:
            high = mid - 1

    # Element was not present in array
    return -1


# Sample Execution
numbers = [10, 20, 30, 40, 50, 60, 70]
key = 60

result = binary_search(numbers, key)

if result != -1:
    print("Element found at index:", result)
else:
    print("Element not found")
```

### Output

```text
Element found at index: 5
```

---

## 8. Java Implementation

```java
class BinarySearch {
    public static int binarySearch(int[] arr, int key) {
        int low = 0;
        int high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            // Check if key is present at mid
            if (arr[mid] == key) {
                return mid;
            }

            // If key is greater, ignore left half
            if (key > arr[mid]) {
                low = mid + 1;
            } 
            // If key is smaller, ignore right half
            else {
                high = mid - 1;
            }
        }

        // Element is not present
        return -1;
    }

    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50, 60, 70};
        int key = 60;

        int result = binarySearch(numbers, key);

        if (result != -1) {
            System.out.println("Element found at index: " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### Output

```text
Element found at index: 5
```

---

## 9. Complexity Analysis

| Case | Scenario | Time Complexity |
|---|---|---|
| **Best Case** | Key is located at the initial `mid` index. | $O(1)$ |
| **Worst Case** | Key is at either end or not present in the array. | $O(\log N)$ |
| **Average Case** | Key is found somewhere in the search space. | $O(\log N)$ |

**Space Complexity:**  
- **Iterative Approach:** $O(1)$ (constant space).
- **Recursive Approach:** $O(\log N)$ (due to recursion stack memory).

---

## 10. Linear Search vs Binary Search

| Feature | Linear Search | Binary Search |
|---|---|---|
| **Array Requirement** | Works on both sorted & unsorted arrays | Array **MUST** be sorted |
| **Approach** | Sequential (element-by-element) | Divide and Conquer |
| **Time Complexity** | $O(N)$ | $O(\log N)$ |
| **Speed / Efficiency** | Slower for large datasets | Significantly faster for large datasets |
| **Pointer Usage** | Single index loop | Uses `low`, `high`, and `mid` pointers |

---

## 11. Quick Revision

```text
Binary Search Steps:
Sorted Array ──► Set low = 0, high = N-1 ──► Calculate mid ──► Compare arr[mid] with key
                                                                     │
               ┌─────────────────────────────────────────────────────┼─────────────────────────────────────────────────────┐
               ▼                                                     ▼                                                     ▼
      arr[mid] == key                                         key > arr[mid]                                        key < arr[mid]
      [Element Found!]                                   [Search Right: low = mid + 1]                         [Search Left: high = mid - 1]
```

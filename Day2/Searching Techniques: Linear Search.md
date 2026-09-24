# Searching Techniques: Linear Search

## 1. Introduction to Searching

**Searching** is the process of finding the location of a specific element (called the **key**) within a collection of data, such as an array or a list.

Searching is one of the most fundamental operations in Data Structures and Algorithms. Common searching techniques include:

- **Linear Search** (Sequential Search)
- **Binary Search** (Divide and Conquer approach)

In this session, we focus on **Linear Search**.

---

## 2. What is Linear Search?

**Linear Search** is the simplest searching technique. It checks every element in a list one by one sequentially from the beginning to the end until the desired element is found or the list ends.

### Key Characteristics
- Works on both **sorted** and **unsorted** arrays.
- Does not require elements to be in any specific order.
- Checks elements sequentially ($O(N)$ time complexity).

---

## 3. Real-Life Analogy: Finding a Book

Imagine you are looking for a specific book on an **unorganized desk**:

```text
[ Book A ]  [ Book B ]  [ Book C ]  [ Book D ]  [ Book E ]
```

1. Look at the 1st book $\rightarrow$ Not the target.
2. Look at the 2nd book $\rightarrow$ Not the target.
3. Look at the 3rd book $\rightarrow$ **Target book found!** Stop searching.

Since the books are unsorted, you must inspect them one by one. This is exactly how Linear Search works.

---

## 4. Step-by-Step Visualization

Consider the following array of numbers:

```text
Index:     0      1      2      3      4
Value:   105    102    110    103    116
```

### Problem
Search for `key = 103`.

### Search Trace

```text
Step 1: Compare index 0 (105) with key (103)  → 105 == 103  (False)
Step 2: Compare index 1 (102) with key (103)  → 102 == 103  (False)
Step 3: Compare index 2 (110) with key (103)  → 110 == 103  (False)
Step 4: Compare index 3 (103) with key (103)  → 103 == 103  (True)  ✓ Found!
```

**Result:** Element found at index `3`.

---

## 5. Linear Search Algorithm

### Algorithm Steps

1. **Accept input array** `arr` and the target element `key`.
2. **Start iterating** from index `0` up to `len(arr) - 1`.
3. **Compare** current array element `arr[i]` with `key`.
4. If `arr[i] == key`:
   - Return current index `i` (or position) and exit loop.
5. If loop completes without finding the element:
   - Return `-1` indicating the element was not found.

---

## 6. Pseudocode

```text
function linearSearch(arr, key):
    for i from 0 to length(arr) - 1:
        if arr[i] == key:
            return i
    return -1
```

---

## 7. Python Implementation

```python
def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i
    return -1

# Sample Execution
arr = [105, 102, 110, 103, 116]
key = 103

result = linear_search(arr, key)

if result != -1:
    print("Element found at index =", result)
else:
    print("Element not found")
```

### Output

```text
Element found at index = 3
```

---

## 8. Java Implementation

```java
class LinearSearch {
    public static int linearSearch(int[] arr, int key) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == key) {
                return i; // Return index if key is found
            }
        }
        return -1; // Return -1 if key is not found
    }

    public static void main(String[] args) {
        int[] arr = {105, 102, 110, 103, 116};
        int key = 103;

        int result = linearSearch(arr, key);

        if (result != -1) {
            System.out.println("Element found at index = " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

### Output

```text
Element found at index = 3
```

---

## 9. Complexity Analysis

| Case | Scenario | Operations | Time Complexity |
|---|---|---|---|
| **Best Case** | Element is at the first position (`index 0`). | 1 comparison | $O(1)$ |
| **Worst Case** | Element is at the last position or not present. | $N$ comparisons | $O(N)$ |
| **Average Case** | Element is present somewhere in the middle. | $N/2$ comparisons | $O(N)$ |

**Space Complexity:** $O(1)$ (Auxiliary space, as no extra memory is allocated).

---

## 10. Summary & Key Takeaways

| Aspect | Linear Search |
|---|---|
| **Data Requirement** | Works on both sorted and unsorted data |
| **Search Pattern** | Sequential (element-by-element) |
| **Time Complexity** | $O(N)$ |
| **Space Complexity** | $O(1)$ |
| **Best Used For** | Small datasets, unsorted arrays |

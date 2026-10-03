# Recursion in Python — Basic to Advanced Notes

# 1. What is Recursion?

Recursion means:

A function calls itself to solve a smaller version of the same problem.

Example:

```python
def fun(n):
    if n == 0:
        return

    print(n)
    fun(n - 1)
````

Here:

```text
fun(3)
  ↓
fun(2)
  ↓
fun(1)
  ↓
fun(0)
```

---

# 2. Two Important Parts of Recursion

Every recursive function generally has two important parts:

1. Base Case
2. Recursive Case

Example:

```python
def fun(n):

    # Base Case
    if n == 0:
        return

    # Recursive Case
    print(n)
    fun(n - 1)
```

Base case:

```python
if n == 0:
    return
```

This stops recursion.

Recursive case:

```python
fun(n - 1)
```

This calls the function again with a smaller problem.

---

# 3. Why Do We Need a Base Case?

Without a base case, the function keeps calling itself forever.

Wrong:

```python
def fun(n):
    print(n)
    fun(n - 1)
```

There is no stopping condition.

Correct:

```python
def fun(n):

    if n == 0:
        return

    print(n)
    fun(n - 1)
```

---

# 4. Recursion Must Move Towards the Base Case

Example:

```python
fun(n - 1)
```

If:

```text
n = 5
```

then:

```text
5 → 4 → 3 → 2 → 1 → 0
```

The value is moving toward the base case.

If we write:

```python
fun(n + 1)
```

it moves away from the base case and can cause infinite recursion.

---

# 5. Call Stack

Python uses a call stack to keep track of function calls.

Example:

```python
def fun(n):

    if n == 0:
        return

    print(n)
    fun(n - 1)

fun(3)
```

Calls:

```text
fun(3)
fun(2)
fun(1)
fun(0)
```

The calls go DOWN first.

Then the functions finish in reverse order:

```text
fun(0)
fun(1)
fun(2)
fun(3)
```

---

# 6. Print Before Recursive Call

Example:

```python
def fun(n):

    if n == 0:
        return

    print(n)
    fun(n - 1)

fun(3)
```

Output:

```text
3
2
1
```

Because `print()` happens before the recursive call.

---

# 7. Print After Recursive Call

Example:

```python
def fun(n):

    if n == 0:
        return

    fun(n - 1)
    print(n)

fun(3)
```

Output:

```text
1
2
3
```

Important:

```text
Before recursive call → output while going DOWN

After recursive call → output while coming BACK
```

---

# 8. return vs print

`print()` displays something.

```python
print(10)
```

`return` sends a value back to the caller.

```python
return 10
```

Example:

```python
def fun(n):

    if n == 0:
        return

    print(n)
    fun(n - 1)
```

This prints values.

But:

```python
def sum_n(n):

    if n == 0:
        return 0

    return n + sum_n(n - 1)
```

This calculates and returns a value.

---

# 9. Print 1 to N

```python
def print_1_to_n(n):

    if n == 0:
        return

    print_1_to_n(n - 1)
    print(n)

print_1_to_n(5)
```

Output:

```text
1
2
3
4
5
```

---

# 10. Print N to 1

```python
def print_n_to_1(n):

    if n == 0:
        return

    print(n)
    print_n_to_1(n - 1)

print_n_to_1(5)
```

Output:

```text
5
4
3
2
1
```

---

# 11. Sum of N Numbers

Problem:

```text
1 + 2 + 3 + ... + N
```

Recursive idea:

```text
sum(5)
= 5 + sum(4)
= 5 + 4 + sum(3)
= 5 + 4 + 3 + sum(2)
= 5 + 4 + 3 + 2 + sum(1)
= 5 + 4 + 3 + 2 + 1 + sum(0)
```

Code:

```python
def sum_n(n):

    if n == 0:
        return 0

    return n + sum_n(n - 1)

print(sum_n(5))
```

Output:

```text
15
```

Time Complexity:

```text
O(n)
```

Space Complexity:

```text
O(n)
```

Because of the recursion call stack.

---

# 12. Factorial

Factorial:

```text
5! = 5 × 4 × 3 × 2 × 1
```

Recursive relationship:

```text
n! = n × (n - 1)!
```

Code:

```python
def factorial(n):

    if n == 0:
        return 1

    return n * factorial(n - 1)

print(factorial(5))
```

Output:

```text
120
```

Time Complexity:

```text
O(n)
```

Space Complexity:

```text
O(n)
```

---

# 13. Count Digits

Example:

```text
12345 → 5 digits
```

Important operation:

```python
n // 10
```

removes the last digit.

Example:

```text
12345 // 10 = 1234
1234 // 10 = 123
123 // 10 = 12
12 // 10 = 1
1 // 10 = 0
```

Code:

```python
def count_digits(n):

    if n == 0:
        return 0

    return 1 + count_digits(n // 10)

print(count_digits(12345))
```

Output:

```text
5
```

---

# 14. Sum of Digits

Example:

```text
12345

1 + 2 + 3 + 4 + 5 = 15
```

Get last digit:

```python
n % 10
```

Remove last digit:

```python
n // 10
```

Code:

```python
def sum_digits(n):

    if n == 0:
        return 0

    digit = n % 10

    return digit + sum_digits(n // 10)

print(sum_digits(12345))
```

Output:

```text
15
```

Time Complexity:

```text
O(d)
```

where `d` is the number of digits.

---

# 15. Product of Digits

Example:

```text
1234

1 × 2 × 3 × 4 = 24
```

Code:

```python
def product_digits(n):

    if n == 0:
        return 1

    digit = n % 10

    return digit * product_digits(n // 10)

print(product_digits(1234))
```

Output:

```text
24
```

---

# 16. Reverse a String Using Recursion

Example:

```text
hello → olleh
```

Code:

```python
def reverse_string(s):

    if len(s) <= 1:
        return s

    return reverse_string(s[1:]) + s[0]

print(reverse_string("hello"))
```

Output:

```text
olleh
```

Idea:

```text
hello
 ↓
ello + h
 ↓
llo + e
 ↓
lo + l
 ↓
o + l
 ↓
o
```

---

# 17. Palindrome Using Recursion

Palindrome means:

The string reads the same from both directions.

Examples:

```text
madam → Palindrome
racecar → Palindrome
hello → Not Palindrome
```

Code:

```python
def is_palindrome(s):

    if len(s) <= 1:
        return True

    if s[0] != s[-1]:
        return False

    return is_palindrome(s[1:-1])

print(is_palindrome("madam"))
```

Output:

```text
True
```

Main idea:

```text
Compare first and last character.

If different:
    False

If same:
    remove both
    check the remaining middle
```

Example:

```text
madam

m == m
 ↓
ada

a == a
 ↓
d

length = 1
 ↓
True
```

---

# 18. Reverse a Number

Example:

```text
12345 → 54321
```

Important operations:

```python
n % 10
```

Gets the last digit.

```python
n // 10
```

Removes the last digit.

Recursive code:

```python
def reverse_number(n, rev=0):

    if n == 0:
        return rev

    digit = n % 10

    rev = rev * 10 + digit

    return reverse_number(n // 10, rev)

print(reverse_number(12345))
```

Output:

```text
54321
```

Important formula:

```text
rev = rev * 10 + digit
```

This adds the new digit to the right side.

---

# 19. Recursion With Parameters

A recursive function can use additional parameters.

Example:

```python
def reverse_number(n, rev=0):
```

Here:

```text
n   → remaining number
rev → reversed number built so far
```

This is called using an accumulator.

Accumulator:

```text
A variable that stores the answer built so far.
```

---

# 20. Linear Recursion

When a function makes only one recursive call.

Example:

```python
def fun(n):

    if n == 0:
        return

    fun(n - 1)
```

There is only one path:

```text
n
↓
n-1
↓
n-2
↓
...
↓
0
```

Usually:

```text
Time = O(n)
Space = O(n)
```

---

# 21. Multiple Recursive Calls

Example:

```python
def fun(n):

    if n == 0:
        return

    fun(n - 1)
    fun(n - 1)
```

Each function call creates two more calls.

For example:

```text
fun(3)
       /    \
    fun(2)  fun(2)
     / \      / \
  fun1 fun1 fun1 fun1
```

The number of calls grows very quickly.

This type of recursion is called branching recursion.

---

# 22. Fibonacci Recursion

Fibonacci sequence:

```text
0 1 1 2 3 5 8 13 ...
```

Relationship:

```text
F(n) = F(n-1) + F(n-2)
```

Code:

```python
def fibonacci(n):

    if n <= 1:
        return n

    return fibonacci(n - 1) + fibonacci(n - 2)
```

Example:

```python
print(fibonacci(5))
```

Output:

```text
5
```

Naive recursive Fibonacci has:

```text
Time Complexity = O(2^n)
Space Complexity = O(n)
```

because many calculations are repeated.

---

# 23. Recursion Tree

For:

```python
fibonacci(4)
```

The calls look approximately like:

```text
                 fib(4)
                /      \
            fib(3)     fib(2)
           /    \      /   \
       fib(2) fib(1) fib(1) fib(0)
       /   \
   fib(1) fib(0)
```

This is called a recursion tree.

It helps us understand:

```text
Number of calls
Repeated work
Time complexity
```

---

# 24. Recursion and Backtracking

Backtracking is a more advanced form of recursion.

Basic idea:

```text
Choose
 ↓
Explore
 ↓
Undo
 ↓
Try another choice
```

Example problems:

```text
Subsets
Permutations
N-Queens
Sudoku
Maze
Combination Sum
```

---

# 25. Example: Generate Subsets

For:

```text
[1, 2]
```

Possible subsets:

```text
[]
[1]
[2]
[1, 2]
```

At every element we have two choices:

```text
Take it
OR
Don't take it
```

Recursion tree:

```text
                 []
               /    \
            take     don't take
             1          |
            [1]         []
           /  \        /  \
        take  don't  take  don't
         2      2     2      2
```

---

# 26. Backtracking Pattern

Common pattern:

```python
def backtrack(...):

    if base_condition:
        # store answer
        return

    # Choose

    # Explore
    backtrack(...)

    # Undo choice
```

The important part is:

```text
Choose → Explore → Undo
```

---

# 27. Recursion With Arrays

Recursion can process arrays using an index.

Example:

```python
def print_array(arr, index):

    if index == len(arr):
        return

    print(arr[index])

    print_array(arr, index + 1)

arr = [10, 20, 30, 40]

print_array(arr, 0)
```

Output:

```text
10
20
30
40
```

---

# 28. Recursive Array Sum

```python
def array_sum(arr, index):

    if index == len(arr):
        return 0

    return arr[index] + array_sum(arr, index + 1)

arr = [10, 20, 30]

print(array_sum(arr, 0))
```

Output:

```text
60
```

Time:

```text
O(n)
```

Space:

```text
O(n)
```

---

# 29. Recursive Binary Search

Binary search repeatedly divides the search space into half.

Example:

```text
[10, 20, 30, 40, 50, 60, 70]
```

Instead of checking every element:

```text
Check middle
 ↓
Go left OR right
 ↓
Check middle again
```

Recursive structure:

```python
def binary_search(arr, low, high, target):

    if low > high:
        return -1

    mid = (low + high) // 2

    if arr[mid] == target:
        return mid

    if target < arr[mid]:
        return binary_search(arr, low, mid - 1, target)

    return binary_search(arr, mid + 1, high, target)
```

Time Complexity:

```text
O(log n)
```

Space Complexity:

```text
O(log n)
```

because of recursive calls.

---

# 30. Divide and Conquer

Divide and conquer is an important use of recursion.

Three steps:

```text
1. Divide
2. Solve
3. Combine
```

Examples:

```text
Merge Sort
Quick Sort
Binary Search
```

---

# 31. Merge Sort

Merge Sort:

```text
Divide array into two halves
        ↓
Recursively sort both halves
        ↓
Merge them
```

Example:

```text
[38, 27, 43, 3]

        ↓

[38, 27]    [43, 3]

    ↓           ↓

[38] [27]    [43] [3]

        ↓

[27, 38]    [3, 43]

        ↓

[3, 27, 38, 43]
```

Time Complexity:

```text
O(n log n)
```

Typical extra space:

```text
O(n)
```

---

# 32. Recursion in Trees

Trees naturally use recursion.

Example:

```python
def preorder(root):

    if root is None:
        return

    print(root.value)

    preorder(root.left)
    preorder(root.right)
```

Tree traversal types:

```text
Preorder
Inorder
Postorder
```

---

# 33. Tree Traversal Order

### Preorder

```text
Root → Left → Right
```

### Inorder

```text
Left → Root → Right
```

### Postorder

```text
Left → Right → Root
```

These are usually implemented using recursion.

---

# 34. Recursion and Dynamic Programming

Some recursive problems repeat the same calculations.

Example:

```python
fibonacci(n)
```

Naive recursion calculates the same values many times.

Dynamic Programming can store already calculated results.

Two common approaches:

```text
Memoization
Tabulation
```

Memoization:

```text
Top-down
Recursion + cache
```

Tabulation:

```text
Bottom-up
Usually iterative
```

---

# 35. Important Recursion Complexity Rule

For simple recursion:

```python
fun(n - 1)
```

usually:

```text
Time = O(n)
```

For recursion that divides the problem by 2:

```python
fun(n // 2)
```

usually:

```text
Time = O(log n)
```

For two recursive calls:

```python
fun(n - 1)
fun(n - 1)
```

the number of calls can grow exponentially.

Often:

```text
Time = O(2^n)
```

---

# 36. Recursion Space Complexity

Always remember:

Recursive calls use the call stack.

Example:

```python
fun(5)
```

creates:

```text
fun(5)
fun(4)
fun(3)
fun(2)
fun(1)
fun(0)
```

Maximum stack depth:

```text
O(n)
```

Therefore even if the algorithm doesn't create an extra array:

```text
Recursive Space = O(n)
```

---

# 37. Important Recursion Interview Patterns

You should be comfortable with:

```text
1. Print 1 to N
2. Print N to 1
3. Sum of N numbers
4. Factorial
5. Count digits
6. Sum of digits
7. Product of digits
8. Reverse string
9. Reverse number
10. Palindrome
11. Array traversal
12. Array sum
13. Maximum element recursively
14. Binary search
15. Fibonacci
16. Power
17. Multiple recursion
18. Recursion tree
19. Subsets
20. Permutations
21. Backtracking
22. Merge sort
23. Quick sort
24. Tree traversal
25. Dynamic programming
```

---

# 38. How to Solve Any Recursion Problem

Use this checklist:

```text
Step 1 → What is the smallest problem?

Step 2 → What is the base case?

Step 3 → How can I make the problem smaller?

Step 4 → What should the recursive call receive?

Step 5 → What should I return?

Step 6 → What happens while going DOWN?

Step 7 → What happens while coming BACK?

Step 8 → What is the time complexity?

Step 9 → What is the recursion stack space?
```

---

# 39. Most Important Mental Model

When you see:

```python
return something + fun(n - 1)
```

think:

```text
GO DOWN
   ↓
GO DOWN
   ↓
GO DOWN
   ↓
BASE CASE
   ↓
COME BACK
   ↓
CALCULATE
   ↓
RETURN
```

When you see:

```python
print(n)
fun(n - 1)
```

think:

```text
PRINT while going DOWN
```

When you see:

```python
fun(n - 1)
print(n)
```

think:

```text
PRINT while coming BACK
```

When you see:

```python
return False
```

think:

```text
STOP FUNCTION IMMEDIATELY
```

---

# 40. Recursion Learning Roadmap

```text
LEVEL 1
↓
What is recursion?
Base case
Recursive case
Function calling itself

        ↓

LEVEL 2
↓
Call stack
Going down
Coming back
Print before/after recursion
return vs print

        ↓

LEVEL 3
↓
Sum
Factorial
Count digits
Sum digits
Product digits
Reverse string
Palindrome
Reverse number

        ↓

LEVEL 4
↓
Arrays
Strings
Index-based recursion
Multiple recursive calls
Recursion trees

        ↓

LEVEL 5
↓
Fibonacci
Binary Search
Divide and Conquer
Merge Sort
Quick Sort

        ↓

LEVEL 6
↓
Backtracking
Subsets
Permutations
Combination problems
N-Queens
Maze

        ↓

LEVEL 7
↓
Trees
Tree Traversals
Dynamic Programming
Memoization
Advanced recursion problems
```

# Final Recursion Cheat Sheet

```text
Recursion = Function calls itself

Base Case = Stops recursion

Recursive Case = Calls itself with smaller problem

Going Down = Recursive calls are being created

Coming Back = Calls finish and return

print before recursion = Output while going down

print after recursion = Output while coming back

return = Sends value back and exits function

n - 1 = Usually reduces problem by 1

n // 2 = Reduces problem by half

One recursive call = Often O(n)

Half-sized recursive call = Often O(log n)

Two recursive calls = Can become O(2^n)

Recursive stack = Must be included in space complexity

Backtracking = Choose → Explore → Undo

Divide & Conquer = Divide → Solve → Combine

Memoization = Recursion + Cache
```

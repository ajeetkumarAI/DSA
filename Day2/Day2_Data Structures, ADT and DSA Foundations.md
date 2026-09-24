# Day 2 --- Data Structures, ADT and DSA Foundations

## 1. DSA Roadmap

The major topics we will cover in DSA are:

1.  Introduction to DSA
2.  Searching
    -   Linear Search
    -   Binary Search
3.  Sorting
4.  Stack
5.  Queue
6.  Linked List
7.  Tree
8.  Graph
9.  Time and Space Complexity

------------------------------------------------------------------------

# 2. What is a Data Structure?

A **Data Structure** is a way of organizing and storing data so that we
can access and process it efficiently.

Different problems require different ways of organizing data.

### Examples

-   Array → Store elements using indexes
-   Stack → Store elements using LIFO
-   Queue → Store elements using FIFO
-   Linked List → Store connected elements
-   Tree → Store hierarchical data
-   Graph → Store interconnected data

------------------------------------------------------------------------

# 3. Types of Data Structures

Data structures can broadly be divided into:

``` text
Data Structures
│
├── Linear
│   ├── Array
│   ├── Stack
│   ├── Queue
│   └── Linked List
│
└── Non-Linear
    ├── Tree
    └── Graph
```

------------------------------------------------------------------------

# 4. Linear Data Structures

In a **linear data structure**, elements are arranged sequentially.

Examples:

-   Array
-   Stack
-   Queue
-   Linked List

------------------------------------------------------------------------

# 5. Non-Linear Data Structures

In a **non-linear data structure**, elements are organized in
hierarchical or interconnected relationships.

Examples:

-   Tree
-   Graph

------------------------------------------------------------------------

# 6. Array

An **Array** is a collection of elements stored using indexes.

In Java, an array generally stores elements of the same data type and
has a fixed size.

### Example

``` java
int[] numbers = {3, 4, 6, 7, 9};
```

Another example:

``` java
double[] numbers = {3.4, 4.6, 6.5, 7.5, 9.4};
```

### Real-Life Example

Imagine a classroom with student roll numbers:

``` text
Roll Number
0 → 101
1 → 102
2 → 103
3 → 104
4 → 105
```

Each element can be accessed using its index.

``` java
numbers[0]
numbers[1]
numbers[2]
```

### Important Features of Array

-   Elements are accessed using an index.
-   In Java, arrays have a fixed/static size.
-   Java arrays generally contain elements of the same data type.
-   Indexing starts from `0`.

------------------------------------------------------------------------

# 7. Array Size

In Java, the size of an array is fixed when the array is created.

### Example

``` java
int[] arr = new int[5];
```

This creates an array that can store 5 integers.

``` text
Index:   0   1   2   3   4
         ↓   ↓   ↓   ↓   ↓
Array:  [ ] [ ] [ ] [ ] [ ]
```

Another way to create an array is:

``` java
int[] arr = {10, 20, 30, 40, 50};
```

------------------------------------------------------------------------

# 8. Stack

A **Stack** follows:

``` text
LIFO
Last In → First Out
```

The element added last is removed first.

### Real-Life Example --- Stack of Plates

``` text
    Plate 3  ← Remove First
    Plate 2
    Plate 1
```

### Main Operations

#### Push

Adds an element to the top.

``` text
push(10)
push(20)
push(30)
```

Stack:

``` text
30 ← Top
20
10
```

#### Pop

Removes the top element.

``` text
pop()
```

Result:

``` text
30 removed
```

### Real-Life Applications

-   Undo operation
-   Browser back operation
-   Function call management
-   Expression processing

------------------------------------------------------------------------

# 9. Queue

A **Queue** follows:

``` text
FIFO
First In → First Out
```

The element that enters first is removed first.

### Real-Life Example --- Bank Counter

``` text
Person 1 → Person 2 → Person 3 → Person 4
   ↓
Served First
```

### Main Operations

#### Enqueue

Adds an element to the rear of the queue.

#### Dequeue

Removes an element from the front of the queue.

### Applications

-   Bank/ticket counter
-   Printer queue
-   Call center waiting system
-   Task scheduling

------------------------------------------------------------------------

# 10. Linked List

A **Linked List** stores elements as connected nodes.

Each node generally contains:

``` text
Data + Link to Next Node
```

Example:

``` text
10 → 20 → 30 → 40 → NULL
```

### Important Characteristics

-   Elements are connected to each other.
-   Size can grow or shrink dynamically.
-   Insertion and deletion can be performed without shifting all
    elements as in an array.

### Java Collection Framework Examples

Java provides several collection classes such as:

-   `ArrayList`
-   `LinkedList`
-   `Vector`
-   `Stack`

These classes provide different ways of storing and managing collections
of data.

------------------------------------------------------------------------

# 11. Tree

A **Tree** is a non-linear data structure used to represent hierarchical
relationships.

### Real-Life Examples

-   Family tree
-   Folder and subfolder structure
-   Organization hierarchy

Example:

``` text
          CEO
         /   \
      Manager Manager
       /  \
    Team  Team
```

------------------------------------------------------------------------

# 12. Graph

A **Graph** is a non-linear data structure used to represent
relationships between multiple objects or points.

### Real-Life Examples

-   Google Maps
-   Social networks
-   GPS navigation
-   Flight routes

Example:

``` text
A ─── B
│   / │
│  /  │
C ─── D
```

The objects are represented as **vertices/nodes**, and their connections
are represented as **edges**.

------------------------------------------------------------------------

# 13. Data Type

A **Data Type** defines what type of value a variable can store.

It helps determine:

-   What kind of data can be stored
-   How the data is represented in memory
-   What operations can be performed on the data

### Real-Life Analogy

Think about different containers:

-   Water bottle → designed to store water
-   Lunch box → designed to store food
-   Pen drive → designed to store digital data

Similarly, a data type tells the programming language what kind of data
a variable is intended to hold.

------------------------------------------------------------------------

# 14. Primitive Data Types

Common Java primitive data types include:

``` text
int
float
double
char
boolean
short
long
```

### Examples

``` java
int age = 25;

double salary = 50000.50;

char grade = 'A';

boolean isActive = true;
```

------------------------------------------------------------------------

# 15. Non-Primitive Data Types

Examples include:

``` text
Array
String
Class
Interface
```

### Example --- Employee Class

``` java
class Employee {
    int id;
    String name;
}
```

Here, `Employee` is a user-defined class.

------------------------------------------------------------------------

# 16. What is ADT?

**ADT = Abstract Data Type**

An ADT is a **logical model of a data structure**.

It defines:

-   What data structure represents
-   What operations can be performed
-   What behavior the operations should provide

It does **not** focus on the internal implementation details.

### Simple Example

A Stack ADT defines operations such as:

``` text
push()
pop()
peek()
```

The ADT tells us **what operations are available**.

The implementation determines **how those operations are performed
internally**.

------------------------------------------------------------------------

# 17. ADT in Java

Java provides interfaces that define operations, while concrete classes
provide implementations.

Examples from the Java Collection Framework include:

``` text
List
Map
Set
Iterator
Queue
```

For example:

``` java
List<Integer> list = new ArrayList<>();
```

Here:

-   `List` → interface / abstraction
-   `ArrayList` → concrete implementation

The interface defines the available behavior, while `ArrayList` provides
the implementation.

------------------------------------------------------------------------

# 18. ADT Example --- Stack

A Stack ADT can define:

``` text
push()
pop()
peek()
isEmpty()
```

Different implementations can provide these operations internally.

The important point is:

``` text
ADT → What operations are supported?
Implementation → How are those operations performed?
```

------------------------------------------------------------------------

# 19. Python Examples of Common Data Structures

Python provides built-in structures that can be used to implement common
data structures.

### List

A Python `list` can be used as a dynamic array.

``` python
numbers = [10, 20, 30, 40]
```

### Stack Using List

``` python
stack = []

stack.append(10)
stack.append(20)
stack.append(30)

stack.pop()
```

The last inserted element is removed first.

### Dictionary

A Python `dict` can be used to store key-value mappings.

``` python
employee = {
    "id": 101,
    "name": "Ajeet"
}
```

------------------------------------------------------------------------

# 20. Data Type vs ADT

  -----------------------------------------------------------------------
  Data Type                           ADT
  ----------------------------------- -----------------------------------
  Defines the type of value           Defines a logical data structure

  Focuses on data representation/type Focuses on behavior and operations

  Examples: `int`, `float`, `char`    Examples: Stack, Queue, List, Map

  Usually provided by the language    Usually implemented using
                                      classes/data structures

  Describes what kind of value can be Describes what operations can be
  stored                              performed
  -----------------------------------------------------------------------

### Simple Difference

``` text
Data Type
    ↓
What type of value?

ADT
    ↓
What operations and behavior?
```

------------------------------------------------------------------------

# 21. Data Structure vs Algorithm

These two concepts work together.

### Data Structure

Defines **how data is organized**.

Example:

``` text
Array
Stack
Queue
Tree
Graph
```

### Algorithm

Defines **how we solve a problem using the data**.

Example:

``` text
Search
Sort
Find Maximum
Find Minimum
Traverse
```

### Together

``` text
Data Structure + Algorithm
            ↓
       Problem Solving
```

------------------------------------------------------------------------

# 22. Why Do We Need Different Data Structures?

Different problems require different ways of organizing data.

For example:

### Need Last-In-First-Out?

Use:

``` text
Stack
```

### Need First-In-First-Out?

Use:

``` text
Queue
```

### Need Hierarchical Data?

Use:

``` text
Tree
```

### Need Network/Relationships?

Use:

``` text
Graph
```

### Need Index-Based Access?

Use:

``` text
Array
```

------------------------------------------------------------------------

# 23. Day 2 Key Takeaways

By the end of Day 2, you should understand:

-   What a Data Structure is
-   Linear vs Non-Linear Data Structures
-   Array
-   Stack
-   Queue
-   Linked List
-   Tree
-   Graph
-   Data Types
-   Primitive and Non-Primitive Data Types
-   Abstract Data Type (ADT)
-   Data Type vs ADT
-   Data Structure vs Algorithm
-   Basic Java Collection Framework interfaces/classes
-   Basic Python data structures

------------------------------------------------------------------------

# 24. Quick Revision

### DSA

``` text
DSA = Data Structure + Algorithm
```

### Linear

``` text
Array
Stack
Queue
Linked List
```

### Non-Linear

``` text
Tree
Graph
```

### Stack

``` text
LIFO
Last In → First Out
```

### Queue

``` text
FIFO
First In → First Out
```

### ADT

``` text
Defines WHAT operations are supported,
not HOW they are implemented.
```

### Final Concept

``` text
Data Structure
      +
Algorithm
      ↓
Problem Solving
```

# 🔗 Linked Lists in Python 

This guide explains **Linked Lists from beginner to advanced level** in
Python.

It includes: - Concept explanation - Memory structure - Types of linked
lists - All major operations - Algorithms - Time complexity - Real‑world
applications - Robotics use cases - Full Python implementations

------------------------------------------------------------------------

# 1. What is a Linked List?

A **Linked List** is a **linear data structure** where elements are
stored in **nodes**.

Each node contains:

1.  **Data**
2.  **Pointer (reference) to the next node**

Example:

    10 → 20 → 30 → 40 → None

Unlike Python lists, linked list elements are **not stored in contiguous
memory**.

------------------------------------------------------------------------

# 2. Why Linked Lists Exist

Arrays (Python lists) have limitations:


  Problem               Example

  --------------------- ------------------------

  Insertion expensive   inserting at index 0

  Memory resizing       dynamic array resizing

  Shifting elements     many elements moved


Linked lists solve these problems by storing **references instead of
contiguous memory**.

------------------------------------------------------------------------

# 3. Linked List vs Python List

  Feature           Python List   Linked List

  ----------------- ------------- -------------

  Memory layout     contiguous    scattered

  Random access     O(1)          O(n)

  Insertion start   O(n)          O(1)

  Deletion start    O(n)          O(1)

  Memory usage      lower         higher


------------------------------------------------------------------------

# 4. Node Structure

Each node has two parts:

    Node

     ├── data

     └── next pointer


### Python Implementation

``` python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

Explanation:

`data` → value stored\
`next` → pointer to next node

------------------------------------------------------------------------

# 5. Linked List Class

``` python
class LinkedList:

    def __init__(self):
        self.head = None
```

The **head** stores the first node.

    head → 10 → 20 → 30 → None

------------------------------------------------------------------------

# 6. Insertion Operations

## Insert at Beginning

### Logic

1.  Create new node
2.  Point new node next to head
3.  Move head

### Code

``` python
def insert_beginning(self, data):

    new_node = Node(data)
    new_node.next = self.head
    self.head = new_node
```

Time Complexity:

    O(1)

------------------------------------------------------------------------

## Insert at End

``` python
def insert_end(self, data):

    new_node = Node(data)

    if not self.head:
        self.head = new_node
        return

    current = self.head

    while current.next:
        current = current.next

    current.next = new_node
```

Time Complexity

    O(n)

------------------------------------------------------------------------

## Insert at Position

``` python
def insert_position(self, position, data):

    new_node = Node(data)

    if position == 0:
        new_node.next = self.head
        self.head = new_node
        return

    current = self.head

    for i in range(position - 1):
        current = current.next

    new_node.next = current.next
    current.next = new_node
```

------------------------------------------------------------------------

# 7. Traversal

Traversal means visiting each node.

``` python
def display(self):

    current = self.head

    while current:
        print(current.data, end=" -> ")
        current = current.next

    print("None")
```

Example output

    10 → 20 → 30 → None

------------------------------------------------------------------------

# 8. Searching

``` python
def search(self, key):

    current = self.head

    while current:
        if current.data == key:
            return True
        current = current.next

    return False
```

Time complexity

    O(n)

------------------------------------------------------------------------

# 9. Deletion Operations

## Delete Beginning

``` python
def delete_beginning(self):

    if self.head:
        self.head = self.head.next
```

------------------------------------------------------------------------

## Delete End

``` python
def delete_end(self):

    if not self.head:
        return

    if not self.head.next:
        self.head = None
        return

    current = self.head

    while current.next.next:
        current = current.next

    current.next = None
```

------------------------------------------------------------------------

## Delete By Value

``` python
def delete_value(self, value):

    if self.head.data == value:
        self.head = self.head.next
        return

    current = self.head

    while current.next:

        if current.next.data == value:
            current.next = current.next.next
            return

        current = current.next
```

------------------------------------------------------------------------

# 10. Reverse Linked List

Very common interview problem.

Example

Before

    10 → 20 → 30

After

    30 → 20 → 10

Code

``` python
def reverse(self):

    prev = None
    current = self.head

    while current:

        next_node = current.next
        current.next = prev

        prev = current
        current = next_node

    self.head = prev
```

------------------------------------------------------------------------

# 11. Types of Linked Lists

## Singly Linked List

    10 → 20 → 30 → None

------------------------------------------------------------------------

## Doubly Linked List

Each node has:

    prev ← data → next

Example

    None ← 10 ↔ 20 ↔ 30 → None

------------------------------------------------------------------------

## Circular Linked List

Last node points to first node.

    10 → 20 → 30

     ↑        ↓

     └────────┘


------------------------------------------------------------------------

# 12. Memory Representation

Example memory layout

    Address   Data   Next

    1000      10     2000

    2000      20     3000

    3000      30     None


------------------------------------------------------------------------

# 13. Time Complexity

  Operation          Complexity

  ------------------ ------------

  Insert beginning   O(1)

  Insert end         O(n)

  Search             O(n)

  Delete             O(n)
  
  Traversal          O(n)
  

------------------------------------------------------------------------

# 14. Real‑World Applications

Linked lists appear in many systems.

### Music playlist

    Song1 → Song2 → Song3

### Browser navigation

Back / Forward history.

### Operating system memory management

Dynamic allocation using linked blocks.

------------------------------------------------------------------------

# 15. Robotics Applications 🤖

Linked lists can help robotics systems manage:

### Robot Task Sequences

Example:

    Move forward → Turn left → Pick object → Drop object

Each action stored as node.

### Motion Planning Steps

Robots break complex movements into sequential commands.

### Sensor Data Logs

Sensors continuously generate readings.

Linked lists allow dynamic storage.

------------------------------------------------------------------------

# 16. Full Python Example

``` python
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None


class LinkedList:

    def __init__(self):
        self.head = None


    def insert_end(self, data):

        new_node = Node(data)

        if not self.head:
            self.head = new_node
            return

        current = self.head

        while current.next:
            current = current.next

        current.next = new_node


    def display(self):

        current = self.head

        while current:
            print(current.data, end=" -> ")
            current = current.next

        print("None")
```

Usage

``` python
ll = LinkedList()

ll.insert_end(10)
ll.insert_end(20)
ll.insert_end(30)

ll.display()
```

Output

    10 → 20 → 30 → None

------------------------------------------------------------------------

# 17. Key Concepts Summary

-   Node
-   Pointer
-   Head
-   Traversal
-   Insertion
-   Deletion
-   Reverse
-   Types of linked lists

Mastering linked lists builds the foundation for:

-   trees
-   graphs
-   advanced algorithms

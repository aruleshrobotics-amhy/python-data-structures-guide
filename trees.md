# 🌳 Trees Data Structure --- Beginner to Advanced Guide (Python)

This guide covers **Trees from A → Z** including:

-   Tree fundamentals
-   Tree terminology
-   Binary Trees
-   Binary Search Trees (BST)
-   Tree traversals
-   Tree algorithms
-   Balanced trees (AVL)
-   Heap trees
-   Tries
-   Real-world systems
-   Robotics applications 🤖
-   Python demos

------------------------------------------------------------------------

# 1. What is a Tree?

A **Tree** is a hierarchical data structure made of **nodes connected by
edges**.

Example:

            A

           / \

          B   C

         / \

        D   E

Here:

-   A → root
-   B,C → children of A
-   D,E → children of B

Trees organize information **hierarchically**.

------------------------------------------------------------------------

# 2. Tree Terminology

  Term      Meaning

  --------- --------------------------

  Root      top node

  Parent    node with children

  Child     node under a parent

  Leaf      node with no children

  Edge      connection between nodes

  Depth     distance from root

  Height    longest path to leaf

  Subtree   smaller tree within tree


Example:

            A

           / \

          B   C

         /

        D

Root = A\
Leaf nodes = C, D

------------------------------------------------------------------------

# 3. Tree Representation in Python

Basic node structure:

``` python
class Node:

    def __init__(self,data):
        self.data = data
        self.left = None
        self.right = None
```

------------------------------------------------------------------------

# 4. Binary Tree

A **Binary Tree** allows maximum **two children per node**.

           A

          / \

         B   C

        / \   \

       D   E   F

Left child\
Right child

------------------------------------------------------------------------

# 5. Binary Search Tree (BST)

A BST keeps nodes **sorted**.

Rule:

    Left subtree < Root < Right subtree

Example:

            50

           /  \

         30    70

        /  \   /

       20  40 60

------------------------------------------------------------------------

# 6. Insert in BST

``` python
class Node:

    def __init__(self,value):
        self.value = value
        self.left = None
        self.right = None


def insert(root,value):

    if root is None:
        return Node(value)

    if value < root.value:
        root.left = insert(root.left,value)
    else:
        root.right = insert(root.right,value)

    return root
```

------------------------------------------------------------------------

# 7. Search in BST

``` python
def search(root,key):

    if root is None or root.value == key:
        return root

    if key < root.value:
        return search(root.left,key)

    return search(root.right,key)
```

------------------------------------------------------------------------

# 8. Tree Traversals

Traversal means **visiting every node**.

## Inorder (Left → Root → Right)

``` python
def inorder(root):

    if root:
        inorder(root.left)
        print(root.value)
        inorder(root.right)
```

Output from BST is **sorted**.

------------------------------------------------------------------------

## Preorder (Root → Left → Right)

``` python
def preorder(root):

    if root:
        print(root.value)
        preorder(root.left)
        preorder(root.right)
```

Used for **tree copying**.

------------------------------------------------------------------------

## Postorder (Left → Right → Root)

``` python
def postorder(root):

    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.value)
```

Used for **deleting trees**.

------------------------------------------------------------------------

# 9. Tree Height

Example:

            A

           / \

          B   C

         /

        D

Height = 3

Python demo:

``` python
def height(root):

    if root is None:
        return 0

    return 1 + max(height(root.left), height(root.right))
```

------------------------------------------------------------------------

# 10. Breadth First Traversal (Level Order)

Uses a **queue**.

``` python
from collections import deque

def level_order(root):

    if root is None:
        return

    queue = deque([root])

    while queue:

        node = queue.popleft()
        print(node.value)

        if node.left:
            queue.append(node.left)

        if node.right:
            queue.append(node.right)
```

------------------------------------------------------------------------

# 11. Deleting in BST

Three cases:

### Case 1: Leaf node

Simply remove.

### Case 2: One child

Replace with child.

### Case 3: Two children

Replace with **inorder successor**.

------------------------------------------------------------------------

# 12. Balanced Trees

If BST becomes skewed:

    10

     \

      20

       \

        30

Search becomes **O(n)**.

Balanced trees maintain height near **log n**.

------------------------------------------------------------------------

# 13. AVL Trees

AVL tree maintains **balance factor**:

    balance = height(left) - height(right)

Allowed values:

    -1, 0, 1

Rotations fix imbalance.

Types:

-   Left Rotation
-   Right Rotation
-   Left-Right Rotation
-   Right-Left Rotation

------------------------------------------------------------------------

# 14. Heap Trees

Heap is a **complete binary tree** used for priority queues.

## Min Heap

Smallest value on top.

           10

          /  \

        20    30

       /

     40

Python example:

``` python
import heapq

heap = []

heapq.heappush(heap,10)
heapq.heappush(heap,5)
heapq.heappush(heap,20)

print(heapq.heappop(heap))
```

------------------------------------------------------------------------

# 15. Trie Trees

Trie stores **strings efficiently**.

Example:

    cat
    car
    dog

Structure:

       c

       |

       a

      / \

     t   r


Used in:

-   autocomplete
-   dictionaries
-   spell checkers

------------------------------------------------------------------------

# 16. Tree Algorithms

Trees support many algorithms:

### DFS

Depth-first search explores deep branches.

### BFS

Breadth-first search explores level by level.

------------------------------------------------------------------------

# 17. Real World Applications

Trees are everywhere.

  System           Tree Type

  ---------------- -----------------

  File systems     directory trees

  Databases        B-trees

  Compilers        syntax trees

  AI models        decision trees

  Search engines   index trees


------------------------------------------------------------------------

# 18. Trees in Robotics 🤖

Trees are critical in robotics.

### Path Planning

Algorithms:

-   RRT (Rapidly Exploring Random Trees)
-   A\* search

Example:

    Start

     /   \

    Path1 Path2


------------------------------------------------------------------------

### Decision Trees

Robot decisions:

    Obstacle?

       |

    Yes → Turn

    No  → Move

------------------------------------------------------------------------

### Motion Planning

Robot explores movement tree:

    Move

    ├─ Turn Left

    ├─ Turn Right

------------------------------------------------------------------------

# 19. Complexity (BST)

  Operation   Average    Worst

  ----------- ---------- -------

  Search      O(log n)   O(n)

  Insert      O(log n)   O(n)

  Delete      O(log n)   O(n)
  

Balanced trees keep complexity **O(log n)**.

------------------------------------------------------------------------

# 20. Complete Demo Program

``` python
class Node:

    def __init__(self,value):
        self.value=value
        self.left=None
        self.right=None


def insert(root,value):

    if root is None:
        return Node(value)

    if value < root.value:
        root.left = insert(root.left,value)
    else:
        root.right = insert(root.right,value)

    return root


def inorder(root):

    if root:
        inorder(root.left)
        print(root.value)
        inorder(root.right)


root=None

root=insert(root,50)
root=insert(root,30)
root=insert(root,70)
root=insert(root,20)
root=insert(root,40)
root=insert(root,60)

inorder(root)
```

Output

    20
    30
    40
    50
    60
    70

------------------------------------------------------------------------

# 🚀 Summary

Trees are powerful hierarchical data structures used in:

-   databases
-   operating systems
-   compilers
-   AI
-   robotics
-   networking

Learning trees prepares you for **graphs, advanced algorithms, and AI
systems**.

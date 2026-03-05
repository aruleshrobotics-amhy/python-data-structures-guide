# 📚 Stack Data Structure

This guide explains **Stacks** from beginner to advanced level with:

-   Concept explanation
-   Internal structure
-   All stack operations
-   Python implementations
-   Algorithms using stacks
-   Time complexity analysis
-   Real‑world applications
-   Robotics applications
-   Full Python programs

------------------------------------------------------------------------

# 1. What is a Stack?

A **Stack** is a **linear data structure** that follows the rule:

**LIFO --- Last In First Out**

This means:

The **last element inserted** is the **first element removed**.

Example:

    Top

    30

    20

    10


If we remove an element:

    Top

    20

    10


------------------------------------------------------------------------

# 2. Real‑World Example

## Stack of Plates

    Top

    Plate3

    Plate2

    Plate1


Rules:

-   Add plate → **Push**
-   Remove plate → **Pop**

You always remove the **top plate first**.

------------------------------------------------------------------------

# 3. Stack Terminology

  Term         Meaning

  ------------ ----------------------

  Push         Insert element

  Pop          Remove top element

  Peek / Top   View top element

  isEmpty      Check if stack empty

  Size         Number of elements


------------------------------------------------------------------------

# 4. Stack Structure

A stack has **one accessible end** called the **Top**.

    Top

    30

    20

    10


Elements are added and removed only from the **top**.

------------------------------------------------------------------------

# 5. Basic Stack Operations

## Push

Insert element at the top.

Example:

    Stack before

    Top

    20

    10


    push(30)

    Stack after

    Top

    30

    20

    10


------------------------------------------------------------------------

## Pop

Remove the top element.

    Stack before
    Top
    30
    20
    10

    pop()

    Stack after
    Top
    20
    10

------------------------------------------------------------------------

## Peek

View the top element **without removing it**.

Example:

    Top element = 30

------------------------------------------------------------------------

# 6. Stack Implementation Methods

Stacks can be implemented using:

1.  Python List
2.  collections.deque
3.  Linked List
4.  Custom Stack Class

------------------------------------------------------------------------

# 7. Stack Using Python List

Simplest implementation.

``` python
stack = []

stack.append(10)
stack.append(20)
stack.append(30)

print(stack)
```

Output

    [10, 20, 30]

------------------------------------------------------------------------

## Pop Example

``` python
stack.pop()
print(stack)
```

Output

    [10, 20]

------------------------------------------------------------------------

## Peek Example

``` python
print(stack[-1])
```

Output

    20

------------------------------------------------------------------------

# 8. Stack Using deque

Deque is faster for large stacks.

``` python
from collections import deque

stack = deque()

stack.append(10)
stack.append(20)
stack.append(30)

print(stack.pop())
```

------------------------------------------------------------------------

# 9. Stack Using Custom Class

``` python
class Stack:

    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):

        if not self.items:
            return "Stack Empty"

        return self.items.pop()

    def peek(self):
        return self.items[-1]

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)
```

------------------------------------------------------------------------

# 10. Example Program

``` python
s = Stack()

s.push(10)
s.push(20)
s.push(30)

print(s.pop())
print(s.peek())
print(s.size())
```

Output

    30
    20
    2

------------------------------------------------------------------------

# 11. Stack Using Linked List

### Node

``` python
class Node:

    def __init__(self,data):
        self.data = data
        self.next = None
```

### Stack

``` python
class Stack:

    def __init__(self):
        self.top = None

    def push(self,data):

        new_node = Node(data)

        new_node.next = self.top

        self.top = new_node

    def pop(self):

        if self.top is None:
            return None

        value = self.top.data
        self.top = self.top.next

        return value
```

------------------------------------------------------------------------

# 12. Stack Time Complexity

  Operation   Complexity

  ----------- ------------

  Push        O(1)

  Pop         O(1)

  Peek        O(1)

  Search      O(n)


------------------------------------------------------------------------

# 13. Stack Overflow

Occurs when stack **exceeds its maximum size**.

Example:

    Stack size = 3

    push 10
    push 20
    push 30
    push 40 → Overflow

------------------------------------------------------------------------

# 14. Stack Underflow

Occurs when removing element from **empty stack**.

Example:

    pop() on empty stack

------------------------------------------------------------------------

# 15. Stack Memory Representation

Example stack

    Top
    30
    20
    10

Memory representation

    Index   Value

    0       10

    1       20

    2       30


Top pointer:

    top = 2

------------------------------------------------------------------------

# 16. Applications of Stack

Stacks are widely used in computing.

### Function Call Stack

Programming languages use stack to manage function calls.

Example:

``` python
def A():
    B()

def B():
    C()

def C():
    print("Hello")
```

Call stack:

    C
    B
    A

------------------------------------------------------------------------

### Undo / Redo Systems

Used in:

-   Text editors
-   Graphic software
-   Programming IDEs

------------------------------------------------------------------------

### Browser History

    Page1
    Page2
    Page3

Press back:

    Page3 removed

------------------------------------------------------------------------

### Expression Evaluation

Stacks evaluate expressions like:

    (5 + 3) * 2

Used in compilers.

------------------------------------------------------------------------

### Parentheses Checking

Example:

    ((()))

Stack checks matching brackets.

------------------------------------------------------------------------

# 17. Parentheses Matching Algorithm

``` python
def is_balanced(expression):

    stack = []

    pairs = {
        ")":"(",
        "}":"{",
        "]":"["
    }

    for char in expression:

        if char in "({[":
            stack.append(char)

        elif char in ")}]":

            if not stack:
                return False

            if stack.pop() != pairs[char]:
                return False

    return len(stack) == 0
```

------------------------------------------------------------------------

# 18. Stack in Graph Algorithms

Stacks are used in:

-   Depth First Search (DFS)
-   Backtracking
-   Path exploration

------------------------------------------------------------------------

# 19. Stack in Robotics 🤖

Stacks help robots manage tasks and decisions.

### Task Execution

Robot tasks:

    Pick object
    Move forward
    Turn left
    Place object

Stack allows reversing actions.

------------------------------------------------------------------------

### Path Backtracking

Robot exploring rooms:

    Room1 → Room2 → Room3

If blocked:

    pop → return to Room2

------------------------------------------------------------------------

### Motion Command Stack

    Move
    Turn
    Stop

Commands stored sequentially.

------------------------------------------------------------------------

# 20. Key Concepts Summary

Important stack ideas:

-   LIFO principle
-   Push operation
-   Pop operation
-   Top pointer
-   Overflow
-   Underflow
-   Applications in algorithms
-   Robotics use cases

------------------------------------------------------------------------



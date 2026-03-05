# 📦 Queue Data Structure 
This document is a **comprehensive guide to Queues**, covering:

-   Core concepts
-   Internal structure
-   All queue operations
-   Multiple implementations
-   Types of queues
-   Algorithms using queues
-   Time & space complexity
-   Real-world systems
-   Robotics applications 🤖
-   Full Python implementations

------------------------------------------------------------------------

# 1. What is a Queue?

A **Queue** is a **linear data structure** that follows the principle:

**FIFO --- First In First Out**

Meaning:

The **first element inserted** is the **first element removed**.

Example:

    Front → 10 → 20 → 30 → 40 → Rear

If we perform dequeue:

    Front → 20 → 30 → 40 → Rear

------------------------------------------------------------------------

# 2. Real‑World Analogy

## Ticket Counter Line

    Person1 → Person2 → Person3 → Person4

Rules:

-   Person1 arrives first
-   Person1 gets served first

This perfectly represents FIFO.

------------------------------------------------------------------------

# 3. Queue Terminology

  Term      Meaning

  --------- ----------------------

  Enqueue   Insert element

  Dequeue   Remove element

  Front     First element

  Rear      Last element

  Peek      View front element

  isEmpty   Check if queue empty

  Size      Number of elements


------------------------------------------------------------------------

# 4. Queue Structure

A queue has **two pointers**:

    Front                       Rear

     ↓                           ↓

    10 → 20 → 30 → 40 → 50

-   Insertion happens at **rear**
-   Removal happens at **front**

------------------------------------------------------------------------

# 5. Basic Operations

## Enqueue

Insert element at rear.

Example:

    Before:
    Front → 10 → 20 → 30 → Rear

    enqueue(40)

    After:
    Front → 10 → 20 → 30 → 40 → Rear

------------------------------------------------------------------------

## Dequeue

Remove element from front.

    Before:
    Front → 10 → 20 → 30 → 40 → Rear

    dequeue()

    After:
    Front → 20 → 30 → 40 → Rear

------------------------------------------------------------------------

## Peek

View first element without removing it.

    Front element = 20

------------------------------------------------------------------------

# 6. Queue Implementation Methods

Queues can be implemented using:

1.  Python List
2.  collections.deque (recommended)
3.  Linked List
4.  Circular array
5.  Custom queue class

------------------------------------------------------------------------

# 7. Queue Using Python List

``` python
queue = []

queue.append(10)
queue.append(20)
queue.append(30)

print(queue)
```

Output

    [10, 20, 30]

Dequeue:

``` python
queue.pop(0)
```

⚠ Problem: removing first element shifts entire list → **O(n)**.

------------------------------------------------------------------------

# 8. Queue Using deque (Best Practice)

Deque is optimized for queue operations.

``` python
from collections import deque

queue = deque()

queue.append(10)
queue.append(20)
queue.append(30)

print(queue)
```

Dequeue:

``` python
queue.popleft()
```

Time complexity:

    O(1)

------------------------------------------------------------------------

# 9. Custom Queue Class

``` python
class Queue:

    def __init__(self):
        self.items = []

    def enqueue(self,item):
        self.items.append(item)

    def dequeue(self):

        if not self.items:
            return "Queue Empty"

        return self.items.pop(0)

    def peek(self):
        return self.items[0]

    def is_empty(self):
        return len(self.items) == 0

    def size(self):
        return len(self.items)
```

------------------------------------------------------------------------

# 10. Queue Using Linked List

### Node

``` python
class Node:

    def __init__(self,data):
        self.data = data
        self.next = None
```

### Queue

``` python
class Queue:

    def __init__(self):
        self.front = None
        self.rear = None
```

### Enqueue

``` python
def enqueue(self,data):

    new_node = Node(data)

    if self.rear is None:
        self.front = self.rear = new_node
        return

    self.rear.next = new_node
    self.rear = new_node
```

### Dequeue

``` python
def dequeue(self):

    if self.front is None:
        return None

    value = self.front.data
    self.front = self.front.next

    if self.front is None:
        self.rear = None

    return value
```

------------------------------------------------------------------------

# 11. Circular Queue

Circular queue connects end to beginning.

    Front

      ↓

    10 → 20 → 30

     ↑        ↓

     └────────┘


Advantages:

-   Efficient memory usage
-   Used in buffering systems
-   Used in CPU scheduling

------------------------------------------------------------------------

# 12. Priority Queue

Elements processed by **priority rather than order**.

Example:

    TaskA priority=1
    TaskB priority=3
    TaskC priority=2

Execution order:

    TaskA → TaskC → TaskB

Python example:

``` python
import heapq

pq = []

heapq.heappush(pq,(1,"TaskA"))
heapq.heappush(pq,(3,"TaskB"))
heapq.heappush(pq,(2,"TaskC"))

print(heapq.heappop(pq))
```

------------------------------------------------------------------------

# 13. Double Ended Queue (Deque)

Allows insertion/removal from both ends.

    Front ← 10 → 20 → 30 → Rear

Python:

``` python
from collections import deque

dq = deque()

dq.append(10)
dq.appendleft(5)
dq.pop()
dq.popleft()
```

------------------------------------------------------------------------

# 14. Time Complexity

  Operation   Complexity

  ----------- ------------

  Enqueue     O(1)

  Dequeue     O(1)

  Peek        O(1)

  Search      O(n)
  

------------------------------------------------------------------------

# 15. Queue Overflow

Occurs when queue is full.

Example:

    Queue size = 3

    enqueue 10
    enqueue 20
    enqueue 30
    enqueue 40 ❌ overflow

------------------------------------------------------------------------

# 16. Queue Underflow

Occurs when removing from empty queue.

    dequeue() on empty queue

------------------------------------------------------------------------

# 17. Algorithms Using Queues

Queues are fundamental to many algorithms.

### Breadth‑First Search (BFS)

Traversal example:

    A
    | \
    B  C
       |
       D

Traversal order:

    A → B → C → D

Python example:

``` python
from collections import deque

graph = {
"A":["B","C"],
"B":[],
"C":["D"],
"D":[]
}

def bfs(start):

    visited=set()
    queue=deque([start])

    while queue:

        node=queue.popleft()

        if node not in visited:

            print(node)
            visited.add(node)
            queue.extend(graph[node])
```

------------------------------------------------------------------------

# 18. Queue in Operating Systems

Queues manage:

-   CPU scheduling
-   I/O buffers
-   process management

Example:

    Process1 → Process2 → Process3

------------------------------------------------------------------------

# 19. Queue in Networking

Network packets arrive in order.

    Packet1 → Packet2 → Packet3

Routers process packets sequentially.

------------------------------------------------------------------------

# 20. Queue in Robotics 🤖

Queues are extremely important in robotics systems.

### Sensor Data Processing

Robots continuously receive sensor readings.

    Sensor1 → Sensor2 → Sensor3

Queue ensures correct processing order.

------------------------------------------------------------------------

### Camera Frame Processing

Vision systems process frames sequentially.

    Frame1 → Frame2 → Frame3

------------------------------------------------------------------------

### Robot Command Queue

    Move Forward
    Turn Left
    Pick Object
    Place Object

Commands executed FIFO.

------------------------------------------------------------------------

### Autonomous Navigation

Path planning systems schedule navigation tasks using queues.

------------------------------------------------------------------------

# 21. Complete Queue Program

``` python
from collections import deque

class Queue:

    def __init__(self):
        self.queue = deque()

    def enqueue(self,item):
        self.queue.append(item)

    def dequeue(self):

        if not self.queue:
            return None

        return self.queue.popleft()

    def display(self):
        print(list(self.queue))
```

Example:

``` python
q = Queue()

q.enqueue(10)
q.enqueue(20)
q.enqueue(30)

q.display()

q.dequeue()

q.display()
```

Output

    [10, 20, 30]
    [20, 30]

------------------------------------------------------------------------

# 🚀 Summary

Important ideas:

-   FIFO principle
-   Front pointer
-   Rear pointer
-   Enqueue
-   Dequeue
-   Circular queue
-   Priority queue
-   Deque
-   BFS algorithms
-   Robotics command queues

Queues are a **core data structure used in operating systems,
networking, AI, robotics, and large-scale distributed systems**.

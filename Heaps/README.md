# Heaps in Python: 


## What is a Heap?

A heap is a specialized tree-based data structure that satisfies the *heap property*:
- In a **max heap**, for any given node, the value of that node is greater than or equal to the values of its children
- In a **min heap**, for any given node, the value of that node is less than or equal to the values of its children

Think of a heap as a partially ordered tree, where the root is either the maximum element (max heap) or minimum element (min heap).

## Why Use Heaps?

Heaps are great for:
- Finding the min/max value quickly (O(1) time)
- Efficiently extracting the min/max value (O(log n) time)
- Implementing priority queues
- Heap sort algorithm

## Python's Built-in Heap: heapq

Python's standard library includes `heapq` module that implements a **min heap**.

```python
import heapq

# Create an empty heap
heap = []

# Add elements (heappush)
heapq.heappush(heap, 3)
heapq.heappush(heap, 1)
heapq.heappush(heap, 4)
heapq.heappush(heap, 2)

print(heap)  # [1, 2, 4, 3] - Not sorted! But structured as a heap

# Get minimum element without removing it
print(heap[0])  # 1

# Remove and return the smallest element (heappop)
smallest = heapq.heappop(heap)
print(smallest)  # 1
print(heap)  # [2, 3, 4]
```

## Visualizing a Heap

Although stored as a list, a heap conceptually looks like a tree:

```
    1          After popping 1:     2
   / \                             / \
  2   4                           3   4
 /
3
```

## Creating a Heap from Existing Data

You can convert an existing list to a heap using `heapify`:

```python
import heapq

numbers = [10, 4, 7, 3, 5, 1, 6]
heapq.heapify(numbers)  # Transform list in-place into a heap
print(numbers)  # [1, 3, 6, 4, 5, 10, 7]

# Now you can use heappop to get items in ascending order
while numbers:
    print(heapq.heappop(numbers), end=' ')  # 1 3 4 5 6 7 10
```

## How Heaps Work Behind the Scenes

A heap is typically implemented as an array where for any element at index `i`:
- Left child is at index `2*i + 1`
- Right child is at index `2*i + 2`
- Parent is at index `(i-1) // 2`

## Implementing Common Heap Operations

Let's look at some common heap operations:

```python
import heapq

# Priority Queue Example
task_queue = []

# Add tasks with priorities (lower number = higher priority)
heapq.heappush(task_queue, (2, "Medium priority task"))
heapq.heappush(task_queue, (1, "High priority task"))
heapq.heappush(task_queue, (3, "Low priority task"))

# Process tasks in priority order
while task_queue:
    priority, task = heapq.heappop(task_queue)
    print(f"Processing {task} with priority {priority}")
```

## Implementing a Max Heap

Since Python's `heapq` only provides a min heap, we can implement a max heap by negating the values:

```python
import heapq

# Create a max heap
max_heap = []

# Insert values with their sign flipped
heapq.heappush(max_heap, -1)
heapq.heappush(max_heap, -5)
heapq.heappush(max_heap, -3)
heapq.heappush(max_heap, -2)

# Get maximum element
print(-max_heap[0])  # 5

# Pop maximum element
max_value = -heapq.heappop(max_heap)
print(max_value)  # 5
print([-x for x in max_heap])  # [3, 2, 1]
```

## Finding K Largest/Smallest Elements

The heapq module provides specialized functions for finding the k largest or smallest elements:

```python
import heapq

numbers = [10, 4, 7, 3, 20, 15, 6, 30]

# Find 3 largest elements
largest = heapq.nlargest(3, numbers)
print(largest)  # [30, 20, 15]

# Find 3 smallest elements  
smallest = heapq.nsmallest(3, numbers)
print(smallest)  # [3, 4, 6]
```

## Implementing a Complete Heap Class

Let's create a more comprehensive heap implementation:

```python
class MinHeap:
    def __init__(self):
        self.heap = []
        
    def parent(self, i):
        return (i - 1) // 2
        
    def left_child(self, i):
        return 2 * i + 1
        
    def right_child(self, i):
        return 2 * i + 2
        
    def get_min(self):
        if self.heap:
            return self.heap[0]
        return None
        
    def insert(self, value):
        self.heap.append(value)
        current = len(self.heap) - 1
        
        # Fix the min heap property if it's violated (bubble up)
        while current > 0 and self.heap[current] < self.heap[self.parent(current)]:
            # Swap with parent
            self.heap[current], self.heap[self.parent(current)] = self.heap[self.parent(current)], self.heap[current]
            current = self.parent(current)
            
    def heapify(self, i):
        smallest = i
        left = self.left_child(i)
        right = self.right_child(i)
        
        # Check if left child exists and is smaller than root
        if left < len(self.heap) and self.heap[left] < self.heap[smallest]:
            smallest = left
            
        # Check if right child exists and is smaller than smallest so far
        if right < len(self.heap) and self.heap[right] < self.heap[smallest]:
            smallest = right
            
        # If smallest is not the root
        if smallest != i:
            # Swap
            self.heap[i], self.heap[smallest] = self.heap[smallest], self.heap[i]
            # Recursively heapify the affected subtree
            self.heapify(smallest)
            
    def extract_min(self):
        if not self.heap:
            return None
            
        # Store the minimum value
        min_val = self.heap[0]
        
        # Replace root with last element
        self.heap[0] = self.heap[-1]
        self.heap.pop()
        
        # Heapify the root
        if self.heap:
            self.heapify(0)
            
        return min_val
        
    def size(self):
        return len(self.heap)
        
    def is_empty(self):
        return len(self.heap) == 0
        
    def __str__(self):
        return str(self.heap)
```

## Usage Example:

```python
# Create a new min heap
min_heap = MinHeap()

# Insert elements
min_heap.insert(5)
min_heap.insert(3)
min_heap.insert(8)
min_heap.insert(1)
min_heap.insert(10)

print(min_heap)  # [1, 3, 8, 5, 10]

# Get minimum
print(min_heap.get_min())  # 1

# Extract minimum elements
print(min_heap.extract_min())  # 1
print(min_heap.extract_min())  # 3
print(min_heap.extract_min())  # 5

print(min_heap)  # [8, 10]
```

## Time Complexity

- Getting minimum/maximum: O(1)
- Insertion: O(log n)
- Extraction: O(log n)
- Creating a heap from an array: O(n)


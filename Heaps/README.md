# Python’s heapq Module (Min-Heap)
First, let’s use the built-in heapq module, which provides an efficient implementation of a min-heap.
import heapq

# Step 1: Create an empty list to store the heap
heap = []

# Step 2: Push elements into the heap
heapq.heappush(heap, 5)  # Add 5
heapq.heappush(heap, 2)  # Add 2
heapq.heappush(heap, 7)  # Add 7
heapq.heappush(heap, 1)  # Add 1

# Step 3: Print the heap (it's maintained as a min-heap)
print("Heap after pushing elements:", heap)  # Output: [1, 2, 7, 5]

# Step 4: Pop the smallest element
smallest = heapq.heappop(heap)
print("Smallest element popped:", smallest)  # Output: 1
print("Heap after popping:", heap)  # Output: [2, 5, 7]

# Step 5: Convert a list into a heap
numbers = [9, 3, 6, 1, 4]
heapq.heapify(numbers)
print("Heapified list:", numbers)  # Output: [1, 3, 6, 9, 4]
Custom Min-Heap Implementation
Now, let’s create a custom Min-Heap class from scratch with step-by-step explanations.
class MinHeap:
    def __init__(self):
        # Step 1: Initialize an empty list to store heap elements
        self.heap = []

    def parent(self, index):
        # Step 2: Find parent index of a node
        return (index - 1) // 2

    def left_child(self, index):
        # Step 3: Find left child index
        return 2 * index + 1

    def right_child(self, index):
        # Step 4: Find right child index
        return 2 * index + 2

    def swap(self, i, j):
        # Step 5: Swap two elements in the heap
        self.heap[i], self.heap[j] = self.heap[j], self.heap[i]

    def heapify_up(self, index):
        # Step 6: Move a node up to maintain heap property
        parent_idx = self.parent(index)
        if index > 0 and self.heap[index] < self.heap[parent_idx]:
            self.swap(index, parent_idx)
            self.heapify_up(parent_idx)

    def heapify_down(self, index):
        # Step 7: Move a node down to maintain heap property
        min_index = index
        left = self.left_child(index)
        right = self.right_child(index)
        size = len(self.heap)

        if left < size and self.heap[left] < self.heap[min_index]:
            min_index = left
        if right < size and self.heap[right] < self.heap[min_index]:
            min_index = right

        if min_index != index:
            self.swap(index, min_index)
            self.heapify_down(min_index)

    def push(self, value):
        # Step 8: Add a new element
        self.heap.append(value)
        self.heapify_up(len(self.heap) - 1)

    def pop(self):
        # Step 9: Remove and return the smallest element
        if not self.heap:
            return None
        if len(self.heap) == 1:
            return self.heap.pop()

        root = self.heap[0]
        self.heap[0] = self.heap.pop()
        self.heapify_down(0)
        return root

    def display(self):
        # Step 10: Display the heap
        print("Heap:", self.heap)

# Demonstration
if __name__ == "__main__":
    # Create a heap instance
    min_heap = MinHeap()

    # Push elements
    min_heap.push(5)
    min_heap.push(2)
    min_heap.push(7)
    min_heap.push(1)
    min_heap.display()  # Output: Heap: [1, 2, 7, 5]

    # Pop the smallest element
    smallest = min_heap.pop()
    print("Popped element:", smallest)  # Output: Popped element: 1
    min_heap.display()  # Output: Heap: [2, 5, 7]
Step-by-Step Explanation of Custom Implementation
	1	Initialization: We start with an empty list (self.heap) to store the heap elements.
	2	Parent/Child Calculations: Helper methods calculate indices of parent, left child, and right child based on the array representation of a binary tree.
	3	Swap: A utility to swap two elements in the heap.
	4	Heapify Up: After inserting an element, this ensures the min-heap property (parent < children) by moving the element up if needed.
	5	Heapify Down: After removing the root, this moves the new root down to maintain the heap property.
	6	Push: Adds an element to the end and heapifies up.
	7	Pop: Removes the smallest element (root), replaces it with the last element, and heapifies down.
	8	Display: Shows the current state of the heap.
Key Points
	•	The heapq module is optimized and recommended for practical use.
	•	The custom implementation helps understand the underlying mechanics.
	•	Time Complexity:
	◦	Push: O(log n)
	◦	Pop: O(log n)
	◦	Heapify: O(n)


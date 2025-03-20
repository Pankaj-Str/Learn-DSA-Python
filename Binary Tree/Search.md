
### What is Binary Search?
Binary Search is an efficient algorithm to find an element in a sorted array. It works by repeatedly dividing the search range in half.
Prerequisites
	•	The input array must be sorted.
	•	Time Complexity: O(log n)
	•	Space Complexity: O(1) for iterative, O(log n) for recursive due to call stack.

Iterative Binary Search
Here’s a step-by-step implementation:
def binary_search_iterative(arr, target):
    # Step 1: Initialize left and right pointers
    left = 0
    right = len(arr) - 1
    
    # Step 2: Continue until left pointer is less than or equal to right
    while left <= right:
        # Step 3: Calculate the middle index
        mid = (left + right) // 2
        
        # Step 4: If target is found at mid, return the index
        if arr[mid] == target:
            return mid
        
        # Step 5: If target is greater than mid element, search right half
        elif arr[mid] < target:
            left = mid + 1
        
        # Step 6: If target is less than mid element, search left half
        else:
            right = mid - 1
    
    # Step 7: If target is not found, return -1
    return -1

# Demonstration
if __name__ == "__main__":
    # Sorted array
    arr = [2, 3, 4, 10, 40, 50, 60, 70]
    target = 10
    
    # Run binary search
    result = binary_search_iterative(arr, target)
    if result != -1:
        print(f"Element {target} found at index {result}")
    else:
        print(f"Element {target} not found")
    # Output: Element 10 found at index 3
Step-by-Step Breakdown (Iterative)
	1	Initialize Pointers: left starts at 0, right at the last index.
	2	Loop Condition: Continue while left <= right (search range is valid).
	3	Calculate Mid: Find the middle index using (left + right) // 2.
	4	Check Mid: If arr[mid] == target, return the index.
	5	Adjust Range:
	◦	If target > arr[mid], move left to mid + 1 (search right half).
	◦	If target < arr[mid], move right to mid - 1 (search left half).
	6	Not Found: If the loop ends, return -1.

Recursive Binary Search
Here’s the recursive version:
def binary_search_recursive(arr, target, left, right):
    # Step 1: Base case - if left pointer exceeds right, element not found
    if left > right:
        return -1
    
    # Step 2: Calculate the middle index
    mid = (left + right) // 2
    
    # Step 3: If target is found at mid, return the index
    if arr[mid] == target:
        return mid
    
    # Step 4: Recursive cases
    # If target is less than mid element, search left half
    elif arr[mid] > target:
        return binary_search_recursive(arr, target, left, mid - 1)
    # If target is greater than mid element, search right half
    else:
        return binary_search_recursive(arr, target, mid + 1, right)

# Demonstration
if __name__ == "__main__":
    # Sorted array
    arr = [2, 3, 4, 10, 40, 50, 60, 70]
    target = 40
    
    # Run binary search
    result = binary_search_recursive(arr, target, 0, len(arr) - 1)
    if result != -1:
        print(f"Element {target} found at index {result}")
    else:
        print(f"Element {target} not found")
    # Output: Element 40 found at index 4
Step-by-Step Breakdown (Recursive)
	1	Base Case: If left > right, the search range is invalid, return -1.
	2	Calculate Mid: Same as iterative, find the middle index.
	3	Check Mid: If arr[mid] == target, return the index.
	4	Recursive Calls:
	◦	If target < arr[mid], recurse on the left half (left to mid - 1).
	◦	If target > arr[mid], recurse on the right half (mid + 1 to right).

Example Walkthrough (Iterative)
Array: [2, 3, 4, 10, 40, 50, 60, 70], Target: 10
	1	Initial: left = 0, right = 7, mid = 3 (value = 10)
	◦	arr[3] == 10, return 3.
Array: [2, 3, 4, 10, 40, 50, 60, 70], Target: 5
	1	Initial: left = 0, right = 7, mid = 3 (value = 10)
	◦	5 < 10, right = 2
	2	Next: left = 0, right = 2, mid = 1 (value = 3)
	◦	5 > 3, left = 2
	3	Next: left = 2, right = 2, mid = 2 (value = 4)
	◦	5 > 4, left = 3
	4	left > right, return -1.

Key Notes
	•	Iterative vs Recursive: Iterative is more space-efficient; recursive is more elegant but uses stack space.
	•	Edge Cases: Empty array, target not present, single-element array—all handled by the above logic.
	•	Optimization Tip: To avoid integer overflow in languages with fixed-size integers, use mid = left + (right - left) // 2 instead of (left + right) // 2. Python handles this automatically due to arbitrary-precision integers.


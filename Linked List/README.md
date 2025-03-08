# Linked List in Python 

## What is a Linked List?

Think of a linked list like a treasure hunt. Each clue (node) contains:
- A treasure (data)
- Directions to the next clue (next pointer)

Unlike arrays where elements are stored in continuous memory, linked list elements can be scattered in memory, connected by these "next" pointers.

## Step 1: Create the Building Block (Node)

```python
class Node:
    def __init__(self, data):
        self.data = data  # The value we want to store
        self.next = None  # Pointer to the next node (initially None)
```

This is like creating a box that can hold:
- Any value you want (data)
- A string that can point to another box (next)

## Step 2: Create the Linked List Container

```python
class LinkedList:
    def __init__(self):
        self.head = None  # At first, our list is empty
```

The `head` is just the first node in our list. When we create a new list, it's empty, so `head` is `None`.

## Step 3: Adding Items to the End (Append)

```python
def append(self, data):
    """Add a new item to the end of the list"""
    # Create the new box with our data
    new_node = Node(data)
    
    # If the list is empty, this new box becomes the head
    if self.head is None:
        self.head = new_node
        return
    
    # Otherwise, find the last box in our list
    current = self.head
    while current.next:  # While there's another box after this one
        current = current.next  # Move to the next box
    
    # Connect the last box to our new box
    current.next = new_node
```

## Step 4: Adding Items to the Beginning (Prepend)

```python
def prepend(self, data):
    """Add a new item to the beginning of the list"""
    # Create the new box
    new_node = Node(data)
    
    # Make the new box point to the current head
    new_node.next = self.head
    
    # The new box is now the head
    self.head = new_node
```

## Step 5: Printing the List

```python
def print_list(self):
    """Show all items in the list"""
    current = self.head  # Start at the first box
    
    # Visit each box until we reach the end
    while current:
        print(current.data, end=" → ")  # Print what's in the current box
        current = current.next  # Move to the next box
    
    print("None")  # Indicate the end of the list
```

## Step 6: Putting It All Together

Here's the complete basic linked list:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
    
    def append(self, data):
        """Add a new item to the end of the list"""
        new_node = Node(data)
        
        if self.head is None:
            self.head = new_node
            return
        
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node
    
    def prepend(self, data):
        """Add a new item to the beginning of the list"""
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
    
    def print_list(self):
        """Show all items in the list"""
        current = self.head
        while current:
            print(current.data, end=" → ")
            current = current.next
        print("None")
```

## Step 7: Let's See It in Action!

```python
# Create an empty list
my_list = LinkedList()

# Add some numbers
my_list.append(10)
my_list.append(20)
my_list.append(30)

# Display our list
print("After adding 10, 20, and 30:")
my_list.print_list()  # Output: 10 → 20 → 30 → None

# Add a number to the beginning
my_list.prepend(5)

# Display our list again
print("After adding 5 to the beginning:")
my_list.print_list()  # Output: 5 → 10 → 20 → 30 → None
```

## Step 8: Let's Add Two More Useful Methods

### Deleting a Node

```python
def delete(self, value):
    """Remove the first node with the given value"""
    # If the list is empty, nothing to delete
    if self.head is None:
        print("List is empty!")
        return
    
    # If the head node has the value we want to delete
    if self.head.data == value:
        self.head = self.head.next
        return
    
    # Search for the value
    current = self.head
    while current.next and current.next.data != value:
        current = current.next
    
    # If we found it, delete it
    if current.next:
        current.next = current.next.next
    else:
        print(f"{value} not found in the list!")
```

### Finding the Length of the List

```python
def length(self):
    """Count how many nodes are in the list"""
    count = 0
    current = self.head
    
    while current:
        count += 1
        current = current.next
    
    return count
```

## Visual Comparison: Array vs. Linked List

Arrays:
```
┌───┬───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │ 5 │  Elements are stored next to each other in memory
└───┴───┴───┴───┴───┘
```

Linked Lists:
```
┌───┬───┐    ┌───┬───┐    ┌───┬───┐
│ 1 │ •─┼───>│ 2 │ •─┼───>│ 3 │ / │
└───┴───┘    └───┴───┘    └───┴───┘
  Data Next    Data Next    Data Next
```

.​​​
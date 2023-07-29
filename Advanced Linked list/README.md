# Advanced Linked List


In Python, you can implement an advanced linked list using classes and object-oriented programming (OOP) concepts. An advanced linked list typically involves more complex functionalities than a basic linked list, such as inserting elements at specific positions, deleting elements, searching for elements, and implementing advanced algorithms based on the linked list data structure.

Here's an example of an advanced singly linked list in Python:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class AdvancedLinkedList:
    def __init__(self):
        self.head = None

    def is_empty(self):
        return self.head is None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node

    def insert_at_position(self, data, position):
        if position <= 0:
            self.prepend(data)
        else:
            new_node = Node(data)
            current = self.head
            count = 0
            while count < position - 1 and current.next:
                current = current.next
                count += 1
            new_node.next = current.next
            current.next = new_node

    def delete_at_position(self, position):
        if position <= 0:
            self.head = self.head.next
        else:
            current = self.head
            count = 0
            while count < position - 1 and current.next:
                current = current.next
                count += 1
            if current.next:
                current.next = current.next.next

    def search(self, data):
        current = self.head
        while current:
            if current.data == data:
                return True
            current = current.next
        return False

    def display(self):
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        print(" -> ".join(str(item) for item in elements))

# Test the AdvancedLinkedList
my_list = AdvancedLinkedList()
my_list.append(10)
my_list.append(20)
my_list.append(30)

my_list.display()  # Output: 10 -> 20 -> 30

my_list.insert_at_position(15, 1)
my_list.display()  # Output: 10 -> 15 -> 20 -> 30

my_list.delete_at_position(2)
my_list.display()  # Output: 10 -> 15 -> 30

print(my_list.search(15))  # Output: True
print(my_list.search(25))  # Output: False
```

In this example, we have a `Node` class representing each element of the linked list. The `AdvancedLinkedList` class contains methods for appending elements, inserting at a specific position, deleting at a specific position, searching for an element, and displaying the linked list.

This implementation provides more functionality compared to a basic linked list and can be further extended to implement additional advanced algorithms and data structures based on linked lists.
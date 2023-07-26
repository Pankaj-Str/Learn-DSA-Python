# Python Search Tree

"Binary Search Tree" (BST) in Python.
A binary search tree is a binary tree data structure in which each node has at most two children, and the left subtree of a node contains values less than the node's value, while the right subtree contains values greater than the node's value. This property enables efficient searching, insertion, and deletion of elements.

Let's see an implementation of a binary search tree in Python:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def insert(self, data):
        if not self.root:
            self.root = Node(data)
        else:
            self._insert_recursive(self.root, data)

    def _insert_recursive(self, current_node, data):
        if data < current_node.data:
            if not current_node.left:
                current_node.left = Node(data)
            else:
                self._insert_recursive(current_node.left, data)
        elif data > current_node.data:
            if not current_node.right:
                current_node.right = Node(data)
            else:
                self._insert_recursive(current_node.right, data)
        else:
            # Handle duplicate values (optional)
            pass

    def search(self, data):
        return self._search_recursive(self.root, data)

    def _search_recursive(self, current_node, data):
        if not current_node or current_node.data == data:
            return current_node

        if data < current_node.data:
            return self._search_recursive(current_node.left, data)
        else:
            return self._search_recursive(current_node.right, data)

# Test the BinarySearchTree
bst = BinarySearchTree()
bst.insert(50)
bst.insert(30)
bst.insert(70)
bst.insert(20)
bst.insert(40)
bst.insert(60)
bst.insert(80)

print(bst.search(40))          # Output: <__main__.Node object at ...>
print(bst.search(100))         # Output: None
```

In this example, we define a `Node` class representing each node of the binary search tree and a `BinarySearchTree` class containing methods to insert elements and search for values within the tree.

The `insert()` method inserts elements into the binary search tree while maintaining the BST property. The `search()` method finds the node with the given value and returns it, or returns `None` if the value is not present in the tree.

Binary search trees are commonly used to implement search algorithms efficiently and to perform tasks like ordered traversal and range queries. They provide average-case time complexity of O(log n) for search, insertion, and deletion operations, making them a powerful data structure for certain applications. However, the efficiency of a binary search tree relies on its balance; if the tree becomes heavily unbalanced, the time complexity of operations may degrade to O(n). To address this issue, balanced binary search tree variants like AVL trees and Red-Black trees are used.
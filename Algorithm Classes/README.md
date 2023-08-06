# Amortized analysis

Amortized analysis is a technique used to analyze the average time complexity of a sequence of operations in a data structure or algorithm. It provides a more accurate understanding of the overall performance, even if individual operations may have varying time complexities. A common method to perform amortized analysis is by using potential functions.

Let's demonstrate amortized analysis with a simple example of a dynamic array that doubles its size when it runs out of space. We'll use a potential function approach to analyze the cost of appending elements to the dynamic array:

```python
class DynamicArray:
    def __init__(self):
        self.array = [None]
        self.size = 0
        self.capacity = 1

    def append(self, element):
        if self.size == self.capacity:
            self.resize(self.capacity * 2)

        self.array[self.size] = element
        self.size += 1

    def resize(self, new_capacity):
        new_array = [None] * new_capacity
        for i in range(self.size):
            new_array[i] = self.array[i]

        self.array = new_array
        self.capacity = new_capacity

# Test the DynamicArray class
if __name__ == "__main__":
    dynamic_array = DynamicArray()
    elements = [1, 2, 3, 4, 5]

    for elem in elements:
        dynamic_array.append(elem)

    print("Dynamic array:", dynamic_array.array)
```

In this example, the `DynamicArray` class represents a resizable array that doubles its capacity whenever it runs out of space. The `append` method is used to add elements to the array. When the array reaches its current capacity, it calls the `resize` method to increase the capacity.

Now, let's perform an amortized analysis of the `append` operation:

1. Appending the first element takes O(1) time, as the array is empty, and no resizing is needed.

2. When the array reaches its capacity and resizing is required, it takes O(n) time to copy all n elements to the new array.

3. However, after resizing, the capacity of the array becomes double, and the next n append operations will take O(1) time each.

To calculate the amortized time complexity per `append` operation, we use the potential function approach. Let the potential function be Φ, and let c_i represent the actual cost of the ith append operation.

Φ(i) = 2 * self.capacity - self.size

The amortized cost for each append operation is then:

ŷ_i = c_i + Φ(i) - Φ(i-1)

When resizing occurs (c_i = O(n)), ŷ_i will be O(n + (2 * new_capacity - self.size) - (2 * self.capacity - self.size)) = O(n). For the next n append operations, ŷ_i will be O(1).

Therefore, the amortized cost per `append` operation is O(1). This analysis tells us that on average, each `append` operation takes constant time, despite occasional expensive resizing operations.

Note: The actual calculation of the potential function and amortized cost varies depending on the specific problem and data structure being analyzed. The example above provides a simplified illustration of amortized analysis for a dynamic array.
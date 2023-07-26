# Dequeue DSA


The `deque` (double-ended queue) data structure in Python, which is part of the `collections` module.

A deque is similar to a list, but with optimizations for efficient append and pop operations from both ends of the deque. It allows you to insert and remove elements from either end with constant-time complexity, making it useful for certain algorithms and scenarios where these operations are frequently performed.

Here's a brief overview of how to use `deque` in Python:

1. Import the `deque` class from the `collections` module:

```python
from collections import deque
```

2. Create a deque:

```python
my_deque = deque()
```

3. Append elements to the right (rear) of the deque using `append()`:

```python
my_deque.append(10)
my_deque.append(20)
my_deque.append(30)
```

4. Append elements to the left (front) of the deque using `appendleft()`:

```python
my_deque.appendleft(5)
```

5. Pop elements from the right (rear) of the deque using `pop()`:

```python
last_element = my_deque.pop()
```

6. Pop elements from the left (front) of the deque using `popleft()`:

```python
first_element = my_deque.popleft()
```

Here's the updated deque after performing the above operations:

```
my_deque: [5, 10, 20]
```

As you can see, `deque` provides efficient ways to work with elements at both ends, making it handy for various algorithms and data processing tasks.

Additionally, `deque` supports various other methods like `clear()`, `extend()`, `extendleft()`, `rotate()`, etc., which you can use to manipulate the deque based on your specific requirements.

Remember to import the `deque` class from the `collections` module before using it, as shown in the examples above.



Python provides an efficient implementation of a deque through the built-in `collections` module. This implementation is called `deque`, and it offers constant-time performance for append and pop operations from both ends of the deque, making it a versatile and powerful data structure.

Here's an example of how to use `deque` in Python:

```python
from collections import deque

# Create a deque
my_deque = deque()

# Append elements to the right (rear)
my_deque.append(10)
my_deque.append(20)
my_deque.append(30)

# Append elements to the left (front)
my_deque.appendleft(5)

# Deque now contains: [5, 10, 20, 30]

# Pop elements from the right (rear)
print(my_deque.pop())      # Output: 30

# Pop elements from the left (front)
print(my_deque.popleft())  # Output: 5

# Deque now contains: [10, 20]
```

In the above example, we used the `deque` class to create a double-ended queue. We appended elements to the right using `append()` and to the left using `appendleft()`. We also used `pop()` to remove an element from the right and `popleft()` to remove an element from the left.

The advantage of using a deque compared to a list for implementations like a queue is that popping elements from the front of the deque is more efficient than doing so from a list since a deque is optimized for this operation.

In DSA, a deque is a valuable data structure in various scenarios where you need efficient insertions and deletions at both ends. It's particularly useful when building complex algorithms or solving specific problems that require bidirectional manipulation of elements.


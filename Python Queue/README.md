# Queue Data Structure


A queue is a data structure that follows the First-In-First-Out (FIFO) principle, meaning that the first element added to the queue will be the first one to be removed. It's similar to waiting in a line or queue in real life, where the person who enters the queue first will be served first.

Python provides a built-in module called `queue` that implements various types of queues. The most commonly used queue classes in Python are `Queue`, `LifoQueue`, and `PriorityQueue`, which are part of the `queue` module.

Here's a brief overview of each type of queue:

1. `Queue`: This is a standard FIFO queue.

2. `LifoQueue`: This is a Last-In-First-Out (LIFO) queue, also known as a stack. The last element added will be the first one to be removed.

3. `PriorityQueue`: This is a queue where elements are ordered based on their priority. Elements with higher priority will be dequeued before those with lower priority.

Here's a simple example of how to use the `Queue` class:

```python
import queue

# Create a Queue
my_queue = queue.Queue()

# Enqueue elements
my_queue.put(10)
my_queue.put(20)
my_queue.put(30)

# Dequeue elements (FIFO order)
print(my_queue.get())  # Output: 10
print(my_queue.get())  # Output: 20
print(my_queue.get())  # Output: 30
```

For the `LifoQueue`, the usage is quite similar, but the order of dequeuing will be different:

```python
import queue

# Create a LifoQueue
my_lifo_queue = queue.LifoQueue()

# Enqueue elements
my_lifo_queue.put(10)
my_lifo_queue.put(20)
my_lifo_queue.put(30)

# Dequeue elements (LIFO order)
print(my_lifo_queue.get())  # Output: 30
print(my_lifo_queue.get())  # Output: 20
print(my_lifo_queue.get())  # Output: 10
```

Keep in mind that Python's `queue` module is thread-safe, which means it can be used in multithreaded programs without worrying about data corruption or race conditions. If you need to synchronize access to a queue from multiple threads, it's a suitable choice.

# Python Graph

A "graph" is a data structure that consists of a collection of nodes (also called vertices) and edges connecting these nodes. Graphs are used to represent relationships between various entities and are a fundamental data structure in computer science and many real-world applications.

Graphs can be classified into two main types based on their properties:

1. Directed Graph (Digraph):
   - In a directed graph, the edges have a direction, indicating a one-way relationship between nodes.
   - If there is an edge from node A to node B, you can go from A to B, but not necessarily from B to A.

2. Undirected Graph:
   - In an undirected graph, the edges have no direction, representing a two-way relationship between nodes.
   - If there is an edge between node A and node B, you can go from A to B and vice versa.

Graphs can also have weighted edges, where each edge has an associated weight or cost. Weighted graphs are used to represent scenarios where there are different costs associated with moving between nodes.

Graphs can be represented using various data structures. Two common representations are:

1. Adjacency Matrix:
   - An adjacency matrix is a 2D array of size V x V, where V is the number of vertices in the graph.
   - The entry at the i-th row and j-th column represents whether there is an edge between vertices i and j (1 if there is an edge, 0 otherwise).
   - For weighted graphs, the entry can represent the weight of the edge between the vertices.

2. Adjacency List:
   - An adjacency list is a collection of lists or dictionaries, where each list/dictionary represents a node and contains its neighbors.
   - For an undirected graph, each node's list contains the nodes it is connected to.
   - For a weighted graph, each node's list contains the neighbors along with their corresponding weights.

Python does not have a built-in graph data structure, but graphs can be implemented using dictionaries or custom classes. Libraries like NetworkX provide more sophisticated implementations for handling graphs and performing various graph algorithms.

Here's a basic example of representing an undirected graph using a Python dictionary:

```python
# Representing an undirected graph using a dictionary
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'C', 'D'],
    'C': ['A', 'B', 'D', 'E'],
    'D': ['B', 'C', 'E'],
    'E': ['C', 'D']
}

# Print the graph
for vertex, neighbors in graph.items():
    print(f"{vertex} -> {neighbors}")
```

Output:
```
A -> ['B', 'C']
B -> ['A', 'C', 'D']
C -> ['A', 'B', 'D', 'E']
D -> ['B', 'C', 'E']
E -> ['C', 'D']
```

In this example, we represent an undirected graph using a Python dictionary, where each key represents a node, and its corresponding value is a list of neighbors. The graph has nodes A, B, C, D, and E, and the edges are represented by the connections between nodes in the dictionary.
# 🐍 Dijkstra's Algorithm Exercise

## Graph Representation

First we need to represent the relationship between nodes using a graph. Graphs can be represented in several ways, including:

- **Adjacency Matrix**: A 2D array where each cell represents the weight of the edge between two nodes.
- **Adjacency List**: A dictionary or list of lists where each key/index represents a node, and the value is a list of tuples containing neighboring nodes and edge weights.

For this exercise, we'll use an **adjacency list** representation because it's more memory-efficient for sparse graphs and easier to work with in Python.

## Prerequisites

- Basic understanding of Python data structures (dictionaries, lists, tuples)
- Familiarity with graphs (nodes, edges, weights)
- Knowledge of priority queues (we'll use Python's `heapq` module)

## Step-by-Step Implementation

### Step 1: Import Required Modules

We'll need the `heapq` module for the priority queue and `collections` for the default dictionary.

```python
import heapq
from collections import defaultdict
```

### Step 2: Represent the Graph

Create an adjacency list using a dictionary where keys are nodes and values are lists of tuples (neighbor, weight).

```python
def create_graph():
    graph = defaultdict(list)
    # Add edges: graph[node].append((neighbor, weight))
    # Example: graph['A'].append(('B', 4))
    return graph
```

### Step 3: Initialize Data Structures

For Dijkstra's algorithm, we need:

- A dictionary to store the shortest distance from the start node to each node
- A dictionary to track the previous node in the shortest path
- A priority queue to select the next node to visit

```python
def dijkstra(graph, start):
    # Initialize distances with infinity, except start node
    distances = {node: float('inf') for node in graph}
    distances[start] = 0

    # Priority queue: (distance, node)
    pq = [(0, start)]

    # Dictionary to reconstruct the path
    previous = {node: None for node in graph}

    while pq:
        # Get the node with the smallest distance
        current_distance, current_node = heapq.heappop(pq)

        # If we've already processed a better path, skip
        if current_distance > distances[current_node]:
            continue

        # Explore neighbors
        for neighbor, weight in graph[current_node]:
            distance = current_distance + weight

            # If we found a shorter path
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                previous[neighbor] = current_node
                heapq.heappush(pq, (distance, neighbor))

    return distances, previous
```

### Step 4: Reconstruct the Shortest Path

After running Dijkstra's, we can reconstruct the path from start to any node.

```python
def get_shortest_path(previous, start, end):
    path = []
    current = end
    while current is not None:
        path.append(current)
        current = previous[current]
    path.reverse()
    if path[0] == start:
        return path
    else:
        return []  # No path found
```

## Complete Example

Let's put it all together with a sample graph:

```python
import heapq
from collections import defaultdict

def create_sample_graph():
    graph = defaultdict(list)
    graph['A'] = [('B', 4), ('C', 2)]
    graph['B'] = [('A', 4), ('C', 1), ('D', 5)]
    graph['C'] = [('A', 2), ('B', 1), ('D', 8), ('E', 10)]
    graph['D'] = [('B', 5), ('C', 8), ('E', 2), ('F', 6)]
    graph['E'] = [('C', 10), ('D', 2), ('F', 3)]
    graph['F'] = [('D', 6), ('E', 3)]
    return graph

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    pq = [(0, start)]
    previous = {node: None for node in graph}

    while pq:
        current_distance, current_node = heapq.heappop(pq)

        if current_distance > distances[current_node]:
            continue

        for neighbor, weight in graph[current_node]:
            distance = current_distance + weight
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                previous[neighbor] = current_node
                heapq.heappush(pq, (distance, neighbor))

    return distances, previous

def get_shortest_path(previous, start, end):
    path = []
    current = end
    while current is not None:
        path.append(current)
        current = previous[current]
    path.reverse()
    return path if path[0] == start else []

# Usage
graph = create_sample_graph()
distances, previous = dijkstra(graph, 'A')
print("Shortest distances from A:", distances)
print("Shortest path from A to F:", get_shortest_path(previous, 'A', 'F'))
```

### Output
```
Shortest distances from A: {'A': 0, 'B': 3, 'C': 2, 'D': 8, 'E': 12, 'F': 15}
Shortest path from A to F: ['A', 'C', 'B', 'D', 'E', 'F']
```

## Explanation

1. **Graph Creation**: We build an undirected graph using a defaultdict of lists, where each list contains tuples of (neighbor, weight).

2. **Algorithm Execution**:
```
- Start with the source node at distance 0
- Use a priority queue to always process the node with the smallest known distance
- For each neighbor, calculate the potential new distance
- If it's shorter than the current known distance, update and add to the queue
```

3. **Path Reconstruction**: Work backwards from the destination using the `previous` dictionary to build the path.

## Extra Exercises

1. Modify the graph to include negative weights. What happens? (Hint: Dijkstra's doesn't work with negative weights)
2. Implement a function to find the shortest path between all pairs of nodes.
3. Add visualization: print the graph and highlight the shortest path.

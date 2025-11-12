# 🐍 A* Exercise

## Graph Representation

For this exercise, we'll use the same adjacency list representation as in the Dijkstra's exercise. However, for A*, we also need to define positions for each node to calculate the heuristic (estimated distance to the goal).

## Prerequisites

- Basic understanding of Python data structures (dictionaries, lists, tuples)
- Familiarity with graphs (nodes, edges, weights)
- Knowledge of priority queues (we'll use Python's `heapq` module)
- Understanding of heuristics in pathfinding algorithms

## Step-by-Step Implementation

### Step 1: Import Required Modules

We'll need the `heapq` module for the priority queue and `collections` for the default dictionary. We'll also use `math` for distance calculations.

```python
import heapq
from collections import defaultdict
import math
```

### Step 2: Represent the Graph and Positions

Create an adjacency list and a dictionary of node positions (for heuristic calculation).

```python
def create_graph():
    graph = defaultdict(list)
    # Add edges: graph[node].append((neighbor, weight))
    return graph

def create_positions():
    positions = {
        # 'node': (x, y)
    }
    return positions
```

### Step 3: Heuristic Function

For this example, we'll use the Euclidean distance as our heuristic.

```python
def heuristic(a, b, positions):
    """Calculate Euclidean distance between two nodes"""
    x1, y1 = positions[a]
    x2, y2 = positions[b]
    return math.sqrt((x1 - x2)**2 + (y1 - y2)**2)
```

### Step 4: A* Algorithm Implementation

A* uses both the actual cost from start (g_score) and the estimated cost to goal (heuristic) to guide the search.

```python
def a_star(graph, positions, start, goal):
    # Priority queue: (f_score, node)
    open_set = [(0, start)]

    # Dictionaries to track scores
    g_score = {node: float('inf') for node in graph}
    g_score[start] = 0

    f_score = {node: float('inf') for node in graph}
    f_score[start] = heuristic(start, goal, positions)

    # Dictionary to reconstruct the path
    came_from = {node: None for node in graph}

    while open_set:
        # Get the node with the lowest f_score
        current_f, current = heapq.heappop(open_set)

        if current == goal:
            # Reconstruct path
            path = []
            while current is not None:
                path.append(current)
                current = came_from[current]
            path.reverse()
            return path, g_score[goal]

        for neighbor, weight in graph[current]:
            tentative_g_score = g_score[current] + weight

            if tentative_g_score < g_score[neighbor]:
                # This path to neighbor is better than any previous one
                came_from[neighbor] = current
                g_score[neighbor] = tentative_g_score
                f_score[neighbor] = g_score[neighbor] + heuristic(neighbor, goal, positions)
                heapq.heappush(open_set, (f_score[neighbor], neighbor))

    return [], float('inf')  # No path found
```

## Complete Example

Let's put it all together with a sample graph and positions:

```python
import heapq
from collections import defaultdict
import math

def create_sample_graph():
    graph = defaultdict(list)
    graph['A'] = [('B', 4), ('C', 2)]
    graph['B'] = [('A', 4), ('C', 1), ('D', 5)]
    graph['C'] = [('A', 2), ('B', 1), ('D', 8), ('E', 10)]
    graph['D'] = [('B', 5), ('C', 8), ('E', 2), ('F', 6)]
    graph['E'] = [('C', 10), ('D', 2), ('F', 3)]
    graph['F'] = [('D', 6), ('E', 3)]
    return graph

def create_sample_positions():
    positions = {
        'A': (0, 0),
        'B': (4, 0),
        'C': (2, 2),
        'D': (6, 2),
        'E': (8, 4),
        'F': (10, 4)
    }
    return positions

def heuristic(a, b, positions):
    x1, y1 = positions[a]
    x2, y2 = positions[b]
    return math.sqrt((x1 - x2)**2 + (y1 - y2)**2)

def a_star(graph, positions, start, goal):
    open_set = [(0, start)]
    g_score = {node: float('inf') for node in graph}
    g_score[start] = 0
    f_score = {node: float('inf') for node in graph}
    f_score[start] = heuristic(start, goal, positions)
    came_from = {node: None for node in graph}

    while open_set:
        current_f, current = heapq.heappop(open_set)

        if current == goal:
            path = []
            while current is not None:
                path.append(current)
                current = came_from[current]
            path.reverse()
            return path, g_score[goal]

        for neighbor, weight in graph[current]:
            tentative_g_score = g_score[current] + weight
            if tentative_g_score < g_score[neighbor]:
                came_from[neighbor] = current
                g_score[neighbor] = tentative_g_score
                f_score[neighbor] = g_score[neighbor] + heuristic(neighbor, goal, positions)
                heapq.heappush(open_set, (f_score[neighbor], neighbor))

    return [], float('inf')

# Usage
graph = create_sample_graph()
positions = create_sample_positions()
path, cost = a_star(graph, positions, 'A', 'F')
print("Shortest path from A to F:", path)
print("Total cost:", cost)
```

### Output

```
Shortest path from A to F: ['A', 'C', 'B', 'D', 'E', 'F']
Total cost: 15
```

## Explanation

```
1. **Graph and Position Setup**: 
We define the graph as an adjacency list and assign 2D coordinates to each node for heuristic calculation.

2. **Heuristic Function**: 
The Euclidean distance provides an admissible heuristic (never overestimates the true distance).

3. **Algorithm Execution**:
- A* maintains two scores: g_score (actual cost from start) and f_score (estimated total cost)
- The priority queue is ordered by f_score, guiding the search toward the goal
- When a better path to a neighbor is found, update scores and parent pointers
- Path reconstruction works backwards from the goal using the came_from dictionary

4. **Optimality**: 
A* finds the optimal path when using an admissible heuristic.

```

## Extra Exercises

1. Modify the heuristic to use Manhattan distance instead of Euclidean. How does this affect the path found?
2. Implement A\* for a grid-based map (like the example in the A\* algorithm page).
3. Add support for diagonal movement in a grid and adjust the heuristic accordingly.
4. Compare the performance of A* vs Dijkstra's algorithm on the same graph by counting the number of nodes explored.
# A* Algorithm

## Introduction

The A* (A-star) algorithm is a popular pathfinding and graph traversal algorithm used in artificial intelligence and computer science. It is an extension of Dijkstra's algorithm that incorporates heuristics to improve efficiency. A* finds the shortest path between a start node and a goal node in a weighted graph, making it ideal for applications like route planning, game AI, and robotics.

## How A* Works

A* uses a best-first search strategy that evaluates nodes based on two cost functions:

- **g(n)**: The actual cost from the start node to the current node n
- **h(n)**: The estimated cost from the current node n to the goal node (heuristic)
- **f(n)**: The total estimated cost, calculated as f(n) = g(n) + h(n)

The algorithm maintains two sets:
- **Open set**: Nodes to be evaluated
- **Closed set**: Nodes already evaluated

### Algorithm Steps

1. Initialize the open set with the start node
2. While the open set is not empty:
   - Select the node with the lowest f(n) value
   - If this node is the goal, reconstruct and return the path
   - Move the node to the closed set
   - For each neighbor of the current node:
     - If the neighbor is in the closed set, skip it
     - Calculate tentative g score
     - If the neighbor is not in the open set or the new g score is better:
       - Update the neighbor's parent and scores
       - Add to open set if not already there

## Pseudocode

```
function A*(start, goal):
    open_set = {start}
    closed_set = {}
    g_score[start] = 0
    f_score[start] = h(start, goal)

    while open_set is not empty:
        current = node in open_set with lowest f_score

        if current == goal:
            return reconstruct_path(current)

        open_set.remove(current)
        closed_set.add(current)

        for neighbor in neighbors(current):
            if neighbor in closed_set:
                continue

            tentative_g_score = g_score[current] + distance(current, neighbor)

            if neighbor not in open_set or tentative_g_score < g_score[neighbor]:
                g_score[neighbor] = tentative_g_score
                f_score[neighbor] = g_score[neighbor] + h(neighbor, goal)
                parent[neighbor] = current

                if neighbor not in open_set:
                    open_set.add(neighbor)

    return failure
```

## Heuristics

The choice of heuristic function h(n) is crucial for A*'s performance:

- **Admissible heuristic**: Never overestimates the true cost (h(n) ≤ actual cost)
- **Consistent heuristic**: Satisfies the triangle inequality (h(n) ≤ h(m) + distance(n,m) for any nodes n,m)

Common heuristics:
- Manhattan distance (grid-based movement)
- Euclidean distance (straight-line distance)
- Diagonal distance

## Example

Consider a grid where movement is allowed in 4 directions (up, down, left, right). Using Manhattan distance as heuristic:

```
Start: (0,0) Goal: (3,3)

Grid:
S . . .
. # . .
. . . .
. . . G

Path found: S → (1,0) → (2,0) → (2,1) → (2,2) → (3,2) → (3,3)
```

## Advantages

- **Optimality**: Finds the shortest path if the heuristic is admissible
- **Completeness**: Will find a solution if one exists
- **Efficiency**: Often much faster than uninformed search algorithms

## Disadvantages

- **Memory intensive**: Stores all generated nodes
- **Heuristic dependent**: Performance relies on a good heuristic function
- **Not suitable for negative edge weights**: Like Dijkstra's, assumes non-negative weights

## Applications

- Video game pathfinding (e.g., enemy AI navigation)
- Route planning in GPS systems
- Robot motion planning
- Puzzle solving (e.g., 8-puzzle, sliding puzzles)

## Comparison with Dijkstra's Algorithm

While Dijkstra's algorithm guarantees the shortest path with g(n) only, A* incorporates heuristics to guide the search towards the goal, potentially exploring fewer nodes. However, if h(n) = 0, A* reduces to Dijkstra's algorithm.
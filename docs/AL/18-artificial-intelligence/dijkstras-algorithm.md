# Dijkstra's Algorithm

<iframe width="560" height="315" src="https://www.youtube.com/embed/bZkzH5x0SKU" title="Dijkstra by FelixTechTips" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Summary of Dijkstra's Algorithm

The algorithm calculates the shortest path from a starting node to every other node in a graph connected by weighted edges. A common application is in digital mapping, where nodes are cities and edges are routes, allowing calculation of distances between them.

The video demonstrates the process using an example graph, starting from node 'A'.

### 1. Initial Setup

Two main pieces of information are tracked:

- Visited/Unvisited Nodes: A list of all nodes is initially marked as unvisited [00:47].
- Distance Table: A table is created to store the current shortest distance and the previous node leading to that distance for every node [01:00].
- The starting node ('A') is set to a distance of 0.
- All other nodes are set to a distance of infinity [01:26].

### 2. Iterative Process

The algorithm repeats the following steps until all nodes are visited:

- Start at the current node (initially 'A'). Calculate the distance to all of its unvisited neighbors.
- Update Distances: If the new calculated distance to a neighbor is shorter than its current distance in the table, the table is updated with the new shorter distance and the current node is recorded as the previous node.
- Mark as Visited: The current node is marked as visited and removed from the unvisited list.
- Choose the Next Node: The next current node is chosen from the unvisited list—it must be the node with the current minimal shortest distance.

### 3. Final Result and Path Reconstruction

- Once all nodes are visited, the table contains:
- The shortest distance from the starting node ('A') to every other node in the graph.
- The shortest path can be reconstructed by starting at the destination node and tracing back its previous nodes until the start node is reached. 

For the path from A to C, the final result is a distance of 12, following the path:
> A → B → D → F → C.

## Dijkstra Uses

The algorithm is widely used in:

- Network routing
- GPS navigation systems
- Path planning for autonomous robots
- AI pathfinding in video games


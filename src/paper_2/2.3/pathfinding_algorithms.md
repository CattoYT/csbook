# Pathfinding Algorithms
![GitHub last commit](https://img.shields.io/github/last-commit/cattoyt/csbook?path=src%2Fpaper_2%2F2.3%2Fpathfinding_algorithms.md&label=Last%20updated)

## Graphs
- A **graph** in data structures is a collection of nodes (or vertices) and edges that connect pairs of nodes. It can be used to represent various real-world problems, such as road networks, social networks, and computer networks.

![Graph Example](https://mathinsight.org/media/image/image/small_undirected_network_labeled.png)
<sub><a href="https://mathinsight.org/network_introduction">Source</a></sub>

- A **weighted graph** is a graph in which each edge has an associated numerical value (weight) that represents the cost, distance, or time required to traverse that edge. Weighted graphs are commonly used in pathfinding algorithms to find the shortest or least costly path between nodes.

## Dijkstra's Algorithm
- **Dijkstra's algorithm** is a popular algorithm for finding the shortest path between nodes in a graph. It was developed by Dutch computer scientist Edsger W. Dijkstra in 1956. The algorithm works by iteratively selecting the node with the smallest tentative distance, updating the distances of its neighbors, and marking it as visited until the destination node is reached or all nodes have been visited. The algorithm guarantees that the shortest path is found, as long as all edge weights are non-negative. Dijkstra's algorithm has a time complexity of O(V^2) for a graph with V vertices, but it can be improved to O(E + V log V) using a priority queue.

1. We begin by locating the starting node.
2. We will then assign the distance values to each node from this one.
    1. At the first note we assign the distance value of 0, as it is the starting node.
    2. All other nodes will be assigned a distance value of infinity, as we do not know their distances from A yet.
3. We then create a **priority queue** (nothing to do with 2b2t) to keep track of the nodes to be explored, starting with the starting node (so the priority queue will contain the starting node with a distance of 0, and everything else with a distance of infinity).
4. We begin to traverse the graph, starting with the starting node and exploring its neighbors. For each neighbor, we calculate the tentative distance from the starting node and update the distance value if it is smaller than the current value (which it will be because it's infinity).
5. We move the starting node to the list of shortest paths, removing it from the priority queue. 
6. We can then reprioritise the queue, in ascending order of distance values, and repeat the process with the next node in the queue. We will continue this process until we reach the destination node or have explored all nodes in the graph.

> [!NOTE]
> [This video](https://www.youtube.com/watch?v=GazC3A4OQTE) may be worth a watch if a text-based explanation is confusing.

## A* Algorithm
- The **A\* algorithm** is a popular pathfinding and graph traversal algorithm that is used to find the shortest path between nodes in a graph. It is an improvement over Dijkstra's algorithm, as it uses a heuristic function to **estimate the cost of reaching the goal node from the current node**. This allows A* to prioritise nodes that are more likely to lead to the goal, resulting in faster search times.
- For example, if you were going from Manchester to Liverpool, the fastest route is probably not via Birmingham, so the A* algorithm would prioritise nodes that are closer to Liverpool, rather than exploring all possible paths equally.
- When calculating the distance between two nodes using the A* algorithm, the approximate cost is added onto the actual cost, which is then used to determine which node is visited next.
- Nodes with very high total costs are ignored to make the algorithm faster.
- When working in an exam, extra columns for heuristic values and total costs should be added to the table.

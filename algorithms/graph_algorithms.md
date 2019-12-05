# Graph Algorithms
## Overview
## Resources
## Questions
1. :star: What is the order of the running time of depth-first search in a connected graph?
1. :star: What is the order of the running time of breadth-first search in a connected graph?
1. :star: Breadth-first search uses a queue to maintain the frontier. What does Dijkstra's algorithm use?
1. :star: When is Dijkstra's algortihm better than breadth-first search for finding shortest paths?
1. :star: What is the order of the running time for the Floyd-Warshall all-pairs shortest-path algorithm?
1. :star::star: Give a topologial sort of the graph below.

    ![There are 6 vertices. 0 points to 3, 1 to 0 and 4, 2 to 1 and 5, 4 to 3, and 5 to 4.](toposort.svg)
1. :star::star: Draw the minimum spanning tree of the graph below.

    ![There are 4 vertices, labeled A through D. The weight along the edge AB is 1, AC is 2, AD is 6, BC is 3, BD is 4, and CD is 5.](mst.svg)
    
## Answers
1. ![order V plus E](https://latex.codecogs.com/svg.latex?\Theta(V+E))
1. ![order V plus E](https://latex.codecogs.com/svg.latex?\Theta(V+E))
1. When the graph is weighted.
1. A priority queue.
1. ![order V cubed](https://latex.codecogs.com/svg.latex?\Theta(V^3))
1. One answer is 2, 1, 5, 4, 0, 3.
1.
    ![The edges of weights 1, 2, and 4 are included.](mst_solved.svg)

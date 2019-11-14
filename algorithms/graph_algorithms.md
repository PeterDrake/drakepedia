# Graph Algorithms
## Overview
## Resources
## Questions
1. :star: What is the order of the running time of breadth-first search in a connected graph?
1. :star: When is Dijkstra's algortihm better than breadth-first search for finding shortest paths?
1. :star: What is the order of the running time for the Floyd-Warshall all-pairs shortest-path algorithm?
1. :star::star: Give a topologial sort of the graph below.

    ![There are 6 vertices. 0 points to 3, 1 to 0 and 4, 2 to 1 and 5, 4 to 3, and 5 to 4.](toposort.svg)
## Answers
1. ![order V plus E](https://latex.codecogs.com/svg.latex?\Theta(V+E))
1. When the graph is weighted.
1. ![order V cubed](https://latex.codecogs.com/svg.latex?\Theta(V^3))
1. One answer is 2, 1, 5, 4, 0, 3.

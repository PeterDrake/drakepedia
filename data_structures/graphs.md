# Graphs
## Terminology
A *graph* consists of a set of *vertices* and a set of *edges*. Each edge connects two vertices.

In the graph below, there are eight vertices, numbered 0 through 7. There is an edge connecting vertices 0 and 1, but no edge connecting 1 and 2.

![Edges are 0-1, 0-4, 1-4, 1-5, 2-5, 2-6, 3-7, 4-5, 5-6, and 6-7](graph.svg)

The *neighbors* of a vertex are the vertices directly connected to it by edges. In the graph above, 4's neighbors are 0, 1, and 5.

Several variations exist, including *directed* graphs (where the edges are one-way arrows) and *weighted* graphs (where there is a number indicating cost or capacity associated with each edge).
## Representation
### Adjacency matrix
An *adjacency matrix* or *neighbor matrix* is a two-dimensional array of booleans, with true at position ![i, j](https://latex.codecogs.com/svg.latex?i\,j) if there is an edge connecting vertex ![i](https://latex.codecogs.com/svg.latex?i) to vertex ![j](https://latex.codecogs.com/svg.latex?j). The adjacency matrix for the graph above is shown below (with shaded boxes indicating true and unshaded boxes indicating false).

![8 by 8 matrix as described above](adjacency_matrix.svg)

### Adjacency lists
In a graph with ![v](https://latex.codecogs.com/svg.latex?v) vertices, the amount of memory used by an adjacency matrix is in ![order v squared](https://latex.codecogs.com/svg.latex?\Theta(v^2)). This is fine for graphs that are small or very *dense* (that is, having close to every possible edge), but in practice there is a more efficient representation.

## Additional Resources
### Online
### Print
## Questions
1. :star: What is the singular form of the plural noun "vertices"?
## Answers
2. "vertex"


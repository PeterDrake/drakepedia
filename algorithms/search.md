# Search
## Overview
## Additional Resources
### Online
### Print
## Questions
1. :star::star: The methods below, as part of a `Graph` class, are supposed to return an array that is true at those indices corresponding to vertices that can be reached from `start`. As written, it goes into an infinite loop for some graphs. Supply the missing code.
    ```java
    public boolean[] reachable(int start) {
        return reachable(start, new boolean[neighbors.length]);
    }

    public boolean[] reachable(int start, boolean[] visited) {
        // Something is missing here
        visited[start] = true;
        for (int n : neighbors[start]) {
            reachable(n, visited);
        }
        return visited;
    }
    ```
## Answers
1.
    ```java
    if (visited[start]) {
        return visited;
    }
    ```
    

# Omitting Needless Code
## Overview
## Additional Resources
### Online
### Print
## Questions
1. :star::star: Using an array, refactor the method below to avoid the long if/else chain.
    ```java
    public String toString() {
        if (n == 0) {
            return "red";
        } else if (n == 1) {
            return "orange";
        } else if (n == 2) {
            return "yellow";
        } else if (n == 3) {
            return "green";
        } else if (n == 4) {
            return "blue";
        } else if (n == 5) {
            return "indigo";
        } else {
            return "violet";
        }
    }
    ```
## Answers
1.
    ```java
    public String toString() {
        String[] colors = {"red", "orange", "yellow", "green", "blue", "indigo", "violet"};
        return colors[n];
    }
    ```
    It would be even better to declare `COLORS` as a constant so that it doesn't have to be created each time `toString` is called.

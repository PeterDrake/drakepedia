# Union-Find
## Overview
## Resources
## Questions
1. :star: When using a forest of trees to represent disjoint sets, what tree shape is more efficient: tall and narrow, or short and wide?
1. :star::star: The array below represents the forest of trees used by the quick-union data structure for disjoint sets. Draw the array after merging the sets containing 0 and 5. Merge the smaller tree into the larger, but don’t worry about path compression.

    ![The numbers in the array are 2, 4, 2, 2, 4, 1, 4, 1, 8.](union_find.svg)
## Answers
1. Short and wide.
1.
    ![Element 2 of the array is now 4](union_find_after_merge.svg)

# Binary Search Trees
## Overview
## Resources
## Questions
1. :star: What is the order of the average running time of the search operation on a binary search tree?
1. :star::star: Draw the binary search tree below after deleting 4.

    ![4 is the root. Its children are 2 and 6. 2's children are 1 and 3. 6's children are 5 and 7.](bst.svg)
1. :star::star: Draw the red-black tree below after inserting 2.

    ![5 is the black root. Its children, both black, are 3 and 7. 3 has a red left child 1.](rbtree.svg)
1. :star::star: Draw the red-black tree below after inserting 3.

    ![6 is the black root. Its children are 4, red, and 7, black. 4's children, both black, are 2 and 5. 2 has a red left child 1.](rbtree2.svg)
## Answers
1. ![order n log n](https://latex.codecogs.com/svg.latex?\Theta(n\log&space;n))
1.
    ![5 is the root. Its children are 2 and 6. 2's children are 1 and 3. 6 has only a right child, 7.](bst_after_deletion.svg)
1.
    ![5 is the black root. Its children are 2, red, and 7, black. 2's children, both black, are 1 and 3.](rbtree_after_deletion.svg)
1.
    ![All nodes are black and the tree is perfect. 4 is the roor, 2 and 6 are its children, and 1, 3, 5, and 7 are its grandchildren.](rbtree2_after_deletion.svg)

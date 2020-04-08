# Trees

Made up of *nodes* and *edges*.

Trees are connected, acyclic (and typically directed) graphs:
- __Connected:__ All nodes are linked into one component
- __Acyclic:__ No circular traversal between any of the nodes
- __Directed:__ Edges can only be traversed in one direction
<img src="../Pictures/tree2.png" width="400">

Branches and leaves can also be referred to as internal and external nodes, respectively.

## Binary Tree

A *binary tree* has at most two children per node (left & right child).

Traversed recursively - every subtree is also tree itself. There are 3 types of traversal:
- __Preorder - (PLR):__ Root printed first
- __Inorder - (LPR):__ Root printed in the middle
- __Postorder - (LRP):__ Root printed last

## Binary Search Tree

For every node, the left subtree contains values less than the node, and the right subtree contains values greater than the node.

The search, insertion, and deletion of elements all take around O(log n) time.

This tree should be balanced to be efficient. \
![](../Pictures/bst.png)

The tree can be rotated to be balanced.

<details>
	<summary>Implementation</summary>



</details>
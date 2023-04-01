
AVL trees are binary search trees that has a height balance property. Named for Adelson-Velesky, Landis tree. The height balance property states that
- for every internal node v, the heights of the children of v differ by at most 1
- rotations are used to solve tree differences
The height balance property makes sure that all operations are $\log(n)$.

The minimum number of nodes for an AVL tree of height $h$ is
$$
n(h) = \begin{cases}
0 & h = 0 \\
1 & h = 1 \\
1 + n(h - 1) + n(h - 2) & h > 1
\end{cases}
$$
## Rebalancing/Rotations
Define a balance factor of a node n:
```cpp
int balance(n) {
	return height(n->left) - height(n->right);
}
```

When inserting an element, look at the balance factor of the path leading from the root to the new element. Rebalance each node along the path if needed.

A rotation is a way to fix balance involving only three pointers and two nodes. It ends up being a swap of a parent and one of its children, and preserves the BST ordering property. Rotations are $O(1)$.
### Right Rotation
- use this when the balance factor of the root node is positive
- Change the left child and the parent's roles - the left child will now be the parent and the parent will be the right child. 
- Take the left child's right child and make this the parent's new left child.
### Left Rotation
- use this when the balance factor of the root node is negative
- Change the right child and the paren'ts roles - the right child will now be the parent and the parent will be the left child.
- Take the right child's left child and make this the parent's new right child.

![[Pasted image 20230320143203.png]]

When there is a sign change in balance factor (a zig zag), you need to rotate around the middle element **first**, then rotate around the root.

- If the final element of a zig zag goes left, you rotate right around the middle, then rotate left around the previous first.
- If the final element of a zig zag goes right, you rotate left around the middle, then rotate right around the previous first.

## AVL Tree Removal
1. Do the same thing as normal BST removal
2. Travel up the tree from the parent of the removed node
	1. at every unbalanced node encountered, rotate if needed
	2. go all the way up to the root
Removals can cause multiple ancestors to be unbalanced. Worst case is that you need $O(\log n)$ fixes for each removal.
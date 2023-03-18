# Tree Definition
A tree is a graph
- which is connected
- has no cycles
- any 2 nodes are connected by a unique shortest path

A **directed tree** has designates child and parent relationships.
An **ordered tree** has a linear ordering for the children of each node.
A **rooted tree** has a selected node as a root. All edges are directed away from the root.

An **ancestor** is a parent of a parent. A **descendent** is a child of a child.
An **internal node** is a node with children. An **external node** is a node without children.

# Binary Trees
A **binary tree** has at most two children per parent. It is an ordered tree in which every node has at most two children.
## Array Implementation
Same thing as what we did in the heaps. Can have gaps, as long as you define something as undefined. Can be very space wasting with lots of gaps.
## Pointer Based Implementation
A node contains a key, and its children:
```cpp
template <class KEY>
struct Node {
	Key key;
	Node *left = nullptr;
	Node *right = nullptr;
	Node(const KEY &k) : key{k} {}
}; // Node{}
```

## Converting General Trees to Binary Trees
This can be done by taking the left child of any node and using this as the left child of the node. On the right child of this new node, tack on all the rest of the siblings:
![[Pasted image 20230315142441.png]]
# Binary Search Tree
The key of any node is
- greater than the keys of all nodes in the left
- lees than or equal to the keys of all nodes in the right
An inorder traversal of a BST is traversing sorted data.
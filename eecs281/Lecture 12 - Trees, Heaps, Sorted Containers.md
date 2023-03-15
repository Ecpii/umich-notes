**Date**: 2023-02-09

# Trees
Properties of trees can be defined recursively:
```cpp
height(empty) = 0;
height(node) = max(height(left_child), height(right_child)) + 1;

size(empty) = 0;
size(node) = size(left_child) + size(right_child);

depth(empty) = 0;
depth(node) = depth(parent + 1);
```
Note that depth and height are not the same, though the *maximum* depth and height are the same.

## Complete Trees
A *complete* tree means every level (except possibly the last) is completely filled. Furthermore, all the nodes are filled from left to right. A complete tree can be represented as an array or other contiguous memory easily:
```
    A
   B C
  D E
is
[0, A, B, C, D, E]
```
We index starting at 1 because math is easier from it, the zeroth index is just a dummy element. Specifically the math is:
- to find a parent, divide an element's index by 2
- to find left child, multiply by 2
- to find right child, multiply by 2, then add 1
- to find what leaf nodes you have, take the last element, divide it by 2, and every index greater than that is a leaf node
# Heaps
Heaps are containers that allow you to get maximum elements quick. The root element is always greater than any of its children.
## Heap Ordering
> A tree is heap ordered if each node's priority is not greater than the priority of its parent.

A heap uses a complete heap ordered tree. A heap has the property that no element in it is greater than the root element.

Sorting is a superset of heap sorting. A valid heap is not necessarily a sorted array, but a sorted array is a valid heap.

## Heap Sort
You can use heap sort to sort heap-ordered data in $O(n\log n)$ time. You pop the highest element and switch it with the back of the heap. Decrease the size of the heap so you never see the formerly maximum element. Fix the remaining heap, rinse and repeat.
# Containers
Ordering is the property of a container to maintain the order of elements when other elements are removed or inserted - it maintains a stable ordering. This condition is necessary but not sufficient for sorted containers.
## Types of Containers
| Type                 | Distinctive Interfaces                                                                   |
| -------------------- | ---------------------------------------------------------------------------------------- |
| Container            | Supports `add()` and `remove()`                                                          |
| Searchable Container | Adds `find()`                                                                            |
| Sequential Container | Allows iteration in some order                                                           |
| Ordered Container    | Sequential container which maintains current order - you can arbitrarily insert anywhere |
| Sorted Container     | Sequential container with a pre-defined order - you can **not** arbitrarily insert everywhere                                                                                        |


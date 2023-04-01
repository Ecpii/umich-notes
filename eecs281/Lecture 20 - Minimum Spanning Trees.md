A minimum subgraph where the sum of the edge weights is minimal. An MST is also a tree, cycles are removed by removing edges with highest weight in the cycle. More than one MST can exist for a graph.
An MST:
- must include the unique shortest edge
- must include the second unique shortest edge
- may or may not include the third+ unique shortest edge
# Prim's Algorithm
Greedy algo to find an MST.
- Start with a vertex.
- Add the minimum edge.
- Repeat with the other end of that edge until no more undiscovered vertex.
## Implementation
For each vertex, keep
- `k_v` - has v been visited?
- `d_v` minimal edge weight to v
- `p_v` parent of v

Get a starting point and set `d_v` of that vertex to 0. Then,
- from the set of vertices for which `k_v` is false, select the vertext with the smallest tentative distance `d_v`
- set `k_v` to true
- for each vertex (w) adjacent to the one selected that has `k_w` false (not visited), check if `d_w` is greater than the distance between v and w. If it is, set `p_w` to v, and `d_w` to the distance from `v` to `w`
- repeat until all discovered
## Complexity
With linear search, the complexity is $O(V^2)$. With a heap, the complexity is $O(E\log E)$, which is not necessarily always better (use for sparse, not dense).
# Kruskal's Algorithm
Does the same thing as Prim's. This is edge-based, unlike Prim's, which is vertex based.
- Presort all edges
- try inserting in order of increasing weight
- if cycle, remove longest edge in that cycle
# Complexity
$O(E\log E)$ because of the sort. Use on sparse graphs $\implies O(E \log V)$.
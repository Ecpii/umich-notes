A graph $G = (V, E)$ is a set of vertices $V = {v_1, v_2, \ldots}$ together with a set of edges $E = {e_1, e_2, \ldots}$ that connect pairs of vertices. Edges are often respresented as ordered pairs of vertices ($e_m = (v_1, v_2)$).

Edges can connect a vertex to itself. This is called a *self-loop*.
Two edges can connect the same vertices. These are called *parallel edges*.

Graphs without either of the above are called *simple graphs*. Typically, graphs are assumed to be simple.

A **simple path** is a sequence of edges leading from one vertex to another with no vertex appearing twice.

A **connected graph** means that for any set of vertices in the graph, a simple path exists between them.

A **cycle** is a simple path that starts and ends at the same vertex.

# Edges
A directed graph is a graph where edges have direction (one way). The order of vertices in an edge definition is important here.

An undirected graph doesn't have direction for edges.

A weighted graphs associates numbers with each edge.

# Density
A complete graph connects every vertex to every other possible vertex. i.e. it has all possible edges, which means
$$
|E| = |V| * |V - 1| / 2 \approx |V|^2
$$

A dense graphs has *many* edges. Approximately $|V|^2$ edges. It is represented in a adjacency matrix.

A sparse graph has *few* edges. Approximately $|V|$ edges or many less than $|V|^2$ edges. Represented as an adjacency list.

# Representations
## Adjacency Matrix
An adjacency matrix is a matrix where the rows are vertices and the columns are also vertices. If there exists an edge connecting the row vertex and the column vertex, the value at that location is true. Otherwise false.

If using an undirected graph, an undericted adjmat needs $|V|^2 /2$ (symmetric) space, and a directed graph needs $|V|^2$ space.

## Adjacency List
An adjacency list is a linked list for each node that shows which nodes are directly connected. It should be treated as more of a stack than a linked list, since sequential items are not necessarily directly connected, they are all just directly connected to the head of the list.

Finding a vertex list takes $O(1)$ time, and finding an edge on a vertex list takes $O(E/V)$ time. The average cost for an individual vertex is $O(1 + E/V)$. The cost for processing all verticies is  $O(V + E)$.

A distance matrix/graph is the same as an adjacnecy matrix/graph, but the value of true and false are replaced with the cost/distance of each edge. No edges should be representated as infinity.
```cpp
#include <limits>
numeric_limits<double>::infinity(); // don't do math on this
numeric_limits<double>::max(); // don't use this for infinity
```
# Depth First Search
Can tell us if a path exist, will not always find the shortest path.
Maintain a stack, discover all connections and add them to the stack if not seen before. After discovering all, pop the top one and discover connections from that.

## Complexity
Called for each vertex at most once $O(V)$.
- For an adjacency list, $O(1 + E/V)$ to find connections. $O(V + E)$ total.
- For an adjacency matrix, $O(V)$ to find connections. $O(V)$ total.
# Breadth-First Search
Will find shortest if edges are unweighted, not always for weighted. Same process as DFS but use a queue.

## Complexity
Identical to DFS. (Queues and Stacks have same complexity for accessing from their optimal ends)
# Dijkstra's Algorithm
Find best path for weighted. Covered in [todo]
# Brute-Force
- simple
- obvious
- typically not efficient, but can be
# Greedy
- pick the best choice *just* based on the current state
- may not always be the best
- fast
## Checking Greedy Correctness
If a greedy step ever invalidates a best solution, the problem cannot be proven to be correct with greedy algorithms.
# Divide and Conquer
- divide problem into smaller problems of roughly equal size
- often recursive
- often log n
## Combine and Conquer
Start with smallest case and combine increasingly larger until size is n.
# Dynamic Programming
- remember partial solutions
- can make inefficient algorithms efficient
# Backtracking
- satisfy all given constraints somehow
- figure out what you did to do that

Like brute force, but prune searches that do not satisfy constraints
- if something breaks constraints, go back one step and try to do something else

Backtracking works **well** when the systems are
- highly constrained (high pruning, so less like brute-force)
- under cosntrained (easy to find a solution)
# Branch and Bound
same as backtracking but for optimization. get set of all solutions and find the one that is the best and boom (like brute-force).

Backtracking and Branch&Bound are both fallback algorithms, because they are more similar to brute force than anything and htuse less efficient.
# Planar Graph
A planar graph is a graph with no crossing edges
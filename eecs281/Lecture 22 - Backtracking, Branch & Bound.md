```lua
Algorithm checkNode(Node v)
	if (not promising(v))
		return;
	if (solution(v))
		return solution
	else
		for each node u adjacent to v
			checknode(u)
```

# Optimization
Rather than checking for the existance of a solution, we want to filter to the best solution. While backtracking, prune any solutions that are worse than the current accepted solutions.
```lua
Algorithm checkNode(Node v, Best currBest)
	Node u
	if (promising(v, currBest))
		if (solution(v)) then
			update(currBest)
		else
			for each child u of v
				checkNode(u, currBest)
	return currBest
```
The *bound* of branch and bound is how you find your estimates to prune. It is usually worth putting in any extra effort to get a good bound because the alternative to efficiency is $O(n!)$ and nothing else is that bad.
# Traveling Salesperson Problem
A **Hamiltonian Cycle** is a cycle that traverses each node exactly once. The TSP problem is finding the least cost hamiltonian cycle.
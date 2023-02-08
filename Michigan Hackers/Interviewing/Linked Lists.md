- Check for a null head when dealing with **any** linked list problem.
- Sometimes it may be easier to put a node before a list to trim out edge cases
	or so that you can do initialization stuff before you dive into the loop for the rest of the list
	remember to **delete the dummy pointer**
- the inverse may also be true, put nodes after the list
- slow/fast pointers - you can use this to find:
	- the midpoint / $\dfrac{1}{k}$ point
	- some number x offset from the end/beginning
	- a pattern with numbers at a specific offset from each other
## Moore's Voting Algorithm
**Objective**: find majority element in an unsorted array
**Time**: $\Theta(n)$ (linear)
**Space**: $\Theta(1)$ (constant)
Introduced in [[Lecture 7 - Containers]].

### Description
Start with two variables, e.g. `candidate = 0` and `count = 0`. Set `candidate` equal to the first element of the array, and `count` to 1. Proceed to the next element.
- If this element is different from the `candidate`, decrement the `count`. If the `count` ever reaches zero, reset `count` to 1 and change `candidate` to the current element.
- If this element is the `candidate`, increase the `count`.
### Example
```cpp
int mooresAlgorithm(int[] nums) {
	int candidate = 0;
	int count = 0;
	for (int num : nums) {
		if (count == 0) {
			candidate = num;
			count = 1;
		}
		count += (candidate == num) ? 1 : -1
	}
}
```
## Misra Gries Summaries
**Objective**: find all elements that occur more than $\dfrac{1}{k}$ of the time in the array.
**Time**: $\Theta(n)$ (linear)
**Space**: $\Theta(n/k)$ (linear)
Introduced in [[Lecture 7 - Containers]].

### Description
Make a dictionary of size `k`. For each item in the input array:
- if the item is in the dictionary's keys, increment the corresponding value in the dictionary
- if the item is not in the keys and the dictionary has fewer than k - 1 keys, add the item as a key to the dictionary with initial value 1
- otherwise (too many keys): decrement the value of each key in the dictionary by one - if this value gets to 0, remove this key
## Example
```python
# this doesn't actually work but i spent too much time on it
def misragGries(k: int, s: iter):
	res = {}
	for i in s:
		if i in res:
			res[i] += 1
		elif len(res) < k - 1:
			res[i] = 1
		else:
			origKeys = list(res.keys())
			for k in origKeys:
				res[k] -= 1
				if not res[k]:
					del res[k]
	return res
```
# Sorts
## Heap Sort
**Time**: $O(n\log n)$ (though it does have linear overhead if data is not pre heap-formatted)
**Space**: $O(1)$
Discussed in [[Lecture 11 - Trees, Heaps, Sorted Containers]] (2/9).

### Description
- Heap order the data (if not already)
- Switch the maximum element with the end element, and mark off the end of the heap to not include the last element (which you just "popped" off the heap)
- Fix the heap
- Repeat until sorted
## Example
using 1-indexed heap
```cpp
void heapsort(Item heap[], int n) {
	heapify(heap, n);
	for (int i = n; i >= 2; i--) {
		swap(heap[i], heap[1]);
		fixDown(heap, i - 1, 1);
	}
}
```
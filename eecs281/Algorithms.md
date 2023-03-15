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
# Bubble Sort
**Time**: Best case $O(n)$, average/worst case $O(n^2)$
**Space**: $O(1)$
## Description
For every pair of elements, switch them so that they resemble the right sorting order. Elements will bubble up to the end. Don't use this.

# Selection Sort
**Time**: $O(n^2)$
**Space**: $O(1)$
## Description
- split the list into a sorted and unsorted part
- iterate through the unsorted part
- take the minimum element
- swap it with the first element in the sorted part
- expand the sorted part
- repeat until no more unsorted part
## Example
```cpp
void selectionSort(int[] items, int size) {
	int sortBoundary = size - 1;
	while (true) {
		int currentExtrema = -1;
		for (int i = 0; i < sortBoundary; i++) {
			if (items[i] < items[currentExtrema]) {
				currentExtrema = i;
			}
		}
		swap(items[currentExrema], items[sortBoundary--]);
		if (!sortBoundary) {
			return;
		}
	}
}
```
# Insertion Sort
**Time**: $O(n)$ best, $O(n^2)$ average
**Space**: $O(1)$

## Description
traverse through the elements left -> right. for each element, shift it left until its in the right place.

# Merge Sort
**Time**: $O(n \log n)$
**Space**: $O(n)$

## Description
- keep splitting the list into smaller lists
- when you get to lists of size 1, switch the lists so that they are in the right order
- for each sublist, you merge the lists back together by looking at the top of each sublist and placing the minimum first

# Quicksort
**Time**: $O(n \log n)$, worst case $O(n^2)$
**Space**: $O(log n)$
not stable

## Description
- select a pivot
- put all elements greater than that pivot in one list, all elements smaller in another list
	- internally this is
	- swap the pivot with the 0 index element
	- create a `L` pointer and an `R` pointer
	- advance the `L` pointer from index 1 until it encounters something that shouldn't be in its partition
	- decrement the `R` pointer from index n - 1 until it encounters something that shouldn't be in its partition
	- swap the two elements once they have stopped
	- repeat until `L` and `R` cross
	- swap the pivot and the element pointed to by `R` (by now `R` points to an element lower than the pivot)
- quicksort the sides of both lists

# Heap Sort
**Time**: $O(n\log n)$ (though it does have linear overhead if data is not pre heap-formatted)
**Space**: $O(1)$
Discussed in [[Lecture 12 - Trees, Heaps, Sorted Containers]] (2/9).

## Description
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
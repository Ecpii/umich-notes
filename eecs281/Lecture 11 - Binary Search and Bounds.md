## Optimization Tips
- check `<` first, then `>`, then `==` (equality is least likely to be triggered)
## `lower_bound`
This function looks for the first thing in a sorted list that is not less than what you are looking for. If the item is in the list, then it willi get the item.
```cpp
int lowerBound(double a[], double val, int left, int right) {
	while (right > left) {
		int mid = left + (right - left) / 2;

		if (a[mid] < val)
			left = mid + 1;
		else
			right = mid;
	}

	return left;
}
```
This is slightly better than binary search because you *always* do two comparisons per search.
## STL Functions
- `binary_search()` returns a `bool` whether the item is in there or not (not likely useful).
- `lower_bound()` returns the first item not less than the target
- `upper_bound()` returns the first item greater than the target (will not find the target)
- `equal_range()` can get you all the items equal to the target
# Sets

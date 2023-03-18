A *way* is a particular location that a piece of memory could exist in.  In a k-way cache, you need to keep track of when a way is accessed in order to correclty implement LRU.

# k-Way Cache
Hold a $\log_2 k$ bit counter per line. When a way is accessed, set it to the maximum value, and decrement all other counters. When a replacement is needed, find the way with counter = 0.
# Stores
- If the memory location is in the cache
	- update the cache. (prevent data hazards)
	- *write-through policy* determines whether to also write to memory
- If not:
	- *allocate-on-write policy* determines whether we want to put it in the cache or just put it only in memory
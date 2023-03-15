# Cache Structure
| Valid | Tag | Data|
|---|---|---|
| is the association valid? (i.e. is this not just initialization value) | the address | the data|

# Locality
**Temporal locality** refers to the trend that if you fetch data once, you are likely to use it often in the next few instructions. Conversely, if you don't fetch a piece of data, you are likely not going to use it.

**Space locality**

## Working Through Cache
Keep track of the *least recently used* value (LRU), and:
- when you have a cache miss, replace the LRU with the new value you fetch
- when you have a hit, make sure the LRU is not the value that is accessed
# Average Access Latency
$$
\text{cycles per reference} = \text{cache latency} + \text{memory latency} * \text{miss rate}
$$
## Improving Latency
- imrpove memory access latency
	- (typically not controllable from this scope)
- improve cache access latency
	- (can be improved by making cache simpler)
- improve cache hit rate
	- **what we should do**
	- make it larger?
## Reformatting Cache 
We want to decrease the overhead of how much of the cache our tag takes up. This can be accomplished by storing more data per each entry. A simple scheme for doing this is by grouping contiguous groups of pairs as tag addresses. Therefore, the number of tag addresses you need decreases.
 
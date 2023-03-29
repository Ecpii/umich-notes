# Counting Memory References
- Each cache miss reads a block from memory
- Each store writes a byte to memory
Most good caches miss < 20% of the time. Improving cache is good because multi-core processors have limited bandwidth between memory/cache. It also saves power because extra stores cost power.

# Write-Back
A *write-back* policy compared to a write-through policy means that you only update memory for a value once it's evicted, rather than when it's updated once.

However, you don't want to write every evicted value to memory - keep a *dirty bit* that keeps track of whether the value has been modified.

# Fully Associative Cache
A cache that allows any piece of memory to go in any cache entry. This has drawbacks because you may need to be able to check against every single cache tag.

To decrease on this cost, we can make a direct mapped cache, where we can make it so that each block maps to a particular location in the cache.
![[Pasted image 20230321154634.png]]
In a direct mapped cache, LRU is no longer needed as there is only one place to put something in the cache.
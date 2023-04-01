# Miss Mitigation
## Compulsory
- Increase block size (you fetch more with each miss, likely preventing more misses)
- reduces the total number of blocks for a cache size
- prefetching (not this class)
## Capacity
- bigger cache
- slower cache
## Conflict miss
- Higher associativity
- slower search
# Cache Size
Bigger caches can make temporal locality more used, but too large a cache means its slower to look through. Too small of a set lets data be replaced too much.
# Block Size
If blocks are too small, then spatial locality is neglected. Too large of a block means that you access more and more unnecessary information. It also means you have less entries in your cache.
# Associativity
Increasing associativity will increase the hit rate, but grows logarithmically. This is the only thing that doesn't hurt if you increase too hard.
Smaller associativity leads to better hit times and cheaper materials.
A mix between fully associative and direct caches. Again, we partition memory into regions, and associate a region to a set of cahce lines. It's like having a direct mapped cache that maps to small fully associative caches. The address is split as:

```
| Tag | Set | Block |
```

# Integrating Caches into Pipeline

Replace instruction memory with Icache (also called I$ sometimes, or by goatmont, "cash me outside how bou that"). Replace data memory with Dcache. There are some new issues that come up:
- memory accesses may have variable runtime
- both caches may miss, or one may miss while the other hits

# Cache Improvements
There are around "3" types of cache misses:
- **compulsory miss**
	- we've never seen the data, mandatory
 - **capacity miss**
	 - cache was not big enough to hold all data
	 - avoidable with larger cache
	 - tradeoffs with increasing cache size though
- **conflict miss**
	- cache was big enough, but the entry was replaced due to associativity policy
	- like mapped caches will kick things out even if there is space in the cache because of how it works
 
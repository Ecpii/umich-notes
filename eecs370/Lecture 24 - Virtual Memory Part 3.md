Looking up virtual to physical memory is slow because the page table translation is in main memory. We avoid this by creating a cache-like structure that stores some virtual page number to physical page number translations. This is called a **Translation Look-aside Buffer**.

Often, this is a small cache and direct mapped.

TLB lookup happens after the address is calculated - this could happen *either* before or after looking at cache, there are pros and cons.

If we use the cache after address translation, this is slower, but simpler. Also, it allows the cache to be preserved as programs switch on the processor, since the physical addresses will not collide.

If we use virtual addresses for cache, we have faster performance.
However, if you have two processes that are accessing the same physical location with different virtual addresses (rare, but possible), this can cause issues. This is known as the *synonym problem*.
The more common issue is that two processes have the same virtual address but refer to different physical addresses. This is the *homonym problem*. Usually, this is resolved by flushing the cache when we switch processes, but this can degrade performance.
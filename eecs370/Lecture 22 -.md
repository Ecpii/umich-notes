# Virtual Memory
The operating system maps each memory access from a program to its own chunk of memory, transparent to the program. The program believes it has full access to the memory.

A **page** of memory is a chunk of contiguous memory. Each process gets a virtual page, and virtual pages match physical pages one to one, aside from their number. This means that the page index is preserved from virtual to physical, but the number of the page may be different.
Similarly, each process gets its own page table, which translates the virtual page number to the real page number. This is maintained by the OS and stored in memory.

Address' most significant bits turns into the page number, least significant become the page index.

# Swap
If you run out of memory, you use disk space as extra memory. In our page table, if the page is located in this swap space rather than main memory, we will set the valid bit of that page entry to invalid. When this happens, this is called a *page fault*, and is analagous to a cache miss. However, it takes much longer to recover from this - we stop everything and tell the OS to do its magic.

The OS will switch a page with the page meant to be accessed. Write the page that will be moved to swap into the disk, get the reference page, then update the page table, and then resume the process.
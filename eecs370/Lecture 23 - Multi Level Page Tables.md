# Size of the Page Table Entry
**Physical page number bits**: Subtract the number of bits needed for page size from the bits needed for physical memory. For example, a 1GB physical memory ($2^{30}$) system with pages of size 4 KB ($2^{12}$), the physical page number is 18 bits.

Additionally, a valid bit, read only bit, dirty bit, and other metadata may need to be stored in each page entry.

The page table will store one entry for each virtual page - therefore the size of the page table is the number of virtual pages * size of each page table entry. In our example, 18 bits is rounded up to 3 bytes (we like bytes), and if our system is 32 bit addressable (there are 32 - 12 = 20 bits for virtual pages), we have $2^{20} * 3$ bytes.

# Multi Level
We have a first level page table that holds addresses of second level page tables that hold translation info. Second level page tables aren't created unless they are used.

Structure of a virtual address:
```
| 1st level offset | 2nd level offset | Page offset |
```

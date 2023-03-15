# Size
**Internal Sort** - the sequence can fit in memory and we just use it
**Indirect Sort** - sort the indices instead
**External Sort** - too big for memory, may require blocks

Insertion sort tip: do one pass of bubble sort to get the most extreme value at the start, this way you never have to check bounds

# Quanitifying Sortedness
An **inversion** is any pair of elements (not necessarily contiguous) that are out of order

# Counting Sort
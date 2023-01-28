Endianness is the ordering of bytes in a number. Little endian means that the most significant bits are listed last, big endian is the opposite.  Little endian is more prominent in architecture.
# Memory Alignment
Most ISAs require data be aligned to certain collections of bytes. The start of an `int` must be at a multiple of 4 in memory, a `short` at a multiple of 2, etc.
## Golden Rule of Alignment
- every primitive object starts at an address divisible by its size
- padding is placed in between objects if needed
Structs pose an issue though, because padding may change across instances, making looping difficult.
- for structs
	- the struct is aligned with respect to the largest primitive member variable
	- padding is added at the back to the total size is also aligned with respect to that primitive
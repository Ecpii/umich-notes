3/8
# Dictionaries
Key-value pairs. Only required functions are insert and search. Likely implemented using Binary Search Trees (`std::map`) or Hash Tables (`std::unordered_map`).
- BST Search: average $O(\log n)$, worst case $O(n)$
- BST Insert: average $O(\log n)$, worst case $O(n)$
- Hash Table Search: average $O(1)$, worst case $O(n)$
- Hash Table Insert: average $O(1)$, worst case $O(n)$
# Hash Table
Hash tables are made to find items in a table by key.
## Defining Table Size
The table size M shoule be
- about the number of elements expected
- guess high
- hash tables usually waste space for speed
## Hashing
Hashing is the process of calculating a table index from a given key. There are three requirements for this:
- **translation**: converts the key into the integer (`std::hash()` only does this step )
- **compression**: makes sure that the integer is in a valid range for the table size
- **collision resolution**: deals with the case that two different keys hash to the same index
Good hash functions are:
- easy to compute
- deterministic (same hash for same key)
- distribute keys evenly in tables
## Direct Addressing
Every possible key has a corresponding element in the array:
![[Pasted image 20230308170651.png]]
## Hashed Addressing
Only actual keys map to elements of the array:
![[Pasted image 20230308170714.png]]
## Translation
### Rabin Fingerprint
Used for translating strings. Uses similar idea to decimal numbers, where the first character is the more significant one. For example:
```cpp
long hash(string a) {
	long res = 0
	for (int i = a.size() - 1; i; ++i) {
		res += a[i] * (255 ** (a.size() - 1 - i));
	}
	return res
}

hash("tom")
// "t" * 255^2 + "o" * 255 + "m"
```
## Compression
We convert a number to one in the interval $[0, M)$
### Divison Method
Use modulo, where m is a prime number:
```cpp
int compress(int hashInt, int m) {
	return hashInt % m;
}
```
Cons: lots of collisions when m is not prime
### MAD (Multiply and Divide)
If m is not prime, you can use the following:
```cpp
int compress(int hashInt, int m) {
	// define a and b as prime numbers
	return (a * hashInt + b) % m;
}
```
## Collision Resolution
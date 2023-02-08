`mutable` allows you to modify a member variable from a `const` member function
# Iterators
![[Pasted image 20230207234537.png]]
All STL containers contain
- `.begin()` start of data
- `.end()` just past end of good data
- `.cbegin()` const version of begin
- `.cend()` const version of end
- `.rbegin()` reverse beginning (last item)
- `.rend()` reverse end (just before beginning of good data)

C arrays have `std::begin()`, `std::end()`, and `std::cbegin()`, etc. to convert pointers to iterators. This allows C arrays to be considered as container classes.

The STL never operates on "classes" or "objects", just iterator ranges.

# Vector Memory Overhead
discussed in Lecture 10

A vector keeps track of 3 pointers regardless of content. For multi-dimensional vectors, this looks like this:
$3 + 3a + 3ab$
for a vector
```
vector<vector<vector<T>>> ar3d(a,b,c);
```
We want to reorder dimensions to reduce overhead: $a<b<c$.
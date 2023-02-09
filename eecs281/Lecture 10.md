# Index Sorting
When you have data you don't want to modify or copy, but you want sorted, you can make an array that stores the indices of the data, and sort that.
| |0|1|2|3|
|---|---|---|---|---|
|original data|1.1|0.8|1.9|0.2|
|index sort|3|1|0|2|

# Lambda
Unnamed functions. Syntax:
```cpp
[capture list] (parameter list) -> return type {function body}
```
- the compiler will try to automatically deduce the return type if not specified
## Captures List
the captures list specifies variables from the current scope that will be available inside the lambda
- `[]` captures no variables from the scope
- `[=]` captures all variables from the scope by value
- `[&]` as above, by reference
- `[foo]` captures `foo` by value
- `[&foo]` catpures `foo` by reference
- `[foo, bar]` captures `foo` and `bar` by value
- `[=, &foo]` captures everything by value except for `foo` which is captured by reference
- `[&, foo]` captures everything by reference except for `foo`, which is captured by value
- `[this]` captures the current object
# Useful Functions
- `find_if(start, end, functor)` Finds anything in a container that causes the functor to output true
- `any_of(start, end, predicate)` returns true if any of the items in the container make the predicate true
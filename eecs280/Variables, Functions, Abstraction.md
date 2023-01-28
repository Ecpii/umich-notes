**Variables** are names that exist at compile time, they can only be used within their **scope**;
**Objects** are data that exist during runtime and only can be accessed during their **lifetime**.**

The equals sign copies the **value** of one object to another.

Using `&` at the end of a class/data type when creating a variable, you can declare a reference. `int& y = x` means that  `y` is a reference to an integer rather than an integer. `y` points to the object that `x` points to. Any operation that changes `y` changes `x`.

```c++
int x = 42;
int z = 3;
int& y = x;
x = 24;
y = z;
```

At the end, `y = x = 3`.
In C++, binding operations are permanent; `y` can never be rebound to another object.

# Function Calls
All a function's data is bundled in an *activation record* or *stack entry* in a stack structure in memory. Only the top of the stack can ever be accessed; in essence, the most recently called function has to finish running and clear its stack entry before you can go back to the function that called it.

In C++, regular parameters are passed **by value**. You can pass parameters by reference by using the `&` as before:

```c++
//Doesn't do anything, since it just modifies x and y, not the original variables
void swap(int x, int y) {
	int temp = x;
	x = y;
	y = temp;
}
// Works
void swap(int& x, int& y) {
	int temp = x;
	x = y;
	y = temp;
}
```

# Procedural Abstraction
Header files (`.h`) are just function signatures that help us see what functions do without having to go through their implementations. When using a header file, `#include` the header file at the top.

Warnings:
- Do **not** include the `.cpp` files.
- Do **not** put a `.h` file as an argument for `g++`

A strategy for writing documentation is **RME** documentation:
- what a function **r**equires
	What needs to be true about the input
- what it **m**odifies
	what is outside the scope of this function that will be changed
- what its **e**ffects are
	describe what happens and what is returned

A unit test is testing one piece at a time, making sure the input to a function gives the correct output.
System testing is running an entire project to make sure it gives reasonable output.
Regression testing is running all system tests - useful when one thing changes and you want to see if the system will still behave as before.

# IO Streams
Streams are abstractions that allow you to read/write data. 

Read using `>>` extraction operator. Write using the `<<` insertion operator.

`cin` will keep reading until it reaches an EOF character, which can be typed in the terminal using `Ctrl` + `D`.

`<fstream>` includes file read/write streams:`ifstream` is an input file stream, `ofstream` is an output file stream.

```cpp
ifstream fin;
fin.open("hello.txt")
assert(fin.is_open());
// do stuff
fin.close();
```

Input and output streams are both cases of the generic `istream` and `ostream`, respectively. Pass streams by reference.
`stringstreams` are like streams but for strings.

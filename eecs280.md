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

A uniit test is testing one piece at a time, making sure the input to a function gives the correct output.
System testing is running an entire project to make sure it gives reasonable output.
Regression testing is running all system tests - useful when one thing changes and you want to see if the system will still behave as before.
# Pointers
similar to reference variables but more flexible.
To declare a pointer variables, put `*` to the right of the data type.  A pointer variable stores the address of another variable with that data type.
```cpp
int x = 3;
int *ptr = &x; // 0x1000
```
To get to the object the pointer is pointing to, you *dereference* the pointer by putting another asterisk in front of the pointer variable.
```cpp
cout << *ptr << endl; // 3
(*ptr)++;
cout << x <<< endl; // 4
```
# Arrays
```cpp
int array_name[4];
```

**note**: Trying to read an entire array will instead just return a pointer to its first element. This is also known as array decay:
```cpp
int array[3] = { 1, 2, 3 };
cout << array << endl;
// will return the pointer to 1
```
## Pointer Arithmetic
You can use `+` and `-` operators to change pointer values.
```cpp
int arr[3] = {1, 2, 3}; // 0x1010,0x1014,0x1018
int *ptr = arr;
int *ptr2 = &arr[2];
int *ptr3 = arr + 2;
// the +2 means it adds the space of two integers, not adding two to the value, so
// ptr2 == ptr3 == 0x1018
// arr[2] == *(arr + 2)
```
In c++, const always refers first to the data type on its left, then the one on the right. When declaring a `const int*`, you can change what the pointer is but not what its pointing to.
# Classes/Structs
Three data types:
- atomic (primitive)
	- pointers, ints, etc
- arrays (homogenous)
	- contiguous memory
- class-type (heterogenous)
	- classes and structs
if you have a pointer that points to a struct
```cpp
(*p)*)
```

# C Strings
*C-style* strings are `char` arrays with special rules:
```cpp
char str[3] = {'h', 'i', '\0'};
// same as
char str[3] = "hi"; // null character automatically inserted
```
*C-style* string always end with a null character (`\0`). C strings will decay into pointers, unless it is passed to `cout`.

Note: `cout` will always assume a character pointer will always point to a C string - if you give a char pointer to `cout` that is not part of a C string you may cause a crash.

For C strings, you may fall into some common traps
```cpp
char str1[6] = "hello";
char str2[6] = "hello";
char str3[6] = "apple";
char *ptr = str1;

// test for equality does not work since it just tests if they point to the same location
str1 == str2;

// type mismatch, char[] and char*
str1 = str3;


ptr = str3;
```

Command line arguments are passed to the main function in C++.

```cpp
int main(int argc, char* argv[]) {
	// argc is the number of the arguments + 1
	// argv is an array of cstrings representing the arguments
}
```

To treat an argumet as if it were an `int`, use the function `cstdlib::atoi`.

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

# Abstract Data Types
Representation invariants express the conditions for a valid compound object.
# OOP Time
```cpp
class Triangle {
private:
	int a;
	int b;
	int c;

public:
	void scale(double s) {
		this->a *= s;
	}
}
```
The pointer `*this` is implicitly passed into every function.

`const` at the end of a function signature means that the function should not modify the class member itelf:
```cpp
double perimeter() const {
	return this->a + this->b + this->c;
}
```

C++ allows other members of the same class to find private values of another member.
### Constructors
```cpp
Triangle(double a_in, double b_in, double c_in)
: a(a_in), b(b_in), c(c_in) {}
```
This is called a *member initialization list* and sets the values as expected.
## Check invariants
create a function to make sure the data is being good and call this function in every function as well as a constructor.
## Scope resolution operator
The `::` operator tells the compiler where to find something. If you are accessing something or defining something out of scope, use the `::` operator.

Inherited classes cannot access private member variables from the classes they inherited from.

# Structs
structs are just old versions of classes, usually used for POD. public by default, classes are private by default.

# Object Slicing
If you have an array of a base class, you can't use the derived class methods in the stored members even if they are of the derived class because the compiler only allocated enough memory for the base class
## Upcasting
Upcasting is assiging the address of a derived class object to a base class pointer - you don't lose the attributes of the derived class unique to the derived class but you also cant access them through the base class pointer
You can't do pointer arithmetic on upcasted pointers.

**dynamic binding** means that the c++ compiler/runtime will find the function overload corresponding to the most accurate class. **static binding** simply uses the type declared *staticly* which is usually faster. Using `virtual` in a function declaration indicates dynamic binding and allows you more flexibility in specifying which version of the function is called.

put `override` at the end of a fucntion sig

Templated functions/classes **must** be initialized in the same file as they are declared in.

**Type aliases** allow you to assign a typ eto another type:

```cpp
using Set = UnsortedSet<T>;
```

The **new** operator puts an object in the *heap*, a region of memory kept for objects like this. The stack is where local variables go, and there is a special area for static variables.
# Copying
There are two main ways class objects are copied:
- copy constructor
used when making a new object
```cpp
Example e3 = e1;
// above is exactly the same as
Example e3(e1);
```
- assignment operator
```cpp
e3 = e2;
```
The copy constructor is defined as
```cpp
Example(const Example& e) {}
```
The assignment operator is defined as
```cpp
Example & operator= (const Example &rhs) {
	return *this;
}
```
We have the `return *this` there for code like this:
```
e1 = (e2 = e3)
```

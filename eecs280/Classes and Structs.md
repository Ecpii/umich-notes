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


# Abstract Data Types
Representation invariants express the conditions for a valid compound object.
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

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
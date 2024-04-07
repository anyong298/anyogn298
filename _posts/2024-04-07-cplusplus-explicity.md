# C++ explicit keyword

## What does `explicit` do?

If a class contructor needs only one parameter to intialize, this constructor implies an `implicit` conversion from the parameter type to the class, which might lead to potential misusage of the class. To avoid this, `explicit` can be used to disable the implicit conversion.

## Example

Let's start with a code
```cpp
class CStringEx{
public:
	CStringEx() = default;
	// create a string with a size of n
	CStringEx(size_t n);
private:
	std::vector<char> string_data_;
};
```

With this definition, the follow code is OK.
```cpp
CStringEx str;
str = 10;  // OK! Create a string with a size of 10 
str = 'a'; // OK too!! Create a string with a size of int('a')
```
However, these two assignment leads to confusion of the code. It's better to avoid this usage. 

Therefore, We can start to use `explicit`.
```cpp
class CStringEx{
public:
	CStringEx() = default;
	// create a string with a size of n
	explicit CStringEx(size_t n);
private:
	std::vector<char> string_data_;
};
```
Now, the same code will not work.
```cpp
CStringEx str;
str = 10;  // Not OK! 
str = 'a'; // Not OK!!
str = CStringEx(10); // OK
```

# C++ explicit keyword

## Background
If a class contructor needs only one parameter to intialize, this constructor implies an `implicit` conversion from the parameter type to the class, which might lead to potential misusage of the class. To avoid this, `explicit` can be used to disable the implicit conversion.

## Example

Let's start with a code
```
class CStringEx{
public:
	CStringEx() = default;
	// create a string with a size of n
	CStringEx(size_t n);
	CStringEx(std::string const &st);
private:
	std::vector<char> string_data_;
};
```

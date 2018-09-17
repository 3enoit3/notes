# Modern C++
According to https://arne-mertz.de/2018/08/modern-c-newest-standard/:
* RAII
* Strong typing
* Compile time programming

# Features
* Meyer
  * List: https://www.artima.com/shop/overview_of_the_new_cpp
  * Effective Modern C++: www.xavierlamorlette.fr/programmation/cpp/effective_modern_cpp/

## Constexpr
* possible to evaluate the value of the function or variable at compile time
http://b.atch.se/posts/constexpr-meta-container/
```c++
constexpr int var;
constexpr int f(int i) {...}
```
constexpr is a property of the function, not of the function's input

## Auto
https://herbsutter.com/2013/08/12/gotw-94-solution-aaa-style-almost-always-auto/

## Enum
An enumerator declared in class scope can be referred to using the class member access operators (::, . and ->)
```c++
namespace N { enum E { X }; }
::N::X; // all standards
::N::E::X; // C++11
```

## Template
### Argument deduction
```c++
std::pair p{1, 2}; // C++17
```
# Links
* Some c++17 features: https://blog.jetbrains.com/rscpp/whats-new-in-resharper-cpp-2018-2/

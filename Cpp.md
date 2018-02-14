# C++
## Misc
### [Namespace](http://en.cppreference.com/w/cpp/language/namespace)
```c++
using namespace ns_name; // using directive
using ns_name::name; // using declaration
namespace alias_name = ns_name; // alias
```

### [Linkage](http://en.cppreference.com/w/cpp/language/storage_duration#Linkage)
* If a name (which denotes an object, reference, function, type, template, namespace, or value) has **linkage**: it refers to **the same entity** in **different scopes**.
If not, then **several instances of the entity are generated**.
* Linkages:
  * **no linkage**: from the scope it is in *(ex: local classes, functions, typedefs, enumerations, and enumerators...)*
  * **internal linkage**: from all scopes in the current translation unit *(ex: static variables and functions...)*
  * **external linkage**: from the scopes in the other translation units, including language linkage like C *(the rest, ex: functions, extern variables...)*

## Templates
### Samples
```c++
// Functions
template<class T> void f(T); // base/primary template
template<class T> void f(T*); // another base template, overloading f(T)
template<> void f<>(int); // full/explicit specialization

// Classes
template<class T> class X; // base template
template<class T> class X<T*>; // partial specialization
template<> class X<int>; // full/explicit specialization

template<class T> void X<T>::f();
template<class T> void X<T*>::f();
template<> void X<int>::f();

// Members
class X { template <class U> void f(U); }; // template member
template<class T> class X { template <class U> void f(U); }; // template class and member

template<class U> void X::f<U>();
template<class T> template<class U> void X<T>::f<U>();
```
### Notes
* [Why Not Specialize Function Templates?](http://www.gotw.ca/publications/mill17.htm)
  * Don't add specialization to **existing** function base template: **use a plain old function**.
  * Prefer to write **new** function base template as a single function template (that should never be specialized or overloaded) calling ***a class template containing a static function** with the same signature.

# Tools
## Online compilers
* Boost: https://wandbox.org
* Assembly: https://godbolt.org
* Performance: http://quick-bench.com

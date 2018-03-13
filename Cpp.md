# C++
## Misc
### Generalities
* Parameter vs Argument
```c++
void f(int parameter) {}
f(argument);
```

* Overload vs Override
```c++
class Base {
  virtual int f(int i);
  char f(char c); // overload: same name
};

class Derived : public Base {
  int f(int i); // override: same signature (name, cv-qualifiers, parameter types) + virtual base
};
```

* Endianness
  * **Most Significant Bit**: greatest bit position (typical use: sign bit for signed binary number)
  * **Big-endian**: byte with MSB **first** (typical use: TCP, UDP - aka **network byte order**)
  * **Little-endian**: byte with MSB **last** (typical use: Intel microprocessors)

* Encoding
  * **Unicode**: character set (from number to symbol) - **abstract form of the text**
  * **UTF-8**: encoding (from binary to number)
    * decoding: binary -> number
    * encoding: number -> binary
  * **ASCII**: encoding, where binary == number
  
### [Namespace](http://en.cppreference.com/w/cpp/language/namespace)
```c++
using ns_name::name; // using declaration
using namespace ns_name; // using directive
namespace alias_name = ns_name; // alias
```
* **using declaration**
  * only brings in names whose declarations have **already been seen**
  * all restrictions on regular declarations of the same names, hiding, and overloading rules apply
* **using directive**
  * brings in **all names** (even if the namespace is extended after the directive); transitive
  * does not add any names to the declarative region
 
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

## RVO/NRVO
* As return value
```c++
// Return Value Optimization (anonymous)
string f() {
  if (...) return string("value"); // only temporary
  else return string("another_value");
}
string a = f(); // no copy construction

// Named Return Value Optimization
string f() {
  string s("value");
  ...
  return s; // one local variable
}
string a = f(); // no copy construction
```
* As argument
```c++
string f(string s) {
  return s;
}
string a = f( string(value) ); // no copy construction if the argument is a temporary
string b = f(a); // copy construction
```
* Notes
  * RVO works across compilation modules and DLL/library boundaries.
  * NRVO doesn’t always happen in debug mode

## Misc
### Rule of 5: https://stackoverflow.com/a/48865077

## Idioms
* [More C++ idioms](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms)

|Idiom|Description|
|-|-|
|Address Of|Workaround overloaded operator&|
|Algebraic Hierarchy|Computations with numbers|
|Attach by Initialization|Use global and static objects to run code before main|
|Attorney-Client|Control access with a Key whose constructor is private|
|Barton-Nackman trick|Define a friend function (with body) in a class|
|Base-from-Member||
|Boost mutant||
|Calling Virtuals During Initialization||
|Capability Query||
|Checked delete||
|Clear-and-minimize||
|Coercion by Member Template||
|Computational Constructor||
|Concrete Data Type||
|Construct On First Use||
|Construction Tracker||
|Copy-and-swap||
|Copy-on-write||
|Intrusive reference counting (Counted Body)||
|Covariant Return Types||
|Curiously Recurring Template Pattern (CRTP)||
|Empty Base Optimization (EBO)||
|enable-if||
|Erase-Remove||
|Execute-Around Pointer||
|Exploding Return Type||
|Export Guard Macro||
|Expression-template||
|Fake Vtable||
|Fast Pimpl||
|Final Class||
|Free Function Allocators75% developed  as of 18 June 2014||
|Function Object||
|Generic Container Idioms||
|Hierarchy Generation||
|Implicit conversions||
|Include Guard Macro||
|Inline Guard Macro||
|Inner Class||
|Int-To-Type||
|Interface Class||
|Iterator Pair||
|Making New Friends||
|Metafunction||
|Move Constructor||
|Multi-statement Macro||
|Member Detector||
|Named Constructor||
|Named External Argument||
|Named Loop (labeled loop)||
|Named Parameter||
|Named Template Parameters||
|Nifty Counter (Schwarz Counter)||
|Non-copyable Mixin||
|Non-member Non-friend Function||
|Non-throwing swap||
|Non-Virtual Interface (NVI, Public Overloaded Non-Virtuals Call Protected Non-Overloaded Virtuals)||
|nullptr||
|Object Generator||
|Object Template||
|Parameterized Base Class (Parameterized Inheritance)||
|Pimpl (Handle Body, Compilation Firewall, Cheshire Cat)||
|Policy Clone (Metafunction wrapper)||
|Policy-based Design||
|Polymorphic Exception||
|Polymorphic Value Types||
|Recursive Type Composition||
|Requiring or Prohibiting Heap-based Objects||
|Resource Acquisition Is Initialization (RAII, Execute-Around Object, Scoped Locking)||
|Resource Return||
|Return Type Resolver||
|Runtime Static Initialization Order Idioms||
|Safe bool||
|Scope Guard||
|Substitution Failure Is Not An Error (SFINAE)||
|Shortening Long Template Names||
|Shrink-to-fit||
|Small Object Optimization||
|Smart Pointer||
|Storage Class Tracker||
|Tag Dispatching||
|Temporary Base Class||
|Temporary Proxy||
|The result_of technique||
|Thin Template||
|Traits||
|Type Erasure||
|Type Generator (Templated Typedef)||
|Type Safe Enum||
|Type Selection||
|Virtual Constructor||
|Virtual Friend Function||

# Tools
## Online compilers
* Boost: https://wandbox.org
* Assembly: https://godbolt.org
* Performance: http://quick-bench.com

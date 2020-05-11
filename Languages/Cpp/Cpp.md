# C++
## Features
[Modern C++ features](https://3enoit3.github.io/data_tools.js/lists/)

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
  
  * *Note: files might contain a header indicating the encoding (ex: UTF-16 files might start with FF FE for big endian, FE FF for little endian)*
  
### [Namespace](http://en.cppreference.com/w/cpp/language/namespace)
```c++
using ns_name::name; // using declaration
using namespace ns_name; // using directive
namespace alias_name = ns_name; // alias

namespace { declarations } // unnamed namespace: scope to the end of the translation unit + internal linkage
```
* **using declaration**
  * only brings in names whose declarations have **already been seen**
  * all restrictions on regular declarations of the same names, hiding, and overloading rules apply
* **using directive**
  * brings in **all names** (even if the namespace is extended after the directive); transitive
  * does not add any names to the declarative region

### Typedef
```c++
typedef type alias; // or typedef type def;

typedef A* PA;
const PA pa; // is a constant pointer (A* const) and not a constant pointee (const A*)
```

### [Linkage](http://en.cppreference.com/w/cpp/language/storage_duration#Linkage)
* If a name (which denotes an object, reference, function, type, template, namespace, or value) has **linkage**: it refers to **the same entity** in **different scopes**.
If not, then **several instances of the entity are generated**.
* Linkages:
  * **no linkage**: from the scope it is in *(ex: local classes, functions, typedefs, enumerations, and enumerators...)*
  * **internal linkage**: from all scopes in the current translation unit *(ex: static variables and functions, const variables...)*
  * **external linkage**: from the scopes in the other translation units, including language linkage like C *(the rest, ex: functions, extern variables...)*
* Directives:
  * **static**: defined in this translation units but cannot be used in others (**internal linkage**) - Linker will enforce it
  * **extern**: used in this translation unit but don't complain if it isn't defined (**external linkage**) - Linker will sort it out
  * **[inline](https://en.cppreference.com/w/cpp/language/inline)**: defined in multiple translation units (typical use: function definition in header) - Linker will make sure they all use the same address
    * Methods defined in their class are implicitely inline

### [Inlining](https://stackoverflow.com/questions/10535667/does-it-make-any-sense-to-use-inline-keyword-with-templates/10536588#10536588)
* Compiler **cannot inline** code if it **cannot access the function definition**
* *Usually all private methods are inlined in maximally optimized code*
* Inlining can be prevented: in GCC use __attribute __(( noinline )), and in Visual Studio use __declspec(noinline).
* Note: **[inline](https://en.cppreference.com/w/cpp/language/inline)** keyword means "multiple definitions are permitted" and not "inlining is preferred"

### Lifetime
* Temporary objects
  * Destroyed at the last step in evaluating the **full-expression** (not a sub-expression - generally ends at ';') that created them
  * Multiple objects: destroyed **opposite order** of creation (even in case of exception)

### Slicing
```c++
struct A { int a_; };
struct B : public A { int b_; }; 
B b;

A a = b; // slicing: A copy-constructor applied on B
A* pa = &b; // ok
A& ra = b; // ok
```

### Forward declaration
* function return value can be foward declared
```c++
struct A {
    struct B;       // forward declaration
    
    B f() {         // the forward declaration of B is sufficient here
        return B(); // the definition of B is needed here, but f body is only evaluated after the full declaration of A
    }
   
    struct B {};    // definition
};
```

### Templates
#### Samples
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
#### Instanciation
* Implicit instantiation
  * Not yet been explicitly specialized or explicitly instantiated
  * **Function**: when **its definition is required**.
    * Implicitely inline, except fully specialized functions
  * **Class**: when **a completely-defined object type is required**, or when the completeness of the class type affects the semantics of the program.
    * **Member declaration**: when the **class is instantiated**
    * **Member definition**: when **required**, except unscoped enumerations / anonymous unions (when the class is instantiated) or static data-member (no instantiation).
    * Friend: the names of its friends are treated as if an explicit specialization had been declared at the point of instantiation
    * Implicitely inline
* Point of instantiation
  * Location where the compiler is allowed to generate the code for the specialization
  * Assuming:
    * D is the location of the declaration/definition namespace scope containing the reference to template specialization X
    * XS depends on template parameters of surrounding template S
  * Functions:
    * X poi is immediately **after** D / XS poi is S poi
    * **Multiple points**, which must all generate the same content: the program is ill-formed if not
  * Classes:
    * X poi is immediately **before** D / XS poi is immediately before S poi
    * **Single point**
#### Notes
* [Why Not Specialize Function Templates?](http://www.gotw.ca/publications/mill17.htm)
  * Don't add specialization to **existing** function base template: **use a plain old function**.
  * Prefer to write **new** function base template as a single function template (that should never be specialized or overloaded) calling ***a class template containing a static function** with the same signature.
* [Instantiation](http://b.atch.se/posts/non-constant-constant-expressions/#template-instantiation)

### RVO/NRVO
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

### CRTP (Curiously Recurring Template Pattern)
https://www.fluentcpp.com/2017/05/12/curiously-recurring-template-pattern/
```c++
template <typename T> class Base {
  void doSomethingWithDerived() {
    T& derived_this = static_cast<T&>(*this);
  }
};
 
class Derived : public Base<Derived> {
};
```
* Usage
  * Add functionality through mixin (ex: derived provides accessors, base provides logic)
  * Static polymorphism (ex: derived+base provides accessors, base used as a generic parameter for functions)
## STL
### Streams
```c++
ostream os; os << "str"; // put(char), write(bin), tellp/seekp, flush
istream is; is >> str; // get(char)/getline/peek, read(bin), tellg/seekg

?fstream fs; fs.open("path"); // is_open/close
?stringstream ss; ss.str("str"); // str()

// ostream, istream <- iostream <- fstream / stringstream
```

## Interesting
### Rule of 5: https://stackoverflow.com/a/48865077
### Zero-cost abstraction
The runtime cost is the same as for a low level language implementation (generally C).
http://matthewfl.com/2114/programming/cost-of-abstractions
### C++ Design
https://web.archive.org/web/20160407215648/http://stroustrup.com/rules.pdf

# Tools
## Online compilers
* Boost: https://wandbox.org
* Assembly: https://godbolt.org
* Performance: http://quick-bench.com

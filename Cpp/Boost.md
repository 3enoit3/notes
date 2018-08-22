# Boost

## Optional
```c++
#include <boost/optional.hpp>

boost::optional<int> a;

a.set(1);
a.value(); // get
a.value_or(2); // get_value_or (deprecated)

if(a) {}
if(a == boost::none) {}

boost::optional<int> f() { return 1; }
boost::optional<int> f() { return boost::none; }

a = boost::in_place<int>(1); // internally calls placement-new and directly passes the parameter to the constructor of T
```

||Boost|C++ 11|
|-|-|-|
|header|`#include <boost/optional.hpp>`|`#include <optional>`|
|namespace|`boost::optional<int> a;`|`std::optional<int> a;`|

## Variant
```c++
#include <boost/variant.hpp>

boost::variant<int, std::string> v; // == 0 (default constructor of first bounded type)
boost::variant<int, std::string> v("hello world");

class my_visitor : public boost::static_visitor<int> {
public:
    int operator()(int i) const { return i; }
    int operator()(const std::string & str) const  { return str.length(); }
};
int result = boost::apply_visitor(my_visitor(), v);

std::string& str = boost::get<std::string>(v);
bool is_string = boost::get<std::string>(&v) != 0;
bool is_empty = v.empty();
std::cout << v << '\n';
```

||Boost|C++ 11|
|-|-|-|
|header|`#include <boost/variant.hpp>`|`#include <variant>`|
|namespace|`boost::variant<int, std::string> v;`|`std::variant<int, std::string> v;`|

## Xpressive
```c++
#include <boost/xpressive/xpressive.hpp>

using namespace boost::xpressive;

// Compile
sregex dynamic_rex = sregex::compile( "(\\w+) (\\w+)!" ); // dynamic
sregex static_rex = (s1= +_w) >> ' ' >> (s2= +_w) >> '!'; // static

// Search
smatch m;
if( regex_match(str, m, rex) ) {
  std::cout << "whole match: " << m[0] << '\n';
  std::cout << "captures: " << m[1] << " " << m[2] << '\n';
}

// Replace
std::string output = regex_replace(str, rex, new_value);

// Split
sregex_token_iterator it(str.begin(), str.end(), rex), end;
for(; it != end; ++cur ) {
  std::cout << "token: " << *it << '\n';
};
```
* Regex format
  * [Static regex](http://www.boost.org/doc/libs/1_66_0/doc/html/xpressive/user_s_guide.html#boost_xpressive.user_s_guide.creating_a_regex_object.static_regexes.static_xpressive_syntax_cheat_sheet)
  * [Dynamic regex](http://www.boost.org/doc/libs/1_66_0/doc/html/xpressive/user_s_guide.html#boost_xpressive.user_s_guide.string_substitutions.the_ecma_262_format_sequences)
* Classes
  * [Iterators](http://www.boost.org/doc/libs/1_66_0/doc/html/xpressive/user_s_guide.html#boost_xpressive.user_s_guide.quick_start.know_your_iterator_type)
  * [Matches](http://www.boost.org/doc/libs/1_66_0/doc/html/xpressive/user_s_guide.html#boost_xpressive.user_s_guide.accessing_results.match_results)

## Thread
```c++
#include <boost/thread/thread.hpp> 

// Sleep
#include <boost/chrono.hpp>
boost::this_thread::sleep_for( boost::chrono::milliseconds(100) );
```

## Bind

## Asserts
```c++
// Dynamic
#include <boost/assert.hpp>

BOOST_ASSERT(expr); // or BOOST_VERIFY(expr) to always evaluate expr (for side effects)
BOOST_ASSERT_MSG(expr, msg); // or BOOST_VERIFY_MSG
#ifndef BOOST_ASSERT_IS_VOID // are asserts enabled?

// Static
#include <boost/static_assert.hpp>

BOOST_STATIC_ASSERT(expr);
BOOST_STATIC_ASSERT_MSG(expr, msg);
```

## Shared_ptr
```c++
#include <boost/shared_ptr.hpp>

boost::shared_ptr<int> p( new int(42) );
```
* [Naive mental model for shared_ptr<T>](https://youtu.be/lkgszkPnV8g?t=1210):
  * T* px *[thread unsafe]*
  * shared_count pn *[thread safe]* (whose impl< T >)
* Multiple threads can simultaneously:
  * **"read"** (const operations) a **same** shared_ptr instance
  * **"write"** (mutable operations: operator=, reset, destructor) **different** shared_ptr instances (even sharing the same reference count underneath)


||Boost|C++ 11|
|-|-|-|
|header|`#include <boost/shared_ptr.hpp>`|`#include <memory>`|
|namespace|`boost::shared_ptr<int> p;`|`std::shared_ptr<int> p;`|

## Function
```c++
// Function
std::function<void(int)> f_function = print_num;
std::function<void(int)> f_functor = PrintNum();
std::function<void(const Foo&, int)> f_member = &Foo::print_num;
std::function<void(int)> f_hidden_member = boost::bind(Foo::print_num, foo, _1);
std::cout << f_function(1) << f_functor(1) << f_member(foo, 1) << f_hidden_member(1);

// Curried
std::function<void(int)> f_function = boost::bind(print_num, 1);
std::function<void(const Foo&)> f_member = boost::bind(Foo::print_num, _1, 1);
std::function<void(const Foo&)> f_hidden_member = boost::bind(Foo::print_num, foo, 1);
std::cout << f_function() << f_member(foo) << f_hidden_member();
```

## Algorithms
```c++ 
// String searching
boost::algorithm::boyer_moore<std::string::const_iterator> search(pattern.begin(), pattern.end());  // boyer_moore,  boyer_moore_horspool_search, knuth_morris_pratt
bool found = search(str.begin(), str.end())) != str.end(); // str aka corpus

// Sequence
boost::algorithm::all_of(v.begin(), v.end(), isOdd) == true; // all_of, any_of, none_of, one_of + predicate
boost::algorithm::all_of_equal(v.begin(), v.end(), 2) == true; // *_equal + value
// other: is_sorted, is_partiotioned, equal, mismatch

// Ceiling
boost::algorithm::clamp(input_23, low_1, high_10) == 10;
```

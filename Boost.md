# Boost

## Optional
```c++
#include <boost/optional.hpp>

boost::optional<int> a;

a.set(1);
a.get();

if(a) {}
if(a == boost::none) {}

boost::optional<int> f() { return 1; }
boost::optional<int> f() { return boost::none; }
```

## Variant
```c++
#include <boost/variant.hpp>

boost::variant<int, std::string> a; // == 0 (default constructor of first bounded type)
boost::variant<int, std::string> v("hello world");

class my_visitor : public boost::static_visitor<int> {
public:
    int operator()(int i) const { return i; }
    int operator()(const std::string & str) const  { return str.length(); }
};
int result = boost::apply_visitor(my_visitor(), v);

std::string& str = boost::get<std::string>(v);
std::cout << v << '\n';
```

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

## Bind

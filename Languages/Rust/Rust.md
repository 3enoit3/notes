# Rust
## What I like
* Const is the default
* When mutable, it has a unique owner and must be moved around
* References are explicit (passed/expected/dereferenced) and cannot take ownership

## What I am not sure
* Typing: when should it be explicit, and when is it deduced?
* Python generators equivalent: do they exist?
* More time spent in compilation than in execution testing
* Some problems must be solved up front (ex. error management..), which is good but frustrating at first (difficult to prototype and expend)
* Compiler seems to guide toward better design (ex. method member taking a reference cannot take data member as parameter, which somehow makes sense -> split into sub-struct)
 
## Playground
* online: https://play.rust-lang.org/
* mine offline: https://github.com/3enoit3/rust_playground

## Environment
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh # to install

rustc file.rs # to compile

cargo new <project> [--lib] # to create a project
project> cargo build
project> cargo test
project> cargo fmt
project> cargo doc
```

### Code format
https://github.com/rust-dev-tools/fmt-rfcs/blob/master/guide/guide.md
```rust
// snake case
let my_variable = 42;
fn my_function_name() {}
```

### Code doc
https://doc.rust-lang.org/rustdoc/how-to-write-documentation.html
```rust
#![deny(missing_docs)]
//! This is a simple file enabling and passing documentation checks

/// Simple string generator
fn hello() -> String {
    "Hello World!".to_string()
}

fn main() {
    println!("{}", hello());
}
```

## Code
```rust
fn name(arg: String) -> String { // "arg: type" and "-> type" are mandatory if not void
  arg // no ;
}

fn early_return() -> u8 {
  if true { // no () needed
    return 0; // return value with ;
  }
  1 // no ;
}

// executed with "cargo test"
mod tests {
  use super::*; // to see early_return()

  #[test]
  fn test_early_return() {
    assert!(early_return() == 0);
    assert_eq!(early_return(), 0);
  }
}

println("{}", i);
let v: Vec<char> = Vec::new(); // let type is optional if compiler can deduce: Vec::<char>::new()
println!("{:?}", v); // debug print

#[derive(PartialEq)] // to test MyEnum::e1 != MyEnum::e2
#[derive(Debug)] // to use println!("{:?}", MyEnum::e1)
enum MyEnum {
  e1,
  e2,
}
let e: MyEnum = MyEnum::e1;

let val = match e {
    MyEnum::e1 => 0,
    MyEnum::e2 => 1,
}

// References
let v = "Hello".to_string();
let mut m = "World".to_string();

let rv1 = &v;
let rv2 = &v; // but not "let r = &mut v" because v is immutable

let rm1 = &m;
let rm2 = &mut m; // but not "let r3 = &mut m" because m is mutable and already borrowed

*rm2 = "There".to_string();
rm2.push('!'); // . implicitely uses *
rv1.is_empty(); 
```

## Types
* String: https://doc.rust-lang.org/std/string/struct.String.html
* str: https://doc.rust-lang.org/std/primitive.str.html
* char: https://doc.rust-lang.org/std/primitive.char.html
* Vec: https://doc.rust-lang.org/std/vec/struct.Vec.html

### Strings
* String has ownership and is mutable
* &str borrows a String and so is immutable
* same relationship as between Vec<T> and &[T], T and &T.
* is interface of &str included in String?
* https://blog.mgattozzi.dev/how-do-i-str-string/

```rust
println!("{}", str); // first argument of println!() is a literal

"Hello".to_string(); // -> String
"Hello".to_owned();
String::from("Hello");

let slice: &str = &s[..]; // -> &str

fn split_into_words() -> Vec<String> {
  "Hello World!".split(' ').map(|x| x.to_string()).collect()
}

fn split_into_words() -> Vec<&str> { // is not possible because &str must be borrowed from somewhere
  "Hello".split(' ').collect()
}

let s: String = v.into_iter().collect(); // convert vec of chars into a String

let s = 4.to_string();
let i = "4".parse::<u8>().unwrap();
```

### Vec
```rust
let v: Vec<char> = Vec::new();
let v = Vec::char::new();
let v = vec!['a', 'b', 'c'];
```

### Conversions
```rust
let x: u32 = 0;
let y: i32 = x as i32;
```

## Modules
```rust
// src/main.rs
mod rendering;
mod game;

let v: rendering::Sprite = game::get_sprite();

// src/rendering.rs
pub struct Sprite { .. }

// src/game.rs
use crate::rendering;

pub fn get_sprite() -> rendering::Sprite { .. }
```
https://stackoverflow.com/a/62702785
 
## Errors
```rust
let result: Result<String, String> = Ok(String::from("Hello, world!"));
let value = result.unwrap(); // move the String to value
// println!("Result: {}", result.unwrap()); // The following line will cause a compilation error because `result` has been consumed.
```

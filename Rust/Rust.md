# Rust
## What I like
* Const is the default
* When mutable, it has a unique owner and must moved around
* References are explicit (passed/expected/dereferenced) and cannot take ownership

## Notes from the playground
https://github.com/3enoit3/rust_playground

### Command line
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh # to install

rustc file.rs # to compile
cargo new project [--lib] # to create a project
cd project; cargo build # to build the project
```

### Misc
```rust
fn name(arg: String) -> String { // "arg: type" and "-> type" are mandatory
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
let v: Vec<char> = Vec::new();
println!("{:?}", v); // debug print

#[derive(PartialEq)] // to test MyEnum::e1 != MyEnum::e2
#[derive(Debug)] // to use println!("{:?}", MyEnum::e1)
enum MyEnum {
  e1,
  e2,
}
let e: MyEnum = MyEnum::e1;
```
* let type is optional, except for Vec?

### String
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

fn split_into_words() -> Vec<String> {
  "Hello World!".split(' ').map(|x| x.to_string()).collect()
}

fn split_into_words() -> Vec<&str> { // is not possible because &str must be borrowed from somewhere
  "Hello".split(' ').collect()
}
```

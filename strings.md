[Main](index.md)

# <font color="green"> Strings </font>

- String
  - little slower.
  - has more functions.
  - it is a pointer with a data in the heap.
  - Owned type.
  - `let var = String::from("Hello, World");`
  - `let var = "Elie".to_strong();`
- &str
  - Simple String
  - `let var  = "hello, world";`
  - fast
  - "&" because it is a reference to use str.

🚀 format! => Creates a String

```
fn main() {
    let my_name = "Billybrobby";
    let my_country = "USA";
    let my_home = "Korea";

    let _together = format!(
        "I am {} and I come from {} but I live in {}.",
        my_name, my_country, my_home
    );
}
```

🚀 into! => makes an owned type.

```
// this will not work because Rust doesn't know which owned type you want. Many types can be made form a &str
fn main() {
    let my_string = "Try to make this a String".into(); // ⚠️
}
```

```
fn main() {
    let my_string: String = "Try to make this a String".into(); // ✔️
}
```

# using var in the return

- to use the match condition in the return portion by giving it a name.

```rust
fn match_number(input: i32) {
    match input {
    // here we gave the match condition name "number" now we can use number in the return portion
    number @ 4 => println!("{} is an unlucky number in China ", number),
    number @  13 => println!("{} is unlucky in North America, lucky in Italy! In bocca al lupo!", number),
    _ => println!("Looks like a normal number"),
    }
}

fn main() {
    match_number(50);
    match_number(13);
    match_number(4);
}
```

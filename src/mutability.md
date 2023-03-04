# <font color="green">Mutability</font>

vars are either

- mutable => can be changed
- immutable => can't be changed

🚀 vars are immutable by default.

```rust
fn main(){
    let my_number = 8;
    println!(" My number is: {}", my_number);

    my_number = 10; // 🛑 we can't vars are immutable by default
    println!("My altered number is: {}" , my_number);
}
```

🚀 To make a var mutable we use the "mut" word.

```rust
fn main() {
    let mut my_number = 8;
    println!(" My number is: {}", my_number);

    my_number = 10; // ✅
    println!("My altered number is: {}" , my_number);
}
```

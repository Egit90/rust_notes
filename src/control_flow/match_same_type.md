# match must return same type

```rust
fn main(){
    let my_number = 10;
    let v = match my_number {
        10 => 8,
        _ => "Something else" // 🛑 🛑 this will not work return type must be the same!!
    }
}
```

- the same rule goes for any checking

```rust
fn main(){
    let v = 2;
    let a = if v == 2 {5} else ("something else"); // 🛑 🛑 wrong return type must be the same !!
}
```

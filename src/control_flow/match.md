# match

- the below code will fail ... because we didn't give it all possibilities. "non-exhaustive pattern"

```rust
fn main(){
    let my_number: u8 =5;
    match my_number{
        8 => println!("it is a 8"),
        10 => println!("it is a 10"),
    }
}
```

- to match everything else use "\_"

```rust
fn main(){
    let my_number: u8 =5;
    match my_number{
        8 => println!("it is a 8"),
        10 => println!("it is a 10"),
        _ => println!("it's something else")
    }
}
```

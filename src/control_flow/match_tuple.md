# match using tuples

- you can match with a tuple ..

```rust
fn main(){
    let sky = "cloudy";
    let temp = "warm";
    match (sky , temp){
        ("cloudy","cold") => println!("it is cloudy and warm"),
        ("sunny","warm") => println!("it is sunny and warm"),
        ("cloudy", "warm") => println!("it is cloudy and warm"),
        _ => println!("it is something else")
    }
}
```

# clone

The Clone Trait makes a copy and pass it to a function.

```rust
fn print_country(country: String){
    println!("{}" , country);
}

fn main(){
    let country = String::from("Austria");
    print_country(country.clone());
    print_country(country);
}
```

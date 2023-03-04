- The types that have the copy trait will be copied when they are sent to a function.

- String doesn't have a copy.
- This will fail because country var will be dropped when finished with the first print

```rust
fn print_country(country: String){
    println!("{}", country);
}
fn main(){
    let country;
    print_country(country); // var country will be dropped and String does not have a copy Trait
    print_country(country); // 🛑 country now does not exist.
}
```

- we can fix this with the clone trait

```rust
fn print_country(country: String){
    println!("{}", country);
}
fn main(){
    let country = String::from("Syria");
    print_country(country.clone()); // var country will be cloned
    print_country(country); // ✔️ country now does not exist.
}
```

- i32 has a copy trait.

```rust
fn print_number(number: i32){
    println!("{}", number);
}
fn main(){
    let my_number = 8;
    print_number(my_number); // ✔️ the value will not be dropped here because a copy of the data will be sent to the function.
    print_number(my_number); // ✔️ because this implement a copy trait the value still exist
}
```

# <font color="Green"> Giving References to Functions </font>

- we can pass refs to functions both mutable and immutable.

```rust
fn print_country(country_name: String) {
  println!("{}", country_name)
}
fn main(){
  let country = String::from("Austria");
  print_country(country);  // Value moved here. the function now own the data. The data will be removed once the fuc dies.
  print_country(country); // 🛑Error value used after move. the data does not exist anymore!
}
```

We can solve this problem by passing a ref to the function

```rust
fn print_country(country_name: &String) {
  println!("{}", country_name)
}
fn main(){
  let country = String::from("Austria");
  print_country(&country);  // ✔️ the func will not take ownership
  print_country(&country); // ✔️
  println!("{}",country); // ✔️
}
```

example for passing mutable ref

```rust
fn add_and_print_hungary(country_name: &mut String){
  country_name.push_str("-Hungry");
  println!("Now it says: {}" , country_name);
}
fn main() {
  let mut country = String::from("Austria");
  add_and_print_hungary(&mut country);
}
```

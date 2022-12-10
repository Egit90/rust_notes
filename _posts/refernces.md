---
layout: post
title: References
---

[Main](index.md)

---

# <font color="green">References </font>

1️⃣ OwnerShip: Who owns a value.

2️⃣ In Rust there is only one owner for a piece of data.

```
let country = String::from("Austria"); // The owner of data.
let ref_one = &country;           // just looking at it.
let ref_two = & country;          // just looking at it.

println!("{} , {} , {}" , country , ref_one , ref_two); // ✔️
```

This prints Austria.

---

```
fn return_str() -> &str{
    let country = String::from("Austria");\
    let country_ref = &country;
    country_ref
}
fn main(){
    let country_name = return_str(); // 🛑 Wrong ...
}
```

- function return_str() creates a String.
- then it creates a reference to that String.
- Then it tries to return the reference.
- The String lives inside the function and then it dies.
- Now the ref is pointing to a data that no longer exist !!
- 🦀🦀<font color="red"> You own a string and you can pass it around. But it's references will die once the owner die. </font>

```
fn return_str() -> &str{
    let country = String::from("Austria");\
    country
}
fn main(){
    let country_name = return_str(); // ✔️
}
```

- here the ownership goes from country to country_name. ✔️

---

# <font color="green">Mutable References</font>

- Regular reference gives you a view to the data. `&number`
  - You can have as many immutable references as you want.
- mutable reference gives you the ability to change the data. `&mut number`
  - <font color="red"> the owner must be mutable if you want to use mutable reference. </font>
  - You can have **ONLY ONE** mutable reference.
- 📝 You can't have immutable and mutable reference together.

```
let my_number = 7;
let ref = &mut my_number; // ⚠️ WRONG this will not make my_number mutable .. it has to be mutable when created
```

```
let mut my_number = 7;
let ref = &mut my_number; // ✔️

*num += 10;    // to change the value we use *
println!("{}" , my_number); // 17
```

```
let mut number =6;
let number_ref = &number;
let number_change = &mut number // 🛑 we cant borrow number as mutable because it is also borrowed as immutable
*number_change += 10; // 🛑
println!("{}" , number_ref); // 🛑
```

```
let mut number =6;
let number_change = &mut number //
*number_change += 10; // ✔️ This is fine because in this point we only have one mutable ref
let number_ref = &number;
println!("{}" , number_ref); // ✔️
```

---

# <font color="Green"> Giving References to Functions </font>

- we can pass refs to functions both mutable and immutable.

```
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

```
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

```
fn add_and_print_hungary(country_name: &mut String){
  country_name.push_str("-Hungry");
  println!("Now it says: {}" , country_name);
}
fn main() {
  let mut country = String::from("Austria");
  add_and_print_hungary(&mut country);
}
```

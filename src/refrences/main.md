<font color="green">References </font>

1️⃣ OwnerShip: Who owns a value.

2️⃣ In Rust there is only one owner for a piece of data.

```rust
fn main(){
    let country = String::from("Austria"); // The owner of data.
    let ref_one = &country;           // just looking at it.
    let ref_two = & country;          // just looking at it.
    println!("{} , {} , {}" , country , ref_one , ref_two); // ✔️
}

```

This prints Austria.

---

```rust
fn return_str() -> &str{
    let country = String::from("Austria");   // create a String
    let country_ref = &country;             // create a ref for that string
    country_ref                             // return the ref 🛑 the country dies here so the ref dies with it.
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

```rust
fn return_str() -> String{
    let country = String::from("Austria");
    country
}
fn main(){
    let country_name = return_str(); // ✔️  here the ownership goes from country to country_name. ✔️
}
```

- here the ownership goes from country to country_name. ✔️

---

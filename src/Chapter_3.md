## <font color="green">Important</font>

- The pointer you usually see in Rust is called a reference.
- A reference points to the memory of another value.
- <font color="red">A reference means you borrow the value, but you don't own it. 🦀🦀🦀🦀</font>
- It's the same as our book: the table of contents doesn't own the information. It's the chapters that own the information.
- In Rust, references have a & in front of them. So:

```
let my_variable = 8  // makes a regular variable
let my_reference = &my_variable // makes a reference.
```

- You can also have a reference to a reference, or any number of references.

```
fn main() {
    let my_number = 15; // This is an i32
    let single_reference = &my_number; //  This is a &i32
    let double_reference = &single_reference; // This is a &&i32
    let five_references = &&&&&my_number; // This is a &&&&&i32
}
```

# <font color="green">& vs \*</font>

<font color="red"> - "\*" Means that you take a reference away back to the value 🦀</font>

```
fn main(){
  let my_number = 8;
  let my_reference = &my_number;
  println!("{}" , my_reference == my_number) // 🛑 Can't compare a reference to a number
                               ^^ no implementation for `&{integer} == {integer}`
}
```

```
fn main(){
  let my_number = 8;
  let my_reference = &my_number;
  println!("{}" , my_reference == *my_number) // ✔️

```

# <font color="green"> Strings </font>

- String
  - little slower.
  - has more functions.
  - it is a pointer with a data in the heap.
  - Owned type.
  - `let var = String::from("Hello, World");`
  - `let var = "Elie".to_strong();`
- &str
  - Simple String
  - `let var  = "hello, world";`
  - fast
  - "&" because it is a reference to use str.

🚀 format! => Creates a String

```
fn main() {
    let my_name = "Billybrobby";
    let my_country = "USA";
    let my_home = "Korea";

    let _together = format!(
        "I am {} and I come from {} but I live in {}.",
        my_name, my_country, my_home
    );
}
```

🚀 into! => makes an owned type.

```
// this will not work because Rust doesn't know which owned type you want. Many types can be made form a &str
fn main() {
    let my_string = "Try to make this a String".into(); // ⚠️
}
```

```
fn main() {
    let my_string: String = "Try to make this a String".into(); // ✔️
}
```

# <font color="green">const</font>

- Rust will not use type inference.
- Values that do not change.
- more popular.
- Shadowing is not allowed. [Shadowing](shadowing.md)

```
const my_number = 8; // 🛑 Will not work there is no type!! also will give a warning; should have an uppercase name.
const MY_NUMBER :i8 = 8; // ✔️
```

# <font color="green">static</font>

- Rust will not use type inference.
- Values that do not change.
- Has a fixed memory location.
- Can act as a global var.
- Shadowing is not allowed. [Shadowing](shadowing.md)

```
static SEASONS: [&str; 4] = ["Spring", "Summer", "Fall", "Winter"];
```

# <font color="green">let</font>

- used to introduce a new set of variables into the current scope, as given by a pattern.
- immutable by default.
- use `mut` to make it mutable.

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

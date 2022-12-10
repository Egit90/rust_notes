## <font color="green">Primitive</font>

---

**`signed integers`** i8, i16, i32, i64, i128, and isize.

**`Unsigned integers`** u8, u16, u32, u64, u128, and usize.

🚀️ isize = 64 bit if possible if not, 32 bits

🚀️ If we dont choose an integer type rust will will choose i32

```
let my_number = 10  //32 Rust default

let number: u16 = 2  //u16;
let number = 2_u16   //u16;

```

# <font color="green">Chars</font>

🚀️The `char` type represents a single character

🚀️A `char` is a ‘Unicode scalar value’

🚀️We use single quote to represent a `char` `let temp = 'a';`

---

# <font color="green">Floats</font>

🚀 f32 f64
🚀 rust will choose f64 by default

```
let my _float = 5.5; //f64

let float1 = 5.0;          // this is a f64
let float2: f32 = 8.5     // this is a f32
let total= float1 + float2  //🛑🛑 WRONG we are mixing two types this will not compile
```

## <font color="green">Semicolons</font>

Almost everything in Rust is an expression. An expression is something that returns a value. If you put a semicolon you are suppressing the result of this expression.

If you end your function with an expression without a semicolon, the result of this last expression will be returned

```
// here a = 4
let a = {
    let inner = 2;
    inner * inner
};
```

➡️ skinny arrow -> what the function is returning

```
// 8 without the semicolons means return 8
fn number () -> i32 {
    8
}

fn main () {
    println!("the number is {}",number());
}
```

```
// this will return ()
fn number(){
    8;
}
```

## <font color="green">Debug Print</font>

```
fn main(){
    let my_number = {
        second_number = 8;
        second_number + 7;
    }
    println!("{}" , second_number); // 🛑 This is an error. because my_number will return ()
}
```

with this code block we will have two issues.

```
println!("{}" , second_number);
                ^^^^^^^^^^^^ `()` cannot be formatted with the default formatter
the trait `std::fmt::Display` is not implemented for `()`
```

We have to use debug printing {:?}
or pretty debug printing {:#?}

```
fn main(){
    let my_number = {
        second_number = 8;
        second_number + 7;
    }
    println!("output is: {:?}" , second_number); // => output is: ()
}
```

# <font color="green">Mutability</font>

vars are either

- mutable => can be changed
- immutable => can't be changed

🚀 vars are immutable by default

```
let my_number = 8;
println!(" My number is: {}", my_number);

my_number = 10; // 🛑 we can't vars are immutable by default
println!("My altered number is: {}" , my_number);
```

🚀 To make a var mutable we use the "mut" word.

```
let mut my_number = 8;
println!(" My number is: {}", my_number);

my_number = 10; // ✅
println!("My altered number is: {}" , my_number);
```

# <font color="green">Shadowing</font>

```
let my_number = 8;
println!(" My number is: {}", my_number);

let my_number = 9.2; // ✔️ This is a new var with  a f64 type !!
println!("My alterd number is: {}" , my_number);
```

🚀 Shadowing will not kill the first var! it only block it ...

```
fn main() {
    let my_number = 8; // This is an i32
    println!("{}", my_number); // prints 8
    {
        let my_number = 9.2; // This is an f64. It is not my_number - it is completely different!
        println!("{}", my_number) // Prints 9.2
                                  // But the shadowed my_number only lives until here.
                                  // The first my_number is still alive!
    }
    println!("{}", my_number); // prints 8
}
```

Example usage:

```
fn times_two(number: i32) -> i32 {
    number * 2
}

fn main() {
    let final_number = {
        let y = 10;
        let x = 9; // x starts at 9
        let x = times_two(x); // shadow with new x: 18
        let x = x + y; // shadow with new x: 28
        x // return x: final_number is now the value of x
    };
    println!("The number is now: {}", final_number)
}
```

# <font color="green">Stack Heap Pointers</font>

🚀 The Stack is Fast

✈️ Heap is Slower

- Rust needs to know the size of a variable at compile time.
- simple variables like i32 go on the stack, because we know their exact size.
  - You always know that an i32 is going to be 4 bytes, because 32 bits = 4 bytes. So i32 can always go on the stack.
- Some types don't know the size at compile time. But the stack needs to know the exact size. So what do you do?
  - Rust puts the data in the heap, because the heap can have any size of data
  - To find it a pointer goes on the stack.
  - This is fine because we always know the size of a pointer.
  - Computer first goes to the stack, reads the pointer, and follows it to the heap where the data is.

✔️ Pointer are like table of a content of a book

```
MY BOOK

TABLE OF CONTENTS

Chapter                        Page
Chapter 1: My life              1
Chapter 2: My cat               15
Chapter 3: My job               23
Chapter 4: My family            30
Chapter 5: Future plans         43
```

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

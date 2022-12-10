# <font color="green">Primitive</font>

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

---

# <font color="green">Debug Print</font>

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

# <font color="green">Semicolons</font>

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

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


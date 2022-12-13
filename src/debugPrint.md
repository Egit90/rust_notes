# <font color="green">Debug Print</font>

```rust
fn main(){
    let my_number = {
        second_number = 8;
        second_number + 7;
    }
    println!("{}" , second_number); // 🛑 This is an error. because my_number will return ()
}
```

with this code block we will have two issues.

```rust
println!("{}" , second_number);
                ^^^^^^^^^^^^ `()` cannot be formatted with the default formatter
the trait `std::fmt::Display` is not implemented for `()`
```

We have to use debug printing {:?}
or pretty debug printing {:#?}

```rust
fn main(){
    let my_number = {
        second_number = 8;
        second_number + 7;
    }
    println!("output is: {:?}" , second_number); // => output is: ()
}
```

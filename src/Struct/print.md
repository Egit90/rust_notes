# Printing a Struct

- You **can't** use the display formatter `println("{}")` nor the debug formatter `println{:?}` to print Struct.
- from the compiler ==> note: add `#[derive(Debug)]` to `SizeAndName` or manually `impl Debug for SizeAndName`


```rust
struct SizeAndName {   // 🛑 the trait `Debug` is not implemented for `SizeAndName` 
    size: u8,
    name: String 
}

fn main(){
    let s_c = SizeAndName{
        size: 150,
        name: String::from("elie")
    };
    println!("{:?}" , s_c);
}

```




```rust
 #[derive(Debug)] 
struct SizeAndName {
    size: u8,
    name: String 
}

fn main(){
    let s_c = SizeAndName{
        size: 150,
        name: String::from("elie")
    };
    println!("{:?}" , s_c);
}

```
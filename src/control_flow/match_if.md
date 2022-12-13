# match with if

- you can use if inside the match statement

```rust
fn main(){
    let children = 5;
    let married = true;
    match (children , married){
        (children , married) if married && children == 4 => println!("married with 4 children"),
        (children , married) if married && children == 5 => println!("married with 5 children"),
        (children , married) if married && children > 0 => println!("married with {} children" , {children}),
        _ => println!("{} , number of children {}" , married , children)
    }
}
```

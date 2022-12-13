# match example with 3 vars

```rust
fn match_colors(rgb: (u8,u8,u8)){
    match rgb {
        (r,_,_) if r < 10 => println!("not much red"),
        (_,g,_) if g < 10 => println!("not much green"),
        (_,_,b) if b < 10 => println!("not much blue"),
            _ => println!("looks good"),
    }
}
fn main(){
    let a = (200,0,0);
    let b = (50,50,50);
    let c = (200,50,0);
    match_colors(a);
    match_colors(b);
    match_colors(c);
}
```

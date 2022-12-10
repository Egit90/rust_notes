[Main](./index.md)

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

➡️ skinnt arrrow -> waht the function is returnning

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

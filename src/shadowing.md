
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

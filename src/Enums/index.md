# enum index

- if an enum does **not** have data then it will be assigned an index that can be accessed.

```rust
enum Test {
    Test1,
    Test2
}
fn main(){
    use Test::*;
    let tests = vec![Test1,Test2];
    for i in tests{
        println!("{}", i as i32);
    }
}
```

- usually they start at 0 and increment by one ... but we can give them custom value.

```rust
enum Star {
    BrownDwarf = 10 ,    // usually it is 0
    RedDwarf =50,      // usually it is 1
    YellowStar = 100,    // usually it is 2
    RedGiant = 1000,       // usually it is 3
    DeadStar ,
}

fn main(){
    use Star::*;
    let v = vec![BrownDwarf,RedDwarf, YellowStar,RedGiant,DeadStar];
    for i in v {
        println!("{}" , i as i32);
    }
}
```

```rust
enum Star {
    BrownDwarf = 10 ,    // usually it is 0
    RedDwarf =50,      // usually it is 1
    YellowStar = 100,    // usually it is 2
    RedGiant = 1000,       // usually it is 3
    DeadStar ,                  // 🍄🍄 if left unassigned it will increment by one from the last one...
}

fn main(){
    use Star::*;
    let v = vec![BrownDwarf,RedDwarf, YellowStar,RedGiant];
    for i in v {
        match i as u32 {
            size if size <= 80 => println!("Not the biggest Star"),
            size if size > 80 => println!("This is a good sized star"),
            _ => println!("other star")
        }
    }
    println!("the Dead start is {}" , DeadStar as i32);
}
```

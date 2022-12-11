# Vecs

- not as performant as arrays.
- only one type.

```rust
fn main(){
    let name1 = String::from("Elie");
    let name2 = String::from("Maatouk");

    let mut my_vec = Vec::new();
    my_vec.push(name1);
    my_vec.push(name2);

    println!("{:?}" , my_vec );
}

```

```rust
fn main(){
        let name1 = String::from("Elie");
    let name2 = String::from("Maatouk");
    let my_vec: Vec<String> = Vec::new();
    my_vec.push(name1);
    my_vec.push(name2);

    println!("{:?}" , my_vec );

}

```

```rust
fn main(){
    let my_vec = vec![1,2,3];
    println!("{:?}" , my_vec);
}

```

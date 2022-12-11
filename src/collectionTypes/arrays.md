# Arrays

- Array items are fixed in size.
- Array items have the same type.

```rust
fn main(){
    let my_array = ["a" ; 40];
    println!("{:?}" , my_array);
}

```

# Array Slicing

- use a ref

```rust
fn main(){
    let my_arr = [1,2,3,4,5,6,7,8,9,10];

    let three_to_five = &my_arr[2..5];
    let start_at_two = &my_arr[1..];
    println!("three to five {:?} , start at two {:?}" , three_to_five , start_at_two);
}

```

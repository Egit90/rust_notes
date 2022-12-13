# Tuples

- you can have multiple types in tuples.
- to get items inside a tuple .. use tuple.itemNumber ex. tuple.5
- you can destructure items.

```rust
fn main(){
    let tu = (7,5,"Elie", [12,3], vec![5,3]);
    println!("{:?}",tu);
    println!("item number 3 is {}" , tu.2);
    let (a,b,..) = ("elie" , "maatouk" ,  2 , [1,2,3]);
    println!("{}" , b);
    println!("{}" , a);

}
```

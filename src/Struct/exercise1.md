# 🏃 Exercise 1

- Create a struct called Person that has the following fields:

  - name: a string representing the person's name

  - age: an integer representing the person's age

  - email: an optional string representing the person's email address (this field should default to None)

- Then, write a function called create_person that takes in a name and age as arguments and returns a Person struct with those values.

- After that, write a main function that creates a Person struct using create_person and prints out the values of its fields.

```rust
#[derive(Debug)]
struct Person {
    name: String,
    age: u8,
    email: Option<String>
}

fn create_person (name: String , age: u8) -> Person{
    Person {
        name,
        age,
        email: None
    }
}

fn main(){
    let me = create_person("Elie".to_string() , 33);
    println!("{:#?}" , me);
}
```

# 🏃 Exercise 2

- Create a struct called Rectangle that has the following fields:

  - width: a float representing the width of the rectangle

  - height: a float representing the height of the rectangle

- Then, write methods for the Rectangle struct that calculate its:

  - area
  - perimeter
  - diagonal length (use the Pythagorean theorem to calculate this)

- Finally, write a main function that creates a Rectangle struct with a width of 4.0 and a height of 3.0, and prints out its area, perimeter, and diagonal length.

```rust
#[derive(Debug)]
struct Rectangle {
    width: f32,
    height: f32
}

impl Rectangle {
    fn calculate_area(&self) -> f32{
        self.width * self.height
    }
    fn calculate_perimeter(&self) -> f32 {
        2.0 * (self.width + self.height)
    }
    fn calculate_diagonal_length(&self) -> f32 {
        (self.width.powi(2) + self.height.powi(2)).sqrt()
    }
}

fn main() {
    let rec1 = Rectangle { width: 3.0, height: 4.5 };
    let area = rec1.calculate_area();
    let perimeter = rec1.calculate_perimeter();
    let diagonal_length = rec1.calculate_diagonal_length();
    println!("Area: {}", area);
    println!("Perimeter: {}", perimeter);
    println!("Diagonal length: {}", diagonal_length);
}

```

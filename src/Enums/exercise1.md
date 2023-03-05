# exercise 1

- Create a Shape enum with the following variants:

  - Circle(f32): represents a circle with a given radius
  - Rectangle(f32, f32): represents a rectangle with given width and height
  - Triangle(f32, f32, f32): represents a triangle with given side lengths
  - Implement a perimeter method for the Shape enum that calculates and returns the perimeter of the shape. The perimeter of a circle is its circumference, and the perimeter of a - rectangle is twice the sum of its width and height. The perimeter of a triangle is the sum of its three sides.

Once you've implemented the perimeter method, create instances of each variant of the Shape enum and call the perimeter method on them.

```rust
use std::f32::consts::PI;

enum Shape {
    Circle(f32),
    Rectangle(f32,f32),
    Triangle(f32,f32,f32)
}


impl Shape {
    fn perimeter(&self){
        match self {
            Shape::Circle(x) =>  println!("{}" ,2.0 * x * PI) ,
            Shape::Rectangle(x,y ) => println!( "{}" ,2.0 * (x + y)) ,
            Shape::Triangle(x,y ,z ) => println!("{}" ,x + y + z)
        }
    }
}

fn main(){

    let circle = Shape::Circle(5.0);
    let rectangle = Shape::Rectangle(3.0 , 4.0);
    let triangle = Shape::Triangle(5.0 , 6.0 , 7.0);

    circle.perimeter();
    rectangle.perimeter();
    triangle.perimeter();

}

```

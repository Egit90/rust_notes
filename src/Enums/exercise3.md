# 🏃 exercise 3

- Write a program that defines an enum Direction with four variants: Up, Down, Left, and Right.
- Define a struct Point with x and y fields of type i32. Add a method to the Point struct called move_point that takes a Direction argument and moves the point in that direction by one unit (i.e., increments or decrements the x or y field by one, depending on the direction).
- Finally, write a main function that creates a Point at (0, 0), moves it up and to the right, and prints the final coordinates of the point.

```rust
enum Direction {
    Up,
    Down,
    Left,
    Right
}

struct Point {
    x: i32,
    y: i32
}

impl Point {
    fn move_point(&mut self , direction: Direction){
        match direction {
            Direction::Up => self.y += 1,
            Direction::Down=> self.y -= 1,
            Direction::Right => self.x +=1 ,
            Direction::Left => self.x -=1
        }
    }
}

fn main(){
    let mut player = Point{x: 0, y: 0};
    player.move_point(Direction::Up);
    player.move_point(Direction::Left);
    println!("The player is at point x: {} , y: {}", player.x  , player.y)

}

```

[Main](./index.md)

# Stack Heap Pointers

🚀 The Stack is Fast

✈️ Heap is Slower

- Rust needs to know the size of a variable at compile time.
- simple variables like i32 go on the stack, because we know their exact size.
  - You always know that an i32 is going to be 4 bytes, because 32 bits = 4 bytes. So i32 can always go on the stack.
- Some types don't know the size at compile time. But the stack needs to know the exact size. So what do you do?
  - Rust puts the data in the heap, because the heap can have any size of data
  - To find it a pointer goes on the stack.
  - This is fine because we always know the size of a pointer.
  - Computer first goes to the stack, reads the pointer, and follows it to the heap where the data is.

✔️ Pointer are like table of a content of a book

```
MY BOOK

TABLE OF CONTENTS

Chapter                        Page
Chapter 1: My life              1
Chapter 2: My cat               15
Chapter 3: My job               23
Chapter 4: My family            30
Chapter 5: Future plans         43
```

## Important

- The pointer you usually see in Rust is called a reference.
- A reference points to the memory of another value.
- A reference means you borrow the value, but you don't own it. 🦀🦀🦀🦀
- It's the same as our book: the table of contents doesn't own the information. It's the chapters that own the information.
- In Rust, references have a & in front of them. So:

```
let my_variable = 8  // makes a regular variable
let my_reference = &my_variable // makes a reference.
```

- You can also have a reference to a reference, or any number of references.

```
fn main() {
    let my_number = 15; // This is an i32
    let single_reference = &my_number; //  This is a &i32
    let double_reference = &single_reference; // This is a &&i32
    let five_references = &&&&&my_number; // This is a &&&&&i32
}
```

# & vs \*

- - means that you take a reference away back to the value 🦀

```
fn main(){
  let my_number = 8;
  let my_reference = &my_number;
  println!("{}" , my_reference == my_number) // 🛑 Can't compare a reference to a number
                               ^^ no implementation for `&{integer} == {integer}`
}
```

https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=46766bd2625dd7036b948ee93e4b4bb0

https://gist.github.com/46766bd2625dd7036b948ee93e4b4bb0

https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&code=fn%20main()%7B%0D%0A%20%20let%20my_number%20%3D%208%3B%0D%0A%20%20let%20my_reference%20%3D%20%26my_number%3B%0D%0A%20%20println!(%22%7B%7D%22%20%2C%20my_reference%20%3D%3D%20my_number)%20%2F%2F%20%F0%9F%9B%91%20Can't%20compare%20a%20reference%20to%20a%20number%0D%0A%7D

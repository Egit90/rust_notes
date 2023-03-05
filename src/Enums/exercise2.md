# 🏃 exercise 2

- you are building a system to manage a library of books. Each book has a title, an author, and a category.
- The categories are: "Fiction", "Non-fiction", "Science fiction", "Mystery", and "Romance".

- Create an enum called Category to represent these categories, and a struct called Book to represent a book.
- The Book struct should have fields for the title, author, and category.

- Write a function called is_romance that takes a Book as input and returns true if the book's category is "Romance", and false otherwise.

- Finally, create a main function that creates three instances of Book with different titles, authors, and categories (at least one of which should be "Romance"), and calls the is_romance function on each one to check if it is a romance book. Use println! to print the result for each book.

```rust
enum Category {
    Fiction,
    NonFiction,
    ScienceFiction,
    Mystery,
    Romance,
}

struct Book {
    title: String,
    author: String,
    category: Category,
}

fn is_romance(book: Book) -> bool {
    match book.category {
        Category::Romance => true,
        _ => false,
    }
}

fn main() {
    let book1 = Book {
        title: "Pride and Prejudice".to_string(),
        author: "Jane Austen".to_string(),
        category: Category::Romance,
    };
    let book2 = Book {
        title: "The Hitchhiker's Guide to the Galaxy".to_string(),
        author: "Douglas Adams".to_string(),
        category: Category::ScienceFiction,
    };
    let book3 = Book {
        title: "The Da Vinci Code".to_string(),
        author: "Dan Brown".to_string(),
        category: Category::Mystery,
    };

    println!("Book 1 is a romance: {}", is_romance(book1));
    println!("Book 2 is a romance: {}", is_romance(book2));
    println!("Book 3 is a romance: {}", is_romance(book3));
}
```

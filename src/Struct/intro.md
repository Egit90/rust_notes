# Intro

- creating your own type, your own Data Structure. 
- By convension use upper camel case `UpperCamelCase`

## Struct Types
- Unit Struct
- Tuple Struct
- Named Struct


    ```rust
    struct FileDirectory;   // ✔️ Unit Struct
    struct Color(u8,u8,u8); // ✔️ Tuple Struct
    struct SizeAndColor {   // ✔️ Named Struch
        size: u32,
        color:  Color
    }
    fn main(){
        let _my_directory = FileDirectory;
        let my_color = Color(50,60,0);
        let my_color2 = Color(50,60,0);

        let size_color = SizeAndColor {
            size: 150,
            color:  my_color2
        };
        println!("The First Color is: {} " ,my_color.0);
    }
    ```
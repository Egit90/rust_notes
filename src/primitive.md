# <font color="green">Primitive</font>

---

**`signed integers`** i8, i16, i32, i64, i128, and isize.

**`Unsigned integers`** u8, u16, u32, u64, u128, and usize.

๐๏ธ isize = 64 bit if possible if not, 32 bits

๐๏ธ If we dont choose an integer type rust will will choose i32

```
let my_number = 10  //32 Rust default

let number: u16 = 2  //u16;
let number = 2_u16   //u16;

```

# <font color="green">Chars</font>

๐๏ธThe `char` type represents a single character

๐๏ธA `char` is a โUnicode scalar valueโ

๐๏ธWe use single quote to represent a `char` `let temp = 'a';`

---

# <font color="green">Floats</font>

๐ f32 f64
๐ rust will choose f64 by default

```
let my _float = 5.5; //f64

let float1 = 5.0;          // this is a f64
let float2: f32 = 8.5     // this is a f32
let total= float1 + float2  //๐๐ WRONG we are mixing two types this will not compile
```

[Main](index.md)

# <font color="green">const</font>

- Rust will not use type inference.
- Values that do not change.
- more popular.
- Shadowing is not allowed. [Shadowing](shadowing.md)

```
const my_number = 8; // 🛑 Will not work there is no type!! also will give a warning; should have an uppercase name.
const MY_NUMBER :i8 = 8; // ✔️
```

# <font color="green">static</font>

- Rust will not use type inference.
- Values that do not change.
- Has a fixed memory location.
- Can act as a global var.
- Shadowing is not allowed. [Shadowing](shadowing.md)

```
static SEASONS: [&str; 4] = ["Spring", "Summer", "Fall", "Winter"];
```

# <font color="green">let</font>

- used to introduce a new set of variables into the current scope, as given by a pattern.
- immutable by default.
- use `mut` to make it mutable.

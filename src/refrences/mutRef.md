# <font color="green">Mutable References</font>

- Regular reference gives you a view to the data. `&number`
  - You can have as many immutable references as you want.
- mutable reference gives you the ability to change the data. `&mut number`
  - <font color="red"> the owner must be mutable if you want to use mutable reference. </font>
  - You can have **ONLY ONE** mutable reference.
- 📝 You can't have immutable and mutable reference together.

```
let my_number = 7;
let ref = &mut my_number; // ⚠️ WRONG this will not make my_number mutable .. it has to be mutable when created
```

```
let mut my_number = 7;
let ref = &mut my_number; // ✔️

*num += 10;    // to change the value we use *
println!("{}" , my_number); // 17
```

```
let mut number =6;
let number_ref = &number;
let number_change = &mut number // 🛑 we cant borrow number as mutable because it is also borrowed as immutable
*number_change += 10; // 🛑
println!("{}" , number_ref); // 🛑
```

```
let mut number =6;
let number_change = &mut number //
*number_change += 10; // ✔️ This is fine because in this point we only have one mutable ref
let number_ref = &number;
println!("{}" , number_ref); // ✔️
```

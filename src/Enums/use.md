# use Statement

- if we don't want to write the enum name every time we can make use of the use statement.
- it is like an import.

Before ...

```rust
enum Mood{
    Happy,
    Sleepy,
    NotBad,
    Angry
}

fn match_mood(mood: &Mood) -> i32{

    let happiness_lvl = match mood {
        Mood::Happy => 10,
        Mood::Sleepy => 6,
        Mood::NotBad => 7,
        Mood::Angry => 2,
    };
    happiness_lvl

}

fn main(){
    let mood = Mood::NotBad;
    let happiness_lel = match_mood(&mood);
    println!("Happiness level is {}" , happiness_lel )
}
```

After:

```rust
enum Mood{
    Happy,
    Sleepy,
    NotBad,
    Angry
}

fn match_mood(mood: &Mood) -> i32{
    // 🍄 import every thing from this enum..
    use Mood::*;
    let happiness_lvl = match mood {
        Happy => 10,
        Sleepy => 6,
        NotBad => 7,
        Angry => 2,
    };
    happiness_lvl

}

fn main(){
    let mood = Mood::NotBad;
    let happiness_lel = match_mood(&mood);
    println!("Happiness level is {}" , happiness_lel )
}
```

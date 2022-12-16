# Intro

- 🚀 enum is about choices.
- 🚀 They can also hold data.
- 🚀 Each variant has like an invisible number that you can reference ..
  - enum = enumeration => a list of choices.
  - Upper camel case.
- enum vs struct.
  - struct is a and b and c and d ...
  - enum is a or b or c ...

```rust
enum ChoiceOfThings {
    Up,
    Down,
    Left,
    Right
}
```

Example

```rust
enum ThingsInTheSky {
    Sun,
    Stars
}

fn create_skyState (time: i32) -> ThingsInTheSky{
    match time {
        6..=18 => ThingsInTheSky::Sun,                   // 6..=18 means including 18
        _ => ThingsInTheSky::Stars
    }
}


fn check_sky_state(state: &ThingsInTheSky) {
    match state {
        ThingsInTheSky::Sun => println!("I can see the Sun"),
        ThingsInTheSky::Stars => println!("I can see the Stars"),
    }
}


fn main(){
    let time = 8;
    let sky_state = create_skyState(time);
    check_sky_state(&sky_state);
}
```

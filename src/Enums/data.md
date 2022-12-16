# enum data

```rust
enum ThingsInTheSky {
    Sun(String),
    Stars(String)
}

fn create_skyState (time: i32) -> ThingsInTheSky{
    match time {
        // 🍄 now when we match we can add data 🍄
        6..=18 => ThingsInTheSky::Sun(String::from("I can see the Sun")),
        _ => ThingsInTheSky::Stars(String::from("I can see the Stars")),
    }
}


fn check_sky_state(state: &ThingsInTheSky) {
    match state {
        // 🍄 Now we can access the data
        ThingsInTheSky::Sun(desc) => println!("{}",desc),
        ThingsInTheSky::Stars(desc) => println!("{}",desc),
    }
}


fn main(){
    let time = 8;
    let sky_state = create_skyState(time);
    check_sky_state(&sky_state);
}
```

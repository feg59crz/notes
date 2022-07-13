# Making a Guessing Game
`let`, `match`, methods, associated functions using external crates and more.

## First
- ask user for input
- process that input
- check if the input is in the expected form.
```rust
use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}
```
### Structure
- `use std::io;`
    - `use` bring that type into scope explicitly
    - `std` standard library
    - `io` input output library
- `println!();` macro
- `let` create a variable
    - `let mut` create a mutable variable
- `//comment`

## Final
- [guessing game](https://github.com/feg59crz/rust-guessing-game) (github repo)
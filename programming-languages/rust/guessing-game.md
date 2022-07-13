# Making a Guessing Game
`let`, `match`, methods, associated functions using external crates and more.

## 1_ver
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
#### Basic
- `use std::io;`
    - `use` bring that type into scope explicitly
    - `std` standard library
    - `io` input output library
- `println!();` macro
- `let` create a variable
    - `let mut` create a mutable variable
- `//comment`
- `String::new()` new instance of a String
- `::` association
#### User input
- `io::stdin()` (`std::io::stdin`) 
    - returns a instance of `std::io::Stdin`
    - handle user input
- `.read_line()`
    - call read_line method to get input form user.
- `&`
    - reference
    - let multiple parts of your code access one piece of data without needing to copy that data
    - `&mut` mutable reference
- `expect();`
    - `read_line` returns a Result.
    - Result is an enumeration.
    - Result's variants: `Ok` or `Err`
#### Printing
- `println!("You guessed: {guess}");`
- `println!("x = {} and y = {}", x, y);`
    - `{}` - placeholders

## 2_ver
### Dependencies
```toml
# ./Cargo.toml
[dependencies]
rand = "0.8.3"
```
- `rand` crate that generates random numbers
- `0.8.3` shorthand for `^0.8.3`
    -  any version that is at least 0.8.3 but below 0.9.0
### Cargo.lock

file that lock requirements version (to not brake)
- `$ cargo update` ->  will ignore the Cargo.lock file and figure out all the latest versions that fit the specifications in Cargo.toml

### Random Number
```rust
use std::io;
use rand::Rng;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    println!("The secret number is: {secret_number}");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}
```
- `use rand::Rng`
    - `Rng` Random Number Generator
- `rand::thread_rng`
    -  particular random number generator that is local to the current thread of execution and seeded by the operating system
- `gen_range`
    - method that takes a range expression as an argument and generates a random number in the range.
- `start..=end`
## Final
- [guessing game](https://github.com/feg59crz/rust-guessing-game) (github repo)
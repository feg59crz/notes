# Making a Guessing Game

`let`, `match`, methods, associated functions using external crates and more.


- [[#^5d3f93|Ver 1]]
- [[#^7a5dd5|Ver 2]]
- [[#^a4dfc1|Ver 3]]
- [[#^ac2c1f|Ver 4]]

## ver_1

^5d3f93

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
nt t
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

  

## ver_2

^7a5dd5

### Dependencies

```toml

# ./Cargo.toml

[dependencies]

rand = "0.8.3"

```

- `rand` crate that generates random numbers

- `0.8.3` shorthand for `^0.8.3`

- any version that is at least 0.8.3 but below 0.9.0

### Cargo.lock

  

file that lock requirements version (to not brake)

- `$ cargo update` -> will ignore the Cargo.lock file and figure out all the latest versions that fit the specifications in Cargo.toml

  

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

- particular random number generator that is local to the current thread of execution and seeded by the operating system

- `gen_range`

- method that takes a range expression as an argument and generates a random number in the range.

- `start..=end`

  

## ver_3

^a4dfc1

```rust

// Error on mismatched type

use std::cmp::Ordering;

fn main(){

// snip

println!("You guessed: {guess}");

  

match guess.cmp(&secret_number) {

Ordering::Less => println!("Too small!"),

Ordering::Greater => println!("Too big!"),

Ordering::Equal => println!("You win!"),

}

```

- `use std::cmp::Ordering;`

- bring type `std::cmp::Ordering` to scope

- `Ordering`

- enum

- `Less`, `Greater`, `Equal`

- `.cmp()`

- compare two values

- returns a variant of `Ordering` enum

- `match {}`

- to decide what to do based on which variant of `Ordering` was returned from the `cmp`.

- made up of _arms_ (patterns to match against, and the code that should be run if the value given to match fits that arm's pattern).

  

mismatched type error -> `guess` is a String type

### Convertion

```rust

let guess: u32 = guess.trim().parse().expect("Please type a number!");

```

- `trim` -> remove whitespaces

- `parse` -> converts a String to another type (let guess: u32)

  

## Ver_4

^ac2c1f

  

### input loop

```rust

// --snip--

  

println!("The secret number is: {secret_number}");

  

loop {

println!("Please input your guess.");

  

// --snip--

  

match guess.cmp(&secret_number) {

Ordering::Less => println!("Too small!"),

Ordering::Greater => println!("Too big!"),

Ordering::Equal => println!("You win!"),

}

}

}

  

```

  

### Quit after correct guess

```rust

// --snip--

  

match guess.cmp(&secret_number) {

Ordering::Less => println!("Too small!"),

Ordering::Greater => println!("Too big!"),

Ordering::Equal => {

println!("You win!");

break;

}

}

}

}

```

  

### Handling invalid input

```rust

// --snip--

  

io::stdin()

.read_line(&mut guess)

.expect("Failed to read line");

  

let guess: u32 = match guess.trim().parse() {

Ok(num) => num,

Err(_) => continue,

};

  

println!("You guessed: {guess}");

  

// --snip--

```

  
  

## Final

- [guessing game](https://github.com/feg59crz/rust-guessing-game) (github repo)
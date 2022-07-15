# Variables and Mutability
## Variables and Mutability
### Variables and Mutability
By default [[variable|variables]] are **immutable**.

```rust
// This code does not compile

fn main() {
    let x = 5; // immutable by default
    println!("The value of x is: {x}");
    x = 6; // cannot assign twice to immutable variable
    println!("The value of x is: {x}");
}
```

```rust
fn main() {
    let mut x = 5; // mutable
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

#### Variable name convention
In [[Rust]] [[variable|variables]] must be in the snake_case style convention.

### Constants
_[[constante|Constants]]_ are values that are bound to a name and are not allowed to change.

You aren't allowed to use `mut` with constants.

Constants can be declared in any scope.

Constants are valid for the entire time a program runs, within the scope they were declared in.

#### Constant structure
`const` keyword + constant name + `:` + datatype + `=` value.

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

#### Constant Names
Use all uppercase with underscores between words.


# Common Programming Concepts
- [[#^c0cde1|Variables and Mutability]]
	- [[#^a0e60d|Variables and Mutability]]
	- [[#^31d92f|Constants]]
	- [[#^855d0c|Shadowing]]
- [[#^325084|Data Types]]
## Variables and Mutability

^c0cde1

### Variables and Mutability

^a0e60d

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
In [[Notes/Rust/Rust]] [[variable|variables]] must be in the snake_case style convention.

### Constants

^31d92f

_[[constant|Constants]]_ are values that are bound to a name and are not allowed to change.

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

### Shadowing

^855d0c

You can declare a [[variable]] with the same name as a previous variable. Rustaceans say that the first variable is _shadowed_ by the second.
```rust
// Shadowing and Scopes
fn main() {
    let x = 5; // x=5

    let x = x + 1; // x=6

    {
        let x = x * 2; // x=12
        println!("The value of x in the inner scope is: {x}");
    }
	// x=6
    println!("The value of x is: {x}");
}
```
When the scope is over, the inner shadowing ends and `x` returns to being 6.

#### Shadowing vs Mutable
The `let` keyword  is necessary.

We can change the **datatype** of variable with shadowing.
```rust
// shadowing - datatype
let spaces = "   "; // string type
let spaces = spaces.len(); // number type
```

## Data types

^325084

[[Rust]] is a statically typed language. it must know the types of all variables in the compile time.

### Multiple possible types
We must add a type notation when multiples types are possible (in this case, a variety of numbers datatypes).
```rust
let guess: u32 = "42".parse().expect("Not a number!")
```

### Scalar Types
**Scalar Types** represents a single value. 

Primary scalar types:
- integers
- floating-point numbers
- Booleans
- characters

#### Integer Types
An _integer_ is a number without a fractional component. 
- signed integers start with `i`
- unsigned integers staat with `u`

##### Types
Signed: `i8`, `i16`, `i32`, `i64`, `i128`, `isize`
- Signed are stored with the [[two's complement]] representation.
Unsigned: `u8`, `u16`, `u32`, `u64`, `u128`, `usize`

###### `isize` and `usize`
They depends on the architecture. Can be 32-bit or 64-bit.

##### Integer Literals
- Decimal: `98_222` equal to `98222`
- Hex: `0xff`
- Octal: `0o77`
- Binary: `0b1111_0000`
- Byte(`u8` only): `b'A'`

#### Floating-Point Types
Numbers with decimal point.

Rust’s floating-point types are `f32` and `f64`.

The default type is `f64`.
```rust
fn main() {
    let x = 2.0; // f64 - double precision

    let y: f32 = 3.0; // f32 - single precision
}
```

#### Numeric Operations
```rust
fn main() {
    // addition
    let sum = 5 + 10;

    // subtraction
    let difference = 95.5 - 4.3;

    // multiplication
    let product = 4 * 30;

    // division
    let quotient = 56.7 / 32.2;
    let floored = 2 / 3; // Results in 0

    // remainder
    let remainder = 43 % 5;
}
``` 

#### Boolean Type
Boolean type has two possible values: `true`  and `false`

Booleans are one byte in size.
```rust
fn main() {
    let t = true;

    let f: bool = false; // with explicit type annotation
}
```

#### The Character Type
We specify `char` literals with single quotes.

[[Rust]]’s `char` type is four bytes in size and represents a Unicode Scalar Value
```rust
fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // with explicit type annotation
    let heart_eyed_cat = '😻';
}
```

### Compound Types
Can group multiple values into one value.

[[Rust]] has two primitive compound types: [[tuple|tuples]] and [[array|arrays]].

#### The Tuple Type
A [[tuple]] is a general way of group diferent datatypes itens into one compound type.

A tuple is defined by the `tup` keyword.

```rust
// tuple definition
fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
}
```

```rust
// pattern matching to destructure a tuple value
fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {y}");
}
```

##### Acessing a Tuple element
```rust
// accessing a tuple element directly by using a period (.) followed by the index of the value
fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
}
```

#### The Array Type
Unlike a [[tuple]], every element of an [[array]] must have the same type.

Arrays in [[Rust]] have a fixed length.

Arrays are useful when you want your data allocated on the stack rather than the heap.

Arrays are useful when you know the number of elements will not need to change.
```rust
// Array
fn main() {
    let a = [1, 2, 3, 4, 5];

	let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];

	// The number 5 indicates that the array contains 5 elements.
	let a: [i32; 5] = [1, 2, 3, 4, 5];

	// The array `a` contains 5 elements that will be set to the value 3 initially.
	let a = [3; 5]; 
}
```

##### Acessing the Array element
```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

    let first = a[0]; //by index 1
    let second = a[1];
}
```
# Cargo "Hello, World"
## Project creation
```console
$ cargo new hello_cargo
$ cd hello_cargo
````

- generates a git repository
- generates a `src` folder with the `main.rs` file
- generates a file `Cargo.toml`

## Cargo.toml
- `[package]` package configs.
- `[dependecies]` -> `crates` (packages of code are referred to as crates.)

## Building and Running
- `cargo build` -> build
- `cargo run` -> build(if not) & run
- `cargo check` -> fast checkup
- `cargo build --release` -> build with optimizations

## Github
https://github.com/feg59crz/rust-hello-cargo

# Rust Basics Course for Experienced Programmers

## Section 2: Tooling & Basic Language Elements

***


## Objectives

- Familiarize with the Rust toolchain: `rustup`, `cargo`, and `rustc`
- Understand Rust’s project structure and build process
- Learn Rust syntax essentials: variables, constants, data types, and control flow
- Compare Rust syntax and behavior with Python and C to leverage prior experience

***

## Rust Tooling Overview

### rustup

- The recommended Rust installer and version manager
- Allows easy installation of Rust and switching between versions and channels (stable, beta, nightly)
- Commands: `rustup update`, `rustup default stable`, `rustup show`

### cargo

- Rust’s build system and package manager
- Manages dependencies (crates), compiles code, runs tests, and more
- Commands:
        - `cargo new <project>` – creates a new Rust project
        - `cargo init` – initializes a new Cargo project in an existing directory
        - `cargo build` – compiles the project
        - `cargo run` – compiles & runs the project
        - `cargo test` – runs tests
        - `cargo doc --open` – generates and opens documentation

### rustc

- The Rust compiler (usually used behind the scenes by Cargo)
- Compile a single file: `rustc main.rs`

***

## Rust Project Structure with Cargo

```text
my_project/
├── Cargo.toml        # Manifest file with project metadata & dependencies
└── src/
    └── main.rs       # Entry point for an executable binary
```

- `Cargo.toml` defines project name, version, dependencies, edition (e.g. 2021)
- `src/main.rs` contains the program source code
- Additional modules under `src/` or libraries may be added later

### About Cargo.toml

The `Cargo.toml` file is the manifest for a Rust project. It configures project metadata, dependencies, and build settings. Here are the main fields and their meanings:

- **[package]**: Contains metadata about the package/project.
  - `name`: The name of the package.
  - `version`: The current version of the package (e.g., `0.1.0`).
  - `authors`: List of authors/maintainers.
  - `edition`: Rust edition to use (e.g., `2018`, `2021`).
  - `description`, `license`, `repository`, etc.: Optional metadata fields.
- **[dependencies]**: Lists external crates (libraries) your project depends on. Each dependency can specify a version, features, and other options.
- **[dev-dependencies]**: Dependencies only needed for development or testing.
- **[lib]** and **[[bin]]**: Configure library or binary targets if your project has multiple outputs.
- **[features]**: Optional named feature sets for conditional compilation.

Example minimal `Cargo.toml`:

```toml
[package]
name = "my_project"
version = "0.1.0"
edition = "2021"

[dependencies]
rand = "0.8"
```

This example declares a package named `my_project`, version `0.1.0`, using the 2021 edition, and depending on the `rand` crate version 0.8.

### Rust Editions

Rust editions are a mechanism to introduce changes in the language that might otherwise break backward compatibility, without fragmenting the ecosystem. Each edition allows Rust to evolve by including new features or syntax changes that can conflict with older code, such as the introduction of new keywords like `async` and `await`. However, editions are opt-in: existing code continues to compile under its original edition unless explicitly migrated.

The choice of edition is specified in the `Cargo.toml` file for each project, and all Rust compiler versions support all previous editions to ensure interoperability between crates using different editions. This means old and new code can coexist and work together seamlessly.

As of now, four editions exist:

- **Rust 2015**: The original edition with the stable release of Rust 1.0.  
- **Rust 2018**: Added improvements like module system reorganization and new keywords (`async`/`await`).  
- **Rust 2021**: Introduced some bug fixes, enhanced macros, and quality-of-life improvements.  
- **Rust 2024**: The latest edition with further enhancements, including changes to ownership model and unsafe code handling.

Each edition packages a set of updates and improvements while maintaining the guarantee that Rust code compiled in any edition will interoperate without issues.

This editions system helps Rust evolve smoothly and keeps the language modern without breaking existing codebases.

***

## Variables and Mutability

- Variables are immutable by default, promoting safer, predictable code  
- Use `mut` keyword to make a variable mutable

```rust
let x = 5;          // immutable
let mut y = 10;     // mutable
y += 3;
println!("x: {}, y: {}", x, y);
```

### Key difference

Rust enforces immutability strictly, unlike Python and C where mutability is the norm.

### Variables with Explicit Types

In Rust you can declare variables with explicit types. The syntax for declaring a variable with a type is:

```rust
let variable_name: Type = value;
```

For example:

```rust
let x: i32 = 42;
let name: &str = "Alice";
```

Rust's compiler usually infers the type from the assigned value, so specifying the type is often optional. However, you must annotate the type explicitly if the compiler cannot infer it or if you want to be very clear.

#### Main Rust Data Types

- **Scalar Types:**
  - Signed integers: `i8, i16, i32, i64, i128`
  - Unsigned integers: `u8, u16, u32, u64, u128`
  - Floating-point numbers: `f32, f64`
  - Boolean: `bool` (`true` or `false`)
  - Character: `char` (Unicode scalar)

- **Compound Types:**
  - Tuples: a fixed-size collection of values of different types — e.g., `(i32, f64, char)`
  - Arrays: fixed-size list of values of the same type — e.g., `[i32; 5]`

#### Example with explicit types

```rust
fn main() {
    let age: u8 = 30;
    let height: f64 = 1.75;
    let is_student: bool = false;
    let name: &str = "Bob";

    let pair: (i32, char) = (42, 'x');
    let numbers: [i32; 3] = [10, 20, 30];

    println!("Name: {}, Age: {}, Height: {}", name, age, height);
    println!("Pair: {:?}, Numbers: {:?}", pair, numbers);
}
```

This explicit typing helps make the code clear and can prevent some types of bugs early.

***

## Constants and Shadowing

- Constants declared with `const` must have a type and are always immutable  
- Shadowing allows redeclaring variables with the same name, changing type or value

```rust
const MAX_POINTS: u32 = 100_000;

let x = 5;
let x = x + 1;    // shadows previous x
let x = x * 2;
println!("x is {}", x);
```

***

## Common Operations on Variables

```rust
let a = 10;
let b = 3;
println!("Sum: {}", a + b);
println!("Product: {}", a * b);
let c = a % b;   // remainder
println!("Remainder: {}", c);
```

***

## Control Flow

### if Expressions

Rust’s `if` is an expression that returns a value:

```rust
let number = 7;
let result = if number % 2 == 0 { "even" } else { "odd" };
println!("Number is {}", result);
```

```rust
// if-else-if example returning a value
let n = -3;
let sign = if n > 0 {
  "positive"
} else if n < 0 {
  "negative"
} else {
  "zero"
};
println!("n is {}", sign);
```

### Loops

- `loop` — infinite loop until `break`
- `while` — loop while condition is true
- `for` — iterate over a range or collection

```rust
for i in 1..5 {    // Range expression: 1 to 4
    println!("i is {}", i);
}
```

***

## Expressions vs Statements

- Expressions return a value and can be part of other expressions  
- Statements perform an action but do not return a value  
- Example:

```rust
let y = {
    let x = 3;
    x + 1  // no semicolon, so this is an expression returning 4
};
println!("y is {}", y);
```

This differs from C or Python where the distinction is less explicit.

***

## Summary and Differences to Python/C

| Concept            | Rust                                 | Python                           | C                                 |
|--------------------|--------------------------------------|----------------------------------|-----------------------------------|
| Variable mutability| Immutable by default, use `mut`      | Mutable                          | Mutable (no restriction)          |
| Constants          | `const` with explicit type            | `const` use rare                 | `#define` and `const`             |
| Control flow       | `if` returns values (expressions)     | Statements                       | Statements                        |
| Loop ranges        | `for` with range syntax (`1..5`)      | `range` function                 | `for` loop with init/condition`   |

***

## Exercises


1. Create a new project with Cargo and write a program that declares:
    - An immutable variable with your name (string literal)
    - A mutable counter that increments in a loop printing each value

2. Define a constant PI with an appropriate floating point value and print it.

3. Write a function that uses an `if` expression to return whether a number is positive, negative, or zero.

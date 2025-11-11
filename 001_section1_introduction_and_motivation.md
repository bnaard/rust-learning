
# Rust Basics Course for Experienced Programmers

## Section 1: Introduction & Motivation

***

## Objectives

- Understand Rust's design philosophy and main goals.
- Recognize the key differences between Rust and familiar languages like Python and C.
- Learn the real-world use cases and why Rust is gaining popularity.
- Set up the Rust development environment and write the first simple program.

***

## What is Rust?

Rust is a systems programming language focused on three key principles:

- **Safety:** Prevents common bugs like null pointer dereferencing and data races without a garbage collector.  
- **Speed:** Enables performance similar to C and C++ for low-level programming.  
- **Concurrency:** Offers fearless concurrency with a strong type system and ownership model.

Rust is designed for tasks where control over hardware and performance is essential, such as operating systems, embedded software, game engines, and web servers.

***

## Differences to Python and C

| Aspect                | Rust                                      | Python                                           | C                                        |
|-----------------------|-------------------------------------------|-------------------------------------------------|------------------------------------------|
| Typing                | Statically typed, strong                   | Dynamically typed, strong                         | Statically typed, weak                    |
| Memory management     | Ownership and borrowing system, no GC     | Garbage collection                               | Manual (malloc/free)                      |
| Safety                | Memory and thread safety guaranteed at compile time | Runtime errors common                            | Unsafe, prone to memory bugs             |
| Concurrency           | Built-in concurrency with safety          | Concurrency via threading library, less safe     | Manual threads, risky concurrency         |
| Syntax                | Modern, expressive                         | Easy to read, interpreted                        | Low-level, verbose                        |

***

## Why Learn Rust?

Rust enables developers to write highly efficient yet safe code, avoiding bugs that are common in C/C++ systems programming. It is increasingly used by major companies like Mozilla, Microsoft, and Amazon. For Python developers, Rust offers performance and control; for C programmers, it provides safety and modern abstractions.

***

## Setting Up Rust Development Environment

1. **Install Rust using rustup:**

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

1. **Verify installation:**

```sh
rustc --version
```

1. **Create your first project with Cargo (Rust’s package manager and build tool):**

```sh
cargo new hello_rust
cd hello_rust
cargo build
```

1. **Run your program:**

```sh
cargo run
```

***

## Your First Rust Program

Replace the contents of `src/main.rs` with:

```rust
fn main() {
    println!("Hello, Rust!");
}
```

Run it with `cargo run`.

***

## Summary and Takeaways

- Rust’s unique ownership model helps ensure safe memory management without a garbage collector.
- It bridges the gap between low-level control (like C) and modern productivity (like Python).
- Setting up the Rust toolchain is straightforward with `rustup` and `cargo`.
- You wrote and ran your first Rust program!

***

Next section will cover: Variables, constants, and basic syntax in Rust.

***

[1](https://zerotomastery.io/courses/learn-rust/)
[2](https://google.github.io/comprehensive-rust/)
[3](https://doc.rust-lang.org/book/ch00-00-introduction.html)
[4](https://training.linuxfoundation.org/express-learning/getting-started-with-rust-lfel1002/)
[5](https://dev.to/dantesbytes/comprehensive-rust-programming-course-5c6d)
[6](https://de.scribd.com/document/638118572/Rust-Programming)
[7](https://updraft.cyfrin.io/courses/rust-programming-basics/course-intro/course-intro)
[8](https://blog.jetbrains.com/rust/2024/09/20/how-to-learn-rust/)
[9](https://github.com/AbdesamedBendjeddou/Rusty-CS)
[10](https://www.reddit.com/r/rust/comments/17bm5bz/what_are_the_best_tools_to_learn_rust_in_the_most/)

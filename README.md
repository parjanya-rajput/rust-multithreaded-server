# Multithreaded Web Server in Rust

This project implements a multithreaded web server in Rust. It is capable of handling multiple incoming TCP connections concurrently by utilizing a thread pool.

## Key Features

*   **Multithreaded:** Leverages a thread pool ([`ThreadPool`](src/lib.rs)) to handle multiple client requests simultaneously.
*   **Basic HTTP Handling:** Responds to `GET /` requests with [hello.html](hello.html) and `GET /sleep` (simulating a delay) with [hello.html](hello.html). Other requests receive a 404 response using [404.html](404.html).
*   **Modular Design:** Server logic is separated into a library crate ([`src/lib.rs`](src/lib.rs)) and a binary crate ([`src/main.rs`](src/main.rs)).

## Rust vs. C++ for Server Development

Rust offers several advantages over C++ for developing concurrent applications like web servers:

*   **Memory Safety without Garbage Collection:** Rust's ownership and borrowing system guarantees memory safety at compile time, preventing common C++ pitfalls like dangling pointers, buffer overflows, and data races in concurrent code, without the overhead of a garbage collector.
*   **Fearless Concurrency:** Rust's type system and ownership rules make it easier to write correct concurrent code. The compiler helps prevent data races, a common and hard-to-debug issue in C++ multithreaded applications.
*   **Modern Tooling:** Cargo, Rust's build system and package manager, simplifies dependency management and project building, often considered more streamlined than C++ equivalents like CMake and Conan/vcpkg.
*   **Expressive Type System:** Features like traits, generics, and sum types (enums) allow for highly expressive and safe abstractions.

## Effectiveness of Rust

Rust is highly effective for building high-performance and reliable servers:

*   **Performance:** Rust provides C/C++ level performance due to its LLVM-based compilation and fine-grained control over system resources, without sacrificing safety.
*   **Reliability:** The strong compile-time guarantees significantly reduce runtime errors and crashes, leading to more robust and maintainable server applications.
*   **Concurrency:** Built-in support for safe concurrency primitives makes it well-suited for I/O-bound applications like web servers that need to handle many connections efficiently.

## Building and Running

1.  **Build the project:**
    ```sh
    cargo build
    ```
2.  **Run the server:**
    ```sh
    cargo run
    ```
    The server will start listening on `127.0.0.1:7878`. You can access it from your web browser or using a tool like `curl`.

    *   `curl http://127.0.0.1:7878/`
    *   `curl http://127.0.0.1:7878/sleep` (This will take 5 seconds to respond)
    *   `curl http://127.0.0.1:7878/other` (This will return a 404)
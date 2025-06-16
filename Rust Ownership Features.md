Ownership is Rust’s most unique feature, and it enables Rust to make memory safety guarantees without needing a garbage collector. Rust manages through a system of ownership with a set of rule that the compiler checks ate compile time.

### Rust Ownership Rules
- Each value in Rust has a variable that’s called its owner.
- There can be only one owner at a time.
- When the owner goes out of scope, the value will be dropped.
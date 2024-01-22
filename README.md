# Rust
This repository is for learning Rust language.

### String
- String is a complex data structure in Rust. String can be either a string literal or data type.
- A string literal is like a constant at compile time, which can be stored onto the binary as a blob. While string data type, as the size is unknown at compile time, is stored on a heap.
- In case of integers, like the example below, 5 is bound to `x` and a copy is created and bounded to `y`, both pushed to the stack:
  ```
    let x = 5;
    let y = x;
  ```
- While storing string data type, there are three parts: pointer, length and capacity. This group is stored on stack while the string contents are stored on the heap. Pointer holds the address of string contents, length is the memory (bytes) that the contents of string are using, and capacity is the total amount of memory (bytes) that allocator has provided.

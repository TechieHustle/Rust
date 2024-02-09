# Rust
This repository is for learning Rust language.

### Scope in context of memory
- In Rust, every value in program is owned by someone. That 
### String in memory
- String is a complex data structure in Rust. String can be either a string literal or data type.
- A string literal is like a constant at compile time, which can be stored onto the binary as a blob. While string data type, as the size is unknown at compile time, is stored on a heap.
- In case of integers, like the example below, 5 is bound to `x` and a copy is created and bounded to `y`, both pushed to the stack:
  ```
    let x = 5;
    let y = x;
  ```
- While storing string data type, there are three parts: pointer, length and capacity. This group is stored on stack while the string contents are stored on the heap. Pointer holds the address of string contents which are in heap, length is the memory (bytes) that the contents of string are using, and capacity is the total amount of memory (bytes) that allocator has provided.
- In case of creating a copy of the string data type as below, a copy of the string data, i.e., pointer, length and capacity are copied to the stack while the contents are same in the heap.

###

- `self` is used to reference the object (an instance of `Self`) on which it's being called, `Self` is used as a reference to the type instead of an instance of `Self`.
```
  struct T { }

  impl T {
    pub mk() -> Self {

    }
    pub f (self, other: Self) -> u:64{

    }
  }
```

- `use crate::C::E{mkE, fnE, self}`: when we want 

# Collections
### String
- Strings are represented using utf-8, which is 32-bit long.
- So, `char` in Rust is 32-bit value, to ensure supporting all the possible chracters from different languages.
- Unicode - they're giant mapping from codepoints (integers) to glyphs/characters.
- Glyphs has all the notations of card decks/chess pieces among others.
- utf-8 represents codepoints which can be anywhere b/n 1, 2, 3 or 4 bytes.
- 

### Vector
- Grows/shrinks at the tail on push and pop respectively.
- 
### VecDeque
- Grows/shrinks in both the directions, 

### HashMap
- 
test_16_exec_cmd_19_prog
    Prog(vec![
        Exec,
        Exec,
        Swap,
        Cmds(vec![Sub, Swap, Num(5)]),
        Cmds(vec![
            Swap,
            Cmds(vec![Exec, Swap, Mul, Num(2)]),
            Cmds(vec![Exec, Swap, Dup, Num(2)]),
        ]),
        Num(2),
    ])


    struct Range(usize, usize);

    impl Range {
      fn slice<T, 'a, 'b> (&'a self, s1: &'b [T]) -> &'a T {
        s1[self.0..self.1] >>>>> Error as return 
      }
    }







        struct Range(usize, usize);

    impl Range {
      fn slice<T, 'a, 'b> (&'a self, s1: &'b [T]) -> &'b T {
        s1[self.0..self.1] >>>>> Error as return 
      }
    }
    Example, photo from class
    

    Question asked in the quiz: (If it was `&'static str`, it would be an issue)
    fn f<'a> (b: &'a bool) -> &'static str
    {
      if b {
        "true
      }
      else{
        "false"
      }
    }




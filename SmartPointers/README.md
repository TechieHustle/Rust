### Smart Pointers
- They work like pointers, with additional capabilities and metadata.
- Implemented using Struct and implement `Drop` & `Deref` traits. `Drop` lets us customize the code that's executed on smart pointer going out of scope. `Deref` trait allows an instance of the smart pointer to be treated like a reference or a smart pointer.
- In case of stack, usually we know the size of variables that we need to store on the stack. But it's not possible in some cases to know the size at compile time.
- Storing the data on heap is a better idea in this case.

#### Box<T> - a smart pointer
- Stores data on heap instead of stack. Stack contains only the pointer pointing to the heap.
- Uselpful in cases:
  1. Dealing with a type with unknown size at compile time.
  2. Ownership transfer of large amount of data w/o copying data.
  3. Owning a datatype which implements some trait, w/o actually knowing the type (aka trait objects).
- Example code:
```
fn main() {
    let b = Box::new(5);
    println!("b = {}", b);  // prints "5"
    // NOTE: Here b is the owner of Box, which is different from having a reference.
}
```
- The data on heap is owned by the Box, in-turn the box is owned by some variable in the program.

> 
- In case of data on stack, the data is cleared when the function calls rollback. The data is popped from the stack. However, in case of Heap, it's not clear when to clear the data.

###### Store Data on the Heap using Box<T>
- 
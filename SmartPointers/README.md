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
- So `Drop` is implemented. When a `Box` is dropped, it first drops the other data sctructures that it's pointing to - for example recursive drop calls in case of Binary Tree.
- On immutable references, drop is not called.

- Other examples of smart pointers:
  -- Box<T>, Vec<T>, String

> Side Note:
  ```
  let x = 7;
  let bx = Box::new();
      '1
  let rbx = &mut bx;
      '2 ('1 is frozen)
  let mr1 = rbx.deref_mut();

  let mr2 = rbx.deref_mut(); \\ Result in error

  ...mr1...
  ```
###### Store Data on the Heap using Box<T>

###### `RefCell<T>` & `Rc<T>`
These features give some relaxation from Rust compile time rules. Sometimes we need to allow runtime checks. For example, we can't know at compile time if we have 8th element present in a vector, as vectors can change the size during code execution.
- `RefCell<T>`:
  - Interior Mutability
  - Dynamic Borrowing
  - `pub fn borrow_mut(&self) -> RefMut<'_, T>`: It helps us to get a mutable reference from an immutable reference using `borrow_mut()`.
  ```
  let x = z;
  let rc = RefCell::new(x);   // stored on the heap
      '1
  let rrc = &rc;

  let rm1 = rrc.borrow_mut();
      :RefMut<'1, u64>
    
  let rm1 = rrc.borrow_mut();
  ```
- `Rc<T>`:
  - Multiple owners
  - Alias/share
  ```
  let x = z;
  let rc = Rc::new(x);
  let rc2 = Rc::clone(&rc); // This increments a count of the references in Rc, doesn't actually do deepcopy.
  ```
  

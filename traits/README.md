- Defines functionality of a particular type by specifying function signatures.
- Can have function signatures and default function implementation. See [this](https://doc.rust-lang.org/book/ch10-02-traits.html#default-implementations)
- A type implementation can override the default implementation.
- Traits can be passed as parameters:
    ```
    pub fn notify(item: &impl Summary) {
        println!("Breaking news! {}", item.summarize());
    }
    ```
    Here, `&impl Summary` is the trait implemented by `item` and `summarize()` is a function in the trait.
#### Trait Bounds:
- While 
### Iterators for Binary Trees
- Box new type, in smart pointers.
- There can't ever be a DAG, since there can't be two owners of an object.
- `into_iter` consumes the iterators. So, it'll be the hardes to implement.
- Pre-order traversal: a, b, d
- Tree is: a, b, c, d, e, f, g, NULL, NULL, NULL, NULL, h, NULL, NULL, NULL, NULL, i, NULL, NULL.
- Iterartors need someone to call the next() function. Using recursive calls for pre-order traversal will be tricky, as we need to figure out who should call next after the root.
- We'll need to implement this iteratively. So we can use stack to contain the subtrees.
- When we print the root, push the right child first and then push the left child.

> Iterators are called lazy, since they don't yield values until someone makes `.next()` call on the iterator.

- Stack declaration: `stk: Vec<BinTree<T>>`
- 

> Every iterator has two important things: type on which we are iterating, and the next function implementation.



- In case of mut/imm reference iterators, we can startover, but in case of owned iterators, iterator can't start again.
- So, in case of using sum(), we can consume all the iterators.
- In case of any()/all(), we might need the iterator at some different point, so we don't consume it so that the caller can do something with it later.
- 


> IntoIter: it knows how to convert itself into an itr. This is what happens, when we use `for x in xs {}`, it turns into something like `let mut i = xs.into_iter(); while let Some(x) = i.next() {....}`.

#### Iterator & IntoIterator Traits
- Any value which implements `std::iter::Iterator` trait is called an iterator:
```
trait Iterator {
    type Item;
    fn next(&mut self) -> Option<Self::Item>;
    ... // many default methods
}
```
- `Item` is the type which the iterator produces, while `next()` method returns `Some(v)` if there are some elements (`v` is the next value), `None` when there are no elements.
- In case of `IntoIterator` trait, there is `Item` and `IntoIter` type:
```
trait IntoIterator where Self::IntoIter: Iterator<Item=Self::Item> {
    type Item;
    type IntoIter: Iterator;
    fn into_iter(self) -> Self::IntoIter;
}
```
- `IntoIter` is the type of the iterator itself, while `Item` is the type it produces.

#### Iterator Adaptors
- They're like transformer, consuming an itr and creating another new one.
- The iterator adaptors remember new states.
- skip(skips some iterators from the original one), zip(yields pairs), chain(append all the elements from another vector)
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
- 
Problems observed in Concurrency
- Writing a sequence of memory can be problematic concurrenlty by multiple processes. Can mix up the writes.
- Data race.
- Deadlocks (can still happen in Rust).
- Rust can ensure that any data race which can lead to undetermined behavior can be prevented.

### Parallel
- Getting more comppute done in lesser time: scientific computations.
- 

### Threads in Rust
- Rust provides one-to-one threading model (one thread created in program creates an OS thread).
- Describe the computation using closure (equivalent to `run()` in Java) and get it to actually running by calling the closure (equivalent to `start()` in Java).
- std::thread::spawn:
```
pub fn spawn<F, T>(f: F) -> JoinHandle<T>
where
    F: FnOnce() -> T + Send + 'static,
    T: Send + 'static,
```
- FnOnce is used, since there can be only one time 
- `'static` is used to ensure that all variables exist for the whole program execution since the thread spawned can outlive the scope in which they were created (aka parent).
- `F` is used for the things that the clousre is carrying around (the environment it has captured), but not the things which are coming into it or being returned from it.
- `Send` is a marker trait is a note that a type has particular type. Gives ability to send messages from one thread to another.
- Majority types in Rust are `Send`. But transferring just the ownership can lead to problem with `Rc` or `RfCell`.
```
let rc1 = Rc::new(...),
let rc2 = Rc::clone(&rc1);              

Thread::spawn(move || {
  ...rc2....
  ....Rc::clone(&rc2) //This along with the clone in the last line can lead to racing condition.
})

... Rc::clone(&rc1).... // This along with the clone in the closure line can lead to racing condition.
```
- `arc` should be used instead of `rc`. In case of `RefCell`, we use `mutex`.
- A vector is passed to another thread with the spawn (using `Send`). In case of sharing the vector with multiple threads, use `mutex`.
- Poisoned lock (lock with mutex).
- MutexGuard: Smart pointer, use deref to get inside the and have the mutex guard. Explicit drop can be used to release the guard if there is some long running process after the use of mutex. mutex guard is dropped to release the lock when the mutex goes out of the scope.
- There is no mutex lock acquire available for mutex read.

#### Scoped Threads
- `'static` ensures the existance of reference of the thread until the parent exist.
- If we can gurantee that child terminates before parent- one way is that parent stops when child starts until all the children are finished.
- `std::thread::scope` it has a token `Scope<'scope, 'env>` to run only once (using `FnOnce`) - this helps us to relax the `'static` bound on the threads.
- The threads get scheduled in a random order. 


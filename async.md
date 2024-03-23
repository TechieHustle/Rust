async fn foo() -> T {

}

Equivalent to:
fn foo()-> impl Future<output = T>{

}

Rust (the lang) allows us to describe async computations.
Rust (the ecosystem) provides "Runtimes" that can execute async computations.

Collection(queue) of Futures that want to be run, some are ready, others are not.

async Runtime
- Single threaded async runtime.
- multi-threaded sync runtime.

On-demand async thread.


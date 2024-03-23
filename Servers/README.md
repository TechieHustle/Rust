### mpsc
- `std::sync::mpsc;` multiple senders, using the channel and one receiver.
- `sender` can be cloned.
- `Result` is used to get the outcome of send operation.
### spsc
- In case of single sender, we can't have multiple senders using the same channels.

### spmc
- One sender going out to multiple receivers. We use this in our server.
- Main thread is single producer, listening to the TCP. But we don't have it in Rust.
- However, we can achieve it using mpsc. Have only one receiver, wrap it with a mutex and then with ArcCell.
- Clone the arcs but truly only one node can receive at a time.
- Since receive is block and send is non-blocking, we have sender as single one provided by RUst in mpsc. I there were multiple.

### mpmc
- Rust also provides mpmc

### Server program walthough in the class
- Channel has a queue.
- When we have send a request using send() function call, the channels takes the ownership.
- 

`oha` is a benchmarking tool for servers in rust.


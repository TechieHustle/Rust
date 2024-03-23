let (sx, rx) = channel::new();

let data = ....;

sx.send(data).unwrap();

let recv_data = rx.recv().unwrap(); // This allows to send the data to the self which is not recommended
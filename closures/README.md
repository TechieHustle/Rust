&self - immuatable reference

&mut self - mutable reference
self - 



let f3 = || {
    vs.use_own();
};

//f3();
// vs.use_own(); //error: use of moved value "vs"

vs is consumed by f3, do it can't be used anywhere else


let f4 = move || { //here, move moves the ownership of everything inside, although not requried by the funcion.
    ws.use_immut();
}


<!-- An Example -->
f: &mut File

let log = |s| {f.write()};

log("step1")
f.write(" some text ") // It will fail complaining that f is mutably borrowed twice.

WorkAround:


f: &mut File

let log = |f, s| {f.write()};

log(f, "step1")
f.write(" some text ") // It will succeed, as we've mentioned f explicitly so mutable borrow will be returned.
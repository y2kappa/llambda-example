# Netlify lambda template (+ local testing)

Deploy a lambda to netlify and also test it locally with hyper, no docker necessary.


## Run locally
```
$ cargo build
$ ./target/debug/server
```

## Build on Mac for linux
You don't need to do it, netlify will do it for you, but you can test, if you want to.

```
$ rustup target add x86_64-unknown-linux-musl
$ brew install FiloSottile/musl-cross/musl-cross
$ cat ~/.cargo/config
[target.x86_64-unknown-linux-musl]
linker = "x86_64-linux-musl-gcc"
```


References:
- https://timryan.org/2018/07/27/cross-compiling-linux-binaries-from-macos.html
- https://john-millikin.com/notes-on-cross-compiling-rust

## To build on netlify
```
cat rust-toolchain
[toolchain]
channel = "stable"
components = ["rustfmt", "clippy"]
targets = ["x86_64-unknown-linux-musl"]
```

References:
- https://docs.netlify.com/configure-builds/manage-dependencies/#rust
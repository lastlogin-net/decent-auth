decent-auth is a library for adding login/authentication to web apps and
services.


# Features

* Simple
* Compiled to WebAssembly (using [Extism][extism]) so it can run in many
  languages (currently supports Rust, Node.js, and Go. New implementations
  can be implemented in <1000 lines of code).
* Focus on decentralized login protocols (currently supports OpenID Connect,
  ATProto OAuth, Fediverse OAuth, email, and QR code)


# Demo

There's a demo running at https://decent-auth.tn7.org

The demo is load balanced in front of the following instances:

https://decent-auth-rs.tn7.org (Native Rust backend, code
[here](https://github.com/lastlogin-net/decent-auth-rs/blob/main/examples/axum.rs))

https://decent-auth-js.tn7.org (Node.js wasm backend, code
[here](https://github.com/lastlogin-net/decent-auth-js/tree/main/examples/full))

https://decent-auth-go.tn7.org (Go wasm backend, code
[here](https://github.com/lastlogin-net/decent-auth-go/tree/main/examples/full))

All of the instances share the same sqlite database for  persisting key/value
state.


# Reasons not to use

* Still young and not reviewed for security. Probably has vulnerabilities.
* Since every request runs through single-threaded wasm it probably won't be
  very performant compared to other solutions.
* All state is currently persisted to a simple KV store interface (defaults to
  sqlite). This is done to minimize the API surface that is necessary for
  developers to need to implement if they want to use a custom store, but
  likely has performance and other implications.


[extism]: https://extism.org/

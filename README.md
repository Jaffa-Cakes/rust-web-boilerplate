# Rust Web Boilerplate

## Status

This boilerplate set-up comes preconfigured using (items in italics are planned to be added in the future):

- Yew
  - Server-Side rendered with Actix Web
  - Rehydrated on the client side
- Tonic Web API
  - gRPC Web implementation
  - Preconfigured with Yew
- *Diesel*
- *Docker*
  - *PostgreSQL Container*
  - *SSR Container*
  - *CSR Container*
- *Tailwind*

## How to Use

Simply use this repository as a template for your next project on GitHub or clone it yourself.

The `api` package holds all the code for your gRPC Web API written with Tonic.
To run this package simply use the `cargo run --package api` command.

The `client` package holds all the code for your WASM application written in Yew.
This package is to be consumed as a library by the `csr` and `ssr` packages in this workspace.

The `csr` package allows you to run your application with client side rendering if you prefer this over server side rendering.
This package should also be used when actively developing as it supports hot-reloading when changes occur via the `trunk serve ./csr/index.html` command.

The `ssr` package allows you to run your application with server side rendering.
To use this package you must first run `cargo clean` if you have been developing or running the `csr` package with Trunk, you must then run`trunk build ./csr/index.html --features ssr` to build the WASM application with server side rendering, followed by `cargo run --package ssr`.
You need to run the `cargo clean` command as errors can occur with static file compilation into the `ssr` binary when recompiling `csr` between client side rendering and server side rendering.
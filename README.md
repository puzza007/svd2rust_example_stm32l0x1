# Overview

A simple 'blinking LED' program for a Cortex-M0+ `STM32L0x1` core. The
target hardware is an STM32L031K6 Nucleo-32 board, but it should work
with any `STM32L0x1` chip with an LED attached to pin B3.

For information on using the [svd2rust](https://docs.rs/svd2rust)
utility to create a usable crate from vendor-supplied .SVD files, see
the README under the `svd_lib/stm32l0x1` directory.

# Building / Running

Config/install some Rust stuff

```shell
rustup default nightly
cargo install svd2rust form
cargo install cargo-generate
rustup target add thumbv6m-none-eabi
```

Install `gcc-arm-embedded`. On OSX it's `brew install gcc-arm-embedded`

To build the program, run `cargo build`.

To run the program, first open an OpenOCD session by running `openocd`
in the project directory. After that, `cargo run` should open a GDB
session, flash the program to the chip, and set a breakpoint at
`main()`. From there, it's a normal GDB session; you can either debug
the program or enter `continue` a couple of times to start it.

See `.cargo/config` and `openocd.gdb` for the exact commands which
`cargo run` performs - they are based off of the embedded Rust ebook
and the
[cortex-m-quickstart](https://github.com/rust-embedded/cortex-m-quickstart)
template.

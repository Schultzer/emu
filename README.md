<!--![a picture of a real-world emu](https://i.imgur.com/8CeUiar.jpg)-->
<!--# The Emu Programming Language-->
<!--[![](https://img.shields.io/crates/d/em.svg)](https://crates.io/crates/em) [![](https://img.shields.io/crates/v/em.svg)](https://crates.io/crates/em) [![](https://img.shields.io/crates/l/em.svg)](https://crates.io/crates/em)-->

# Emu is a language for programming GPUs

But unlike OpenCL/CUDA/Halide/Futhark, Emu is embedded in Rust. This lets it take advantage of the ecosystem in ways...
- `cargo build` for importing functions
- `cargo test` for testing functions
- `cargo doc` for documenting functions
- `rustc` for validating and parsing function code
- `rustc` for verifying safe data transfer to GPU
- `rustc` for familiar error reporting
- `crates.io` for hosting function code
- `docs.rs` for hosting function documentation

...that let it provide a far more streamlined system for programming GPUs. Consequently, Emu makes Rust ideal - compared to Python/Julia/C++ - for writing minimalistic programs that do robust, data-intensive computation.

```rust

// The "emu!" macro accepts a chunk of Emu code and
// generates Rust functions that can be called to perform computation on the GPU
emu! {

    // Multiply any element in given data by given coefficient
    // Data and coefficient must be floats
    function multiply(data [f32], coeff f32) {
        data[..] *= coeff;
    }
    
    // Apply sigmoid function to any element in given data
    // Data must be floats
    function sig(data [f32]) {
        let elem: f32 = data[..];
        let res: f32 = 1 / (1 + pow(E, -elem));
        data[..] = res;
    }
    
    /// Multiplies each element in given data by given coefficient
    pub fn multiply(data: &mut Vec<f32>, coeff: &f32);
    /// Applies sigmoid to each element in given data
    pub fn sig(data: &mut Vec<f32>);
    
}
```
```rust
fn main() {
    // Vector of data to be operated on
    let mut my_data = vec![0.9, 3.8, 3.9, 8.2, 2.5];
    
    // Multiply data by 10 and take sigmoid
    multiply(&mut my_data, &10.0)
    sig(&mut my_data);
}

```

To get started programming GPUs with Emu, check out [**the book**](https://github.com/calebwin/emu/tree/master/book#table-of-contents), [**the examples**](https://github.com/calebwin/emu/tree/master/examples), and [**the crate**](https://crates.io/crates/em) itself.

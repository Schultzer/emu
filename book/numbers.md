# Table of contents
- Chapter 0 - [Introduction](https://github.com/calebwin/emu/tree/master/book/introduction.md#table-of-contents)
- Chapter 1 - [Language](https://github.com/calebwin/emu/tree/master/book/language.md#table-of-contents)
- Chapter 2 - [Types](https://github.com/calebwin/emu/tree/master/book/types.md#table-of-contents)
- Chapter 3 - [Holes](https://github.com/calebwin/emu/tree/master/book/holes.md#table-of-contents)
- Chapter 4 - [Numbers](https://github.com/calebwin/emu/tree/master/book/numbers.md#table-of-contents)

# Numbers
Emu has a couple of cool little features that make working with numbers a bit easier. They are inspired by problems I (Caleb, the developer of this language) has encountered in other languages and wished I had especially when doing "scientific" programming. Numbers can be converted to be in terms of different units.

```rust
let distance: f32 = 19.2;

distance += 49.2 as cm;
distance += 2.9 as mm;
```

The above code will initialize distance to be in terms of meters and the subsequent additions will convert the quantities 49.2 and 2.9 to meters before adding. In general, using the form - `x as y` will convert `x` to be in terms of `y` using the prefix of `y` from the below list to do the conversion. The following are all supported unit prefixes.

- `Y` - `10^24`
- `Z` - `10^21`
- `E` - `10^18`
- `P` - `10^15`
- `T` - `10^12`
- `G - `10^9`
- `M` - `10^6`
- `k` - `10^3`
- `h` - `10^2`
- `D` - `10^1`
- `d` - `10^-1`
- `c` - `10^-2`
- `m` - `10^-3`
- `u` - `10^-6`
- `n` - `10^-9`
- `p` - `10^-12`
- `f` - `10^-15`
- `a` - `10^-18`
- `z` - `10^-21`
- `y` - `10^-24`

Some numbers are special - they are constants defined by symbolic formulae. Emu lets you use some of these constants in your functions without having to define them before. Below is an example of usage and a list of currently supported constants.
```rust
let num_particles: u64 = 34 * L;
```
- `PAU`
- `TAU`
- `PI`
- `E` - Euler's number
- `PHI` - golden ratio
- `R` - gas constant
- `G` - gravitational constant
- `SG` - standard gravity
- `C` - speed of light in vacuum
- `H` - Planck constant
- `K` - Boltzmann Constant
- `L` - Avogadro constant
- `MU0` - magnetic constant permeability of free space vacuum permeability

There is also a number of functions and constants that are built into the language and while documentation on them will be added soon a comprehensive list can be found at https://www.khronos.org/registry/OpenCL/specs/2.2/html/OpenCL_C.html#built-in-functions.

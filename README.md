# SRA WASM Library

![Build Status](https://github.com/zkCohort/sra-wasm/actions/workflows/rust.yml/badge.svg?branch=main)
[![Crate Version](https://img.shields.io/crates/v/sra-wasm.svg)](https://crates.io/crates/sra-wasm)
![License](https://img.shields.io/crates/l/sra-wasm)
[![Documentation](https://docs.rs/sra-wasm/badge.svg)](https://docs.rs/sra-wasm)

## Overview

This Rust library utilizes WebAssembly (WASM) to implement encryption and decryption methods based on the SRA algorithm. It provides functions for generating encryption keys, encrypting and decrypting messages, and supporting operations such as modular exponentiation and extended Euclidean algorithm. The library is intended to be used in a web application, and is designed to be compiled to WASM and used in a JavaScript application.

## SRA Algorithm

The SRA algorithm is a public-key cryptosystem that uses modular exponentiation and the extended Euclidean algorithm to encrypt and decrypt messages. The algorithm is based on the following steps:

1. Generate two large prime numbers, p and q.
2. Calculate N = p \* q.
3. Calculate phi = (p - 1) \* (q - 1).
4. Choose a number e such that 1 < e < phi and e is coprime to phi.
5. Calculate d such that d \* e = 1 (mod phi).
6. The public key is (e, N) and the private key is (d, N).
7. To encrypt a message m, calculate c = m^e (mod N).
8. To decrypt a cipher c, calculate m = c^d (mod N).

SRA is commutative, meaning that the order of encryption and decryption does not matter. This is proven by the following:

```
(m^eA mod N)^eB mod N = (m^eB mod N)^eA mod N
```

SRA is an algorithm developed by the inventors of RSA, Shamir, Rivest and Adleman. It is similar to RSA, but uses a different method for generating the public and private keys. The SRA algorithm is described in more detail in the following paper: A. Shamir, R.L. Rivest, L.M. Adleman, Mental poker, in: The Mathematical Gardner, Springer, 1981: pp. 37–43.

## Features

- Generation of SRA key pairs.
- SRA encryption and decryption.
- Modular exponentiation.
- Extended Euclidean algorithm for calculating modular inverses.

## Functions

Here is a brief description of the functions implemented in the library:

- `js_generate_phi_n`: Generates a shared phi and N while keeping p and q secret.
- `js_generate_key_pair`: Generates an SRA key pair.
- `js_encrypt`: Encrypts a message using SRA encryption.
- `js_decrypt`: Decrypts a cipher using SRA decryption.
  
  -----
- `exp_by_squaring`: Implements the exponentiation by squaring algorithm.
- `encrypt`: Encrypts a message using SRA encryption.
- `decrypt`: Decrypts a cipher using SRA decryption.
- `get_fixed_sized_prime`: Generates a fixed-size prime number.
- `generate_phi_n`: Generates a shared phi and N while keeping p and q secret.
- `extended_gcd`: Implements the extended Euclidean algorithm.
- `mod_inverse`: Calculates the modular inverse of a number.
- `generate_key_pair`: Generates an SRA key pair.

## Tests

The library includes a suite of tests to ensure correctness of the implemented functions. These tests can be run using the command `wasm-pack test --node`.

## Usage

To use this library, you need to have Rust and wasm-bindgen installed. You can then include it in your project by adding the following to your Cargo.toml file:

```toml
[dependencies]
sra_wasm = "0.1.0"
```

Then, in your main.rs file, you can use the library functions as follows:

```rust
use sra_wasm::\*;
fn main() {
// Use the library functions here
}
```

## Contribution

Contributions to this project are welcome. If you find a bug or want to add a new feature, please open an issue or submit a pull request. If your code adds new functionality, please write tests to confirm the new features function as expected.
Make sure to incorporate your changes into the CHANGELOG.md file as well.

## License

This project is licensed under the GNU GPLv3 license. See the LICENSE file for details.

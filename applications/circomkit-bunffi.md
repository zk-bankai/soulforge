# Circomkit: Bun FFI

> **Note:** This document will be part of the grant agreement. Ensure that all sections are completed accurately. Please use **markdown** format and **delete all instructional notes** before submitting.

## [Section 1] Project Information

- **Project Name:** Circomkit: Bun FFI

- **Payment Details:** 0x0000Bb8c7B69d6c1a8D6A58A3c3B1757A37C08ce

- **Total Amount Requested:** 5000 USDC

## [Section 2] Project Overview

### **Brief Description**

We aim to use [bun:ffi](https://bun.sh/docs/api/ffi) to obtain much more efficient witness calculators and provers for Circom, via [Circomkit](https://github.com/erhant/circomkit). Concretely, we aim to add the following to Circomkit:

- add `rs` option to witness calculator, to call [circom-witnesscalc](https://github.com/iden3/circom-witnesscalc) via Bun FFI.
- add `arkworks` option to provers, to call [circom-compat](https://github.com/arkworks-rs/circom-compat) via Bun FFI.
- add `lambdaworks` option to provers, to call [circom-adapter](https://github.com/lambdaclass/lambdaworks/tree/main/provers/groth16/circom-adapter)

In the end, we will have `wasm`, `c` and `rs` options for witness calculation, and `snarkjs`, `arkworks`, and `lambdawork` option for provers. We will not focus on verification, just on proof generation.

### **Core Idea**

Bun is faster runtime alternative to NodeJS, and it works with witness computations. For instance, tests written in [Circom101](https://github.com/erhant/circom101) use Bun and it is many times faster than plain Jest + NodeJS. However, it cant be used with SnarkJS, due to some compatibility issues in lower-level libraries used by SnarkJS.

WASM based provers are slow, especially on large circuits. There are faster alternatives to prove circuits and compute witnesses, such as those written in C++, Go, and Rust; but here we focus on Rust only.

All the Rust code will be bundled within a single library, perhaps shared via `node_modules` static files, or perhaps downloadable via a GitHub release asset with static link via the `latest` tag which Circomkit will download if needed.

Note that these functionalities will be included in Circomkit, which can be executed via Bun by simply doing `bunx circomkit` instead of `npx circomkit`.

If time permits, we may add NodeFFI as well; the runtime can be detected simply with `typeof Bun != "undefined"` so we can be cross-runtime-compatible as well, using the same Rust library on Node.

### **Technology Stack**

We will be using the following tech:

- **Bun**, as the JavaScript runtime and FFI provider
- **Rust**, to write the library to be compiled and connect the prover backends
- **Lambdaworks**, for Groth16 backend
- **Arkworks**, for Groth16 backend

### **Design Mockups/Prototypes**

Consider the following Rust code using iden3's `wtns_file` crate:

```rs
#[no_mangle]
pub extern "C" fn read_witness() {
    let reader = std::fs::File::open("build/multiplier_3/default/witness.wtns").unwrap();
    let x = wtns_file::WtnsFile::<32>::read(reader).unwrap();
    println!("{:?}", x);
}
```

Here, it reads the witness of some dummy multiplier circuit with two inputs. We can see that `println` in action with the following function:

```ts
import { dlopen, suffix } from "bun:ffi";

const path = `target/debug/libcircombun.${suffix}`;
const lib = dlopen(path, { read_witness: {} });
lib.symbols.read_witness();
```

To obtain that target at the path, we simply add the following to our Cargo.toml and then do `cargo build`:

```toml
[lib]
crate-type = ["cdylib"]
```

Of course, this is just PoC and in reality we would like to return some value back to JS instead of printing it.

## [Section 3] Ecosystem Fit

- **Similar Projects:** To the best of my knowledge, there aren't any JS-based Circom tooling (such as [hardhat-zkit](https://github.com/dl-solarity/hardhat-zkit) or [SHIELD](https://github.com/xorddotcom/SHIELD/)) that make use of FFI for providing alternative prover backends.

- **Unique Contribution:** Using FFI to access Rust-based prover backends and faster witness calculators will help developers work with larger circuits more easily. It will also help Circomkit reach to larger codebase by working much more efficiently in larger circuits. Finally, it will enable the usage of Bun runtime in Circom circuit development.

## [Section 4] Team

- **Team Members:** erhant

### Contact Information

- **Name:** Erhan

- **Email:** [erhany96@gmail.com](mailto:erhany96@gmail.com)

- **Prior Work/Research (Optional):** I am the author of Circomkit, which is a [widely used](https://github.com/search?q=path%3Acircomkit.json&type=code) Circom circuit testing & development tool. I have also experience with [lambdaworks](https://github.com/erhant/lambda-0b10), and some [theoretical background](https://github.com/erhant/moonmath) on zero-knowledge cryptography.

## [Section 5] Development Roadmap

### Milestone 1 — Witness Calculator & Lambdaworks

- **Estimated Duration:** 1 month

- **Description:** We plan on adding Witness calculator support via FFI, and start development of Lambdaworks prover.

- **FTE (Full-Time Equivalent):** 1

- **Costs:** 2500 USDC: time and effort, there are no realized costs for this project as all tools are open-source.

### Milestone 2 — Lambdaworks & Arkworks

- **Estimated Duration:** We aim to finish Lambdaworks prover, and continue with Arkworks prover to finish the project.

- **Description:** A detailed description of tasks to be completed under this milestone.

- **FTE:** 1

- **Costs:** 2500 USDC: time and effort, there are no realized costs for this project as all tools are open-source.

### Total Costs: 2500 + 2500 = 5000 USDC

## [Section 6] Extended Scope

- **Future Plans:** When implementations are complete, we plan on reaching out to open-source Circom projects that may use these efficient provers in their tests / development flows. If time permits, we plan on adding support for NodeJS-usable FFI as well.

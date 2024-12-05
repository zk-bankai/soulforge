# Hybrid-Hash MMCS and STIR Implementation for Plonky3

## [Section 1] Project Information

- **Project Name:** Plonky3 Enhancement: Hybrid-Hash MMCS; STIR
- **Payment Details:** 0x4f9720356Eae7000Ec2e3379caDF8990232c62a0
- **Total Amount Requested:** 45,000 USDC

## [Section 2] Project Overview :page_facing_up:

- **Brief Description:**
This project aims to enhance Plonky3 by implementing hybrid-hash mixed-matrix commitment scheme (H2M2CS) and STIR (Shift To Improve Rate). These improvements will boost Plonky3's performance and flexibility.
More details on each issue:
- https://github.com/Plonky3/Plonky3/issues/485
- https://github.com/Plonky3/Plonky3/issues/476

- **Core Idea:**
The core innovations are:
1. Hybrid-hash mixed matrix commitment scheme: Balancing fast hashes with recursion-friendly arithmetic hashes to optimize prover performance without significantly impacting verifier circuit complexity.
2. STIR implementation: Offering an alternative to FRI for low-degree testing, leading to reduced proof size at the expense of little extra prover work. This should lead to improved verification efficiency and help especially at the later stages of recursion when trying to reduce proof sizes as much as possible.

- **Technology Stack:**
  - Rust
  - Plonky3 library

- **Design Mockups/Prototypes (Optional):**
N/A

## [Section 3] Ecosystem Fit

- **Similar Projects:**
N/A

- **Unique Contribution:**
This project makes valuable contributions to the Plonky3 repo:
1. H2M2CS optimize the trade-off between prover speed and (recursive) verifier efficiency.
2. STIR implementation offers a potentially more efficient alternative to FRI, allowing for reducing proof sizes in the later stages of recursion. 

## [Section 4] Team :busts_in_silhouette:
NP Labs

- **Team Members:**
- Antonio
- César
- Marti
- (optional) intern candidate

- **Contact Information:**
  - **Name:** Marti Gorny
  - **Email:** marti@hungrycats.studio

- **Prior Work/Research (Optional):**
Antonio has contributed multiple PRs to cryptographic libraries such as arkworks or halo2, e.g.:
- https://github.com/axiom-crypto/halo2-lib/pull/98
- https://github.com/arkworks-rs/poly-commit/pull/130
- https://github.com/arkworks-rs/algebra/pull/667/

César has written about zkML, and co-authored a Ligero IOP implementation based on arkworks:
- https://github.com/NP-Eng/ligero
- https://np.engineering/posts/zkml-tradeoffs/

Marti is an arkworks core contributor and maintainer:
- https://github.com/arkworks-rs/algebra/commits?author=mmagician

## [Section 5] Development Roadmap :open_book:

### Milestone 1 — Mixed-hash Merkle Trees Implementation

- **Estimated Duration:** 3 weeks
- **Description:** 
  - Define relevant traits
  - Implement H2M2CS
  - Develop flexible configuration for hash switching
  - Benchmark performance against single-hash implementations:
    - MT construction and path verification,
    - Recursive circuit (that verifies an MT path) proving and verification, using e.g. sp1 library
  - Write comprehensive tests and documentation
- **FTE:** 2
- **Costs:** 15,000 USDC

### Milestone 2 — STIR Implementation and Integration

- **Estimated Duration:** 6 weeks
- **Description:** 
  - Implement core STIR algorithm
  - Create trait umbrella for FRI and STIR (?)
  - Benchmark performance:
    - Proof generation time, verifier time, proof size
  - Write comprehensive tests and documentation
- **FTE:** 3
- **Costs:**: 45,000 USDC

### Total Costs: 60,000 USDC

## [Section 6] Extended Scope

- **Future Plans:**
After completing the initial development phase, we plan to:
- Write a blog post about our work,
- Implement a recursive version of Blake3,
- Continue maintaining these features,
- Explore further optimizations, such as adaptive hash selection based on input size or circuit characteristics,
- Develop a recursive verifier for STIR (e.g. sp1).


# Plonky On Rails: Verifying Arithmetic Circuit Satisfiability for Plonky3

## [Section 1] Project Information

- **Project Name:** Plonky On Rails: Verifying Arithmetic Circuit Satisfiability for Plonky3
- **Payment Details:** Polygon USDC Wallet Address: 0xA3250Ab6292F2aAe7DE2DE5dC46Ba0D24dcf699E
- **Total Amount Requested:** 20,000 USDC

## [Section 2] Project Overview :page_facing_up:

- **Brief Description:**
Plonky On Rails is a tool designed to assist users of Plonky3, a recursive SNARK system, in verifying the satisfiability of arithmetic circuits and ensuring the correctness of user-defined traces. This tool will transform arithmetic circuits into SMT-LIB format and use SMT solvers to automate satisfiability checks, offering greater confidence in circuit designs. Our goal is to improve the usability and security of Plonky3, streamlining proof generation and enhancing trust in the circuits produced by developers in the zero-knowledge proof and secure computation communities.

- **Core Idea:**
The primary goal of Plonky On Rails is to create a robust and user-friendly tool that translates arithmetic circuits into SMT queries, enabling users to automatically verify their satisfiability. The tool will help developers ensure that user-defined traces are consistent with their circuits, preventing faulty or ambiguous proofs. This verification ensures circuit validity and optimizes proof generation in Plonky3, increasing trust and efficiency.

- **Technology Stack:**
  - Plonky3: Recursive SNARK framework.
  - SMT-LIB: Satisfiability Modulo Theories Library format for solving logical problems.
  - Z3 Solver: SMT solver for checking the satisfiability of logical formulas.
  - Rust: For implementing the circuit translation and verification tool.
  - Python: For building Z3Py models for proof validation.

## [Section 3] Ecosystem Fit

- **Similar Projects:**
No similar comprehensive tool for checking the satisfiability of arithmetic circuits in Plonky3 currently exists. This tool will uniquely bridge the gap by allowing users to automate circuit verification, which currently requires manual expertise.

- **Unique Contribution:**
Plonky On Rails provides a critical missing component for the Plonky3 ecosystem by automating the verification of arithmetic circuits. It ensures that users can validate their circuits and traces, significantly enhancing the trustworthiness of Plonky3 proof generation.

## [Section 4] Team :busts_in_silhouette:

- **Team Members:**
  
  - Daniel Cumming - Formal Verification Engineer:  
    Daniel Cumming's interests are related to information flow security and automating the verification of programs. Daniel studied at The University of Queensland, completing his Bachelor's and his Master's in Information Technology. Between 2020 and 2022 he worked for The University of Queensland as a research and teaching assistant as a member of the Program Analysis Centre. He assisted in teaching formal methods, computer systems, and algorithms. Daniel worked on research projects related to specifying the ARM64 instruction set, invariant generation techniques, and automatic verification of EVM bytecode smart contracts with Vale.
  
  - Gregory Makodzeba - Head of Developer Relations:  
    Gregory brings a unique combination of technical education and business-related blockchain expertise. With prior education in Aviation Management from Georgian College and a Bachelors in Computer Science from the National Technical University of Ukraine ‘Kyiv Polytechnic Institute’, Gregory has built a robust foundation in both business and engineering disciplines. His entrepreneurial spirit is evidenced by his co-founding role at Rektoff, a community-driven cybersecurity R&D company specializing in Web3 security, where he excelled in forging strategic partnerships and spearheading innovative security strategies. Beyond his business acumen, Gregory has actively contributed to the blockchain community as a mentor at ETHGlobal Waterloo and ETHToronto, guiding participants through the complexities of web3 development and security. At Runtime Verification, Gregory is leveraging his comprehensive background to enhance client engagement and drive the adoption of secure, reliable decentralized applications.
  
  - Everett Hildenbrandt - Technical Advisor:  
    Everett Hildenbrandt is a CEO of Runtime Verification. He has spent over 6 years leading the technical direction for RV's software tooling. He is passionate about providing high-quality and consistent developer tooling for all programming languages emphasizing usability and power. In his journey from studying physics to working on validating the safety of distributed Web3 applications, he's seen that formal methods can play a crucial role in improving the quality of software for everyone. During his time at RV, he's driven broader adoption of formal verification through education and bringing the verification tooling to the developers via improved UX.

- **Contact Information:**

  - **Name:** Gregory Makodzeba
  - **Email:** gregory.makodzeba@runtimeverification.com
  - **Telegram:** @gregorymakodzeba

- **Prior Work/Research (Optional):**
Runtime Verification has extensive experience in formal verification, symbolic execution, and tooling development for blockchain ecosystems, founding and developing projects like KEVM, Kontrol, Komet, and other formal verification and security tools for Solidity, Rust, WASM and other languages and ecosystems.

## [Section 5] Development Roadmap :open_book:

### Milestone 1 — Complete Functionality

- **Estimated Duration:** 1 month
- **Description:** 
  - Manual translation of the Fibonacci circuit to Z3: Manually translating the Fibonacci sequence circuit into Z3 (using Python, SMT-LIB, or Rust) to check its satisfiability.
  - Fork Plonky3: Fork the Plonky3 repository and add logging capabilities to extract Z3 models for arithmetic circuits.
  - Reproduce Automated Results: Reproduce the automated results and compare them against manually generated results for validation.
  - Extend to More Complex Examples: Implement support for more complex examples such as:
    - Fixed-size list max finder: Ensure that the circuit works efficiently with list operations to find the maximum value in a fixed-size list.
    - Newton-Raphson square root: Test a circuit that computes the square root using the Newton-Raphson method.
- **FTE (Full-Time Equivalent):** 1 FTE (1 engineer, full-time), 0.5 PTE (1 head of developer relations, part-time), 0.5 PTE (1 technical advisor, part-time)
- **Costs:** 20,000 USDC

### Total Costs: 20,000 USDC

## [Section 6] Extended Scope

- **Future Plans:**
Following the initial development, we plan to enhance the tool to support more complex circuits, recursive SNARKs, and larger constraint systems. Additionally, we aim to optimize performance and explore integration with other zkp projects. The tool will continue to evolve, offering extended support for advanced circuit designs and enabling more efficient trace verification.

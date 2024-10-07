# Enhancing zkEmail with Plonky3: Advanced Features for Decentralized Systems
## [Section 1] Project Information

Project Name: Enhancing zkEmail with Plonky3: Advanced Features for Decentralized Systems
Payment Details: 0x0ed18cFf1e16Db3f8b76D05c84182E4849ab03D4
Total Amount Requested: 15,000 USDC

## [Section 2] Project Overview :page_facing_up:

Brief Description:
This project aims to enhance zkEmail by developing new features and improvements using Plonky3, specifically tailored for decentralized systems with a focus on C2C marketplaces. We will expand zkEmail's capabilities to address data integrity, censorship resistance, and privacy, while pushing the boundaries of Plonky3's application in practical scenarios.

Core Idea:
The primary goal is to extend zkEmail's functionality by implementing the following features:

- Enhanced data integrity verification for email attachments using Plonky3
  - Experiment with most of the attachment formats
    - Write circuit in plonky3 to encode/decode base64 attachments from emails
    - Use zk-regex to parse the attachments and verify the content
    - Point out performance bottlenecks for future research and improvements

- Censorship-resistant email content verification with Plonky3's recursive proofs
  - Hash the email content
  - Port some of the existing circuits written in Circom to Plonky3
  - Use plonky3's recursive proof to chain proofs of several emails
  - Chain the proofs to generate a final proof and verify

- Develop a hybrid Plonky3-Circom system for optimized performance in zkEmail verifications

These improvements will be developed as modular components that can be integrated into various applications, with C2C markets as a primary use case.

Technology Stack:

- Plonky3 for developing high-performance ZK circuits
- Circom for compatibility with existing zkEmail components and additional circuit development
- Typescript for testing and integration
- Solidity for on-chain components (if necessary)
- Rust for performance-critical operations

## [Section 3] Ecosystem Fit

Similar Projects:
While zkEmail provides a foundation for email-based verification, our project focuses on extending its capabilities using Plonky3, specifically for decentralized marketplace scenarios.

Unique Contribution:
This project will contribute to both the zkEmail and Plonky3 ecosystems by:

- Implementing new Plonky3 circuits responsible for decoding base64 attachments allowing to run regex inside of the attachments, as requested on zkEmail's GitHub as one of the Research Ideas and pointed out as a performance bottleneck in the current implementation on [Issue 13](https://github.com/zkemail/zk-email-verify/issues/13)
- Creating a censorship-resistant method for email content verification using Plonky3's recursive proofs as improving performance on some of the current circuits written in Circom
- Implementing a privacy-preserving reputation system based on email interactions using Plonky3's lookup arguments
- Providing comprehensive documentation and examples for integrating these new Plonky3-based features into decentralized applications
- Pioneering the integration of Plonky3 with zkEmail, potentially setting a new standard for performance in email-based ZK applications
- Developing novel techniques for using Plonky3's unique features in the context of email verification

## [Section 4] Team :busts_in_silhouette:
- **Team Members:** Yash Bharti, Krishanu Dhar, Rute Figueiredo

- **Contact Information:**
  - **Name:** Yash Bharti
  - **Email:** yashbharti924@gmail.com
  - **Name:** Krishanu Dhar
  - **Email:** rony.kris@gmail.com
  - **Name:** Rute Figueiredo
  - **Email:** rfigueiredo.dev@gmail.com

- **Prior Work/Research Yash:**
  - Experience writing Circom Circuits
  - Porting Circuits between different ZK frameworks
  - Developed Binary Incremental Merkle Tree, ECDSA in Circom
  - Aztec Alpha Build Program - Wallet, Account Abstraction, Fee Paymasters
  - Rust - Distributed Systems
  - Smart Contracts with Solidity
  - ZK Circuit Writing: Halo2 (Protostar, IVC Folding Schemes), Circom
  - NYU BA CS '22, University of Cambridge - MPhil (CBL Lab) - Deferred 2025
  - AI Research Background - Deep Reinforcement Learning for Robotics, Natural Language Understanding, Cognitive Science

- **Prior Work/Research Krish:** 
   -  Full stack, smart contract and zkp developer
   -  6+ years in web3
   -  Solidity developer on EVM chains
   -  ZK circuits developer in Mina, and Aztec
   -  Built zkpoker on EVM with solidity and zokrates
   -  Experienced in Circom for ZK circuit development
   -  GitHub: https://github.com/ronykris
 

- **Prior Work/Research Rute:** 
  - Implementation of a ZK Compiler and work on optimisations for zkDSL with Rust
  - Good understanding of Halo2 and Circom functionality and source code
  - Smart Contracts with Solidity and Cairo
  - Fullstack development for several relevant web applications with high user traffic
  - GitHub: https://github.com/rutefig


## [Section 5] Development Roadmap :open_book:
### Milestone 1 — Research and Circuit Development

Estimated Duration: 1 month
Description:

- Research and design new Plonky3 circuits for email attachment integrity verification
- Develop prototype Plonky3 circuits for censorship-resistant content verification using recursive proofs
- Create a hybrid Plonky3-Circom system for optimized zkEmail verifications
- Conduct comparative analysis (with benchmarking) between Plonky3 and Circom implementations for zkEmail
- Create test suite for new zkEmail features

FTE: 1 FTE
Costs: 7,500 USDC

- Development labor: 6,000 USDC
- Software licenses and tools: 1,000 USDC
- Miscellaneous expenses: 500 USDC

### Milestone 2 — Implementation and Integration

Estimated Duration: 1 month
Description:

- Implement and optimize new Plonky3 circuits
- Integrate Plonky3 features into the zkEmail protocol
- Develop example implementations showcasing Plonky3's advantages in zkEmail scenarios, particularly for C2C markets
- Create comprehensive documentation for new Plonky3-based features
- Conduct security audits and performance benchmarks, comparing Plonky3 to existing Circom solutions

FTE: 1 FTE
Costs: 7,500 USDC

- Development labor: 6,000 USDC
- Testing and quality assurance: 1,000 USDC
- Documentation and deployment costs: 500 USDC

### Total Costs: 15,000 USDC
## [Section 6] Extended Scope

Future Plans:

- Explore advanced applications of Plonky3's recursive proofs in complex email-based verification scenarios (this will open the door for many use cases be solved in a more private way)
- Develop a library of optimized Plonky3 circuits for various email verification tasks
- Contribute improvements and optimizations back to the Plonky3 project based on our findings
- Investigate the potential for Plonky3 to enable new forms of private, verifiable communication beyond email
- Explore integration with other privacy-preserving technologies (e.g., Fully Homomorphic Encryption)
- Develop additional features for zkEmail based on community feedback
- Create educational resources on implementing Plonky3-enhanced zkEmail in various Web3 applications
- Collaborate with other projects to establish standards for high-performance, Plonky3-based email verification in decentralized systems

# [Project Name]

 Plonky3 of STIR (PoS)

## [Section 1] Project Information

  

-  **Project Name:** PoS 

-  **Payment Details:** 0x0f4161a816df6a1469430bde83aa3e197837f630

-  **Total Amount Requested:** 30000 usdc

  

## [Section 2] Project Overview :page_facing_up:

  

-  **Brief Description:**

1. Implement STIR (Scalable Transparent Interactive Reed-Solomon) for Plonky3, including both standard STIR and Circle-STIR variants.

2. Implement a Bitcoin-compatible Stark-Verifier for Plonky3, supporting both FRI and STIR-based proving systems.

-  **Core Idea:**

[STIR](https://eprint.iacr.org/2024/390) represents a cutting-edge advancement in zero-knowledge proof systems, identified as a promising future direction for Plonky3 as per this [GitHub issue](https://github.com/Plonky3/Plonky3/pull/351). 

Our project aims to integrate STIR (Scalable Transparent Interactive Reed-Solomon) into Plonky3, significantly enhancing its performance by reducing proof sizes and decreasing verifier computational costs.

Additionally, implementing the STIR verifier on Bitcoin is more cost-effective compared to the FRI verifier.

- **Technology Stack:**

Our team possesses the following key competencies essential for this project:

1. **Plonky3 Expertise:** Comprehensive understanding and hands-on experience with the Plonky3 proof system architecture and implementation.

2. **Advanced Rust Programming:** Proficient in Rust, with a focus on systems programming and cryptographic implementations.

3. **Zero-Knowledge Proof Systems:** Deep theoretical and practical knowledge of STIR, FRI (Fast Reed-Solomon Interactive Oracle Proofs), and Circle-STARK protocols.

4. **Cryptographic Engineering:** Strong background in implementing and optimizing cryptographic primitives and protocols.
5. **Bitcoin Script Programming:** Have good bitcoin script programming experience.

-  **Design Mockups/Prototypes (Optional):**

1. Refactor the FRI system:
   - Design a generic FRI trait.
   - Modify `fri_prove` and `fri_verify` functions to implement this trait.
   - Ensure the STIR struct can implement the FRI trait for compatibility.

2. Bitcoin Script Verifier Implementation:
   - Create a new repository for the Stark verifier of Plonky3 written in Bitcoin Script
   - This approach avoids adding Bitcoin-specific libraries to Plonky3, maintaining its independence.
   - Design a multi-transaction verification system for Plonky3 proofs on the Bitcoin network:
     - Split proof verification across multiple transactions
     - Optimize for on-chain efficiency and cost-effectiveness

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**


  
-  **Unique Contribution:**

Smaller proof size and less verification cost.
  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

List the names of all team members (separated by commas).

0xhhh，Dylon, Andrew, Even

-  **Contact Information:**

-  **Name:** 0xhhh

-  **Email:** hhhquickcreation@gmail.com

  

-  **Prior Work/Research (Optional):**

1. We have rewritten the uni-stark verifier of Plonky3 using Bitcoin Script. The following table shows the verifier data we have collected:

| bit security | log-blowup-factor | query-num | constraint | row-num | column-num | public-input-num  | total-verifier-script  | verify-pcs-fri-script  | verify-constraints-script  | verify-quotient-poly-script  |
|--------------|-------------------|-----------|------------|---------|------------|-------------------|------------------------|------------------------|----------------------------|------------------------------|
|    99        |          4        |    16     | Fibonacci  |   1<<3  |   2        |          3        |       7041 kb          |          6848 kb       |         120kb              |            73 kb             |
|    99        |          4        |    16     | Fibonacci  |   1<<5  |   2        |          3        |       9185 kb          |          8992 kb       |         120kb              |            73 kb             |
|    99        |          4        |    16     | Fibonacci  |   1<<10 |   2        |          3        |       14593 kb         |          14400 kb      |         120kb              |            73 kb             |
2. We have nearly completed the implementation of using Plonky3 to recursive Risc0 Proof by translating RISC0 constraint expressions into Plonky3 constraint expressions. 

3. "Simulation Extractable SNARKs based on Target linear Collision-Resistant Oracle" SCIENCE CHINA Technological Sciences, 2024.DOI: 10.1007/s11431-023-2580-5

4. "Epistle: Elastic Succinct Arguments for Plonk Constraint System" https://eprint.iacr.org/2024/872

  

## [Section 5] Development Roadmap :open_book:
  

### Milestone 1 — Basic Functionality

  

-  **Estimated Duration:** 1 month

-  **Description:**  Support multi-degree(K>2) folding feature for Fri and implement Stir for Plonky3.
-  **FTE (Full-Time Equivalent):** 1

-  **Costs:** Salary 10000u

  

### Milestone 2 — Basic Functionality



-  **Estimated Duration:** 1 month

-  **Description:**  Support a Uni-STARK verifier on Bitcoin(based OP_CAT), whether based on PCS-STIR or PCS-FRI. 
-  **FTE:** 1

-  **Costs:** Salary 10000u

### (Optional) Milestone 3 — Additional Features



-  **Estimated Duration:** 1 month

-  **Description:**  Implement Circle-Stir for Plonky3 and the corresponding verifier on Bitcoin(based OP_CAT).
-  **FTE:** 1

-  **Costs:** Salary 10000u


  


### Total Costs: 30000u

## [Section 6] Extended Scope


-  **Future Plans:**

- **Future Development Roadmap:**

1. Expand Plonky3 capabilities:
   - Implement WHIR (Weighted Holographic Interactive Reed-Solomon) protocol
   - Develop Circle-WHIR variant for enhanced performance
   
2. Bitcoin Script Integration:
   - Create efficient Bitcoin Script implementations for WHIR and Circle-WHIR verifiers
   - Ensure compatibility and optimize for on-chain verification
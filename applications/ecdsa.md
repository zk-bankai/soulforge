
# ECDSA x Plonky3

## [Section 1] Project Information

  

-  **Project Name:** ECDSA

-  **Payment Details:** 0x3c1763006FcdEa4b467cC8FE9c28Fab664d0F6ED

-  **Total Amount Requested:** 8000 USDC

  

## [Section 2] Project Overview :page_facing_up:

  

-  **Brief Description:**

**ECDSA x Plonky3** is an educational project that implements ECDSA operations over `secp256k1` curve in plonky3. 
This project will significantly expand the educational resources available for Plonky3, moving beyond basic examples such as [fibonacci example](https://github.com/BrianSeong99/plonky3_fibonacci) and [range check](https://github.com/BrianSeong99/plonky3_rangecheck) to demonstrate complex cryptographic operations in a zero-knowledge proof system. 

-  **Core Idea:**

THe primary goal of this project is to extend the educational content space from just fibonacci and range checks to something more interesting and yet so simple to understand for something like ECDSA. 
The key things that needs to be implemented is 
- Implementation of secp256k1 curve and its operations in plonky3 along with efficiently handling 256-bit fields within Plonky3's smaller, CPU-optimized fields. 
- Implementing of ECDSA Signing and Verification Algorithm. 
- Create comprehensive documentation for educational purposes
-  **Technology Stack:**

We will be using the following tech stack:

- **Lambdaworks** for native secp256k1 operations 
- **Rust** for writing circuits in plonky3
- **PLONKY3** Primary framework for zero-knowledge proof generation

## [Section 3] Ecosystem Fit
-  **Similar Projects:** 
To the best of my knowledge there aren't many projects using plonky3 except zkVMs like `SP1` and `Valida` and like i previously mentioned [fibonacci example](https://github.com/BrianSeong99/plonky3_fibonacci) and [range check](https://github.com/BrianSeong99/plonky3_rangecheck) are the begineer friendly ones i could find.

To the best of my knowledge this project will be one of the first to implement Elliptic Curve operations in Plonky3, filling a crucial gap in the ecosystem. While projects like SP1 and Valida (zkVMs) utilize Plonky3, there's a scarcity of educational content beyond basic examples like [fibonacci example](https://github.com/BrianSeong99/plonky3_fibonacci) and [range check](https://github.com/BrianSeong99/plonky3_rangecheck) 

-  **Unique Contribution:**

This project will be the one of the first projects to implement Elliptic Curves in plonky3. It will help the ecosystem to get their hands on more complex yet easy to understand projects in plonky3.

  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

-  **Contact Information 1:**

-  **Name:** Rahul Guha

-  **Email:** 19rahul2003@gmail.com

-  **Contact Information 1:**

-  **Name:** Poulav Bhowmick

-  **Email:** bpoulav@gmail.com

  

-  **Prior Work/Research (Optional):**

**Rahul**
I have worked with Starky and plonky2 before on private repositories. 
I built a very small project while learning plonky3 that [verifies a polynomial evaluation](https://github.com/guha-rahul/Plonky3-polyVerifier)
  
**Poulav**
I am a full stack developer with extensive knowledge of Rust and circom circuit.  


## [Section 5] Development Roadmap :open_book:



### Milestone 1 — Add secp256k1 curve

  

-  **Estimated Duration:** 1 month 

-  **Description:** Implement the secp256k1 curve along with the all the operations of the curve i.e addition of curve points, doubling of curve points, scalar multiplication of curve point

-  **FTE (Full-Time Equivalent):** 2 FTE

-  **Costs:** 4000 USDC


### Milestone 2 — Add ECDSA operations


-  **Estimated Duration:** 1 month

-  **Description:** Implement the signing and verification logic of ECDSA.

-  **FTE:**  2 FTE

-  **Costs:** 4000 USDC

  
  ### Total Costs: (e.g. 4,000+ 4,000 = 8,000 USDC)

## [Section 6] Extended Scope


-  **Future Plans:**

The successful completion of this project will lay the groundwork for implementing other elliptic curves (e.g., BN254, BLS12-381) in Plonky3. This could lead to the development of more advanced cryptographic primitives, such as pairing-based schemes and potentially a Groth16 verifier within the Plonky3 ecosystem.

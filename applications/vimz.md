
# VIMz: Privacy Preserving Verifiable Image Manipulation using Folding-based zkSNARKs
  

## [Section 1] Project Information

  

-  **Project Name:** VIMz

-  **Payment Details:** Provide your wallet address for USDC (on Polygon Network).

-  **Total Amount Requested:** (e.g., 12,000 USDC)

  

## [Section 2] Project Overview :page_facing_up:

### **Brief Description:**

Ensuring the authenticity and credibility of daily media on internet is an ongoing problem. Meanwhile, genuinely captured images often require refinements before publication. **_Zero-knowledge proofs (ZKPs)_** offer a solution by verifying edited image without disclosing the original source. However, ZKPs typically come with high costs, particularly in terms of prover complexity and proof size.

We propose [**VIMz**](https://github.com/zero-savvy/vimz), a framework for efficiently proving the authenticity of high-resolution images using _folding-based_ _zkSNARKs_ (using [nova](https://github.com/microsoft/Nova) proving system). We use [Circom](https://github.com/iden3/circom) to define our flding steps in nova through ([nova-scotia](https://github.com/nalinbhardwaj/Nova-Scotia) frontend). As a complete proof system, VIMz proves the integrity of both the original and edited images, as well as the correctness of the transformation without revealing intermediate images within a chain of edits---only the final result is disclosed. VIMz maintains the anonymity of the original signer and all subsequent editors while proving the authenticity of the final image. This enables the development of a privacy-preserving autonomous contract system for trustless and authentic marketplace compatible with [C2PA](https://c2pa.org/) standards. 

  Our benchmarks show that VIMz performs efficiently in both prover and verifier sides. It can practically prove the transformations on **8K (33MP) images** on **a mid-range laptop**, while reaching to **a peak memory of only 10 GB**. Moreover, VIMz has a **verification time of under 1 second** and achieves **succinct proofs of less than 11 KB** for all resolutions. VIMz's low prover complexity allows for proving multiple transformations in parallel to achieve an additional 3.5x speedup on the same laptop device.
  
  VIMz is fully open-source and available on a [public GitHub repository](https://github.com/zero-savvy/vimz). Within this repository, you will find all the code necessary for implementing zero-knowledge circuits in the Circom language, which can be used with Nova. The repository is organized into four directories: 
  
   --  **circuits:** Contains the underlying ZK circuits of VIMz in circom language.
   
   --  **contracts:** Contains high-level Solidity smart contracts that provide the infrastructure for a C2PA-compatible marketplace on EVM-based blockchains.
   
   --  **nova:** Contains the main cargo-based package for building and installing VIMz using nova protocol.
   
   --  **py_modules:** Houses the Python interface (GUI) of VIMz, facilitating image editing and preparation of input files for the VIMz prover.
   
   --  **samples:** Holds images in standard resolutions (e.g., SD, HD, 4K) along with pre-built JSON files of supported edits to be fed into the VIMz prover.
  

###  **Core Idea:**

Describe the primary goal or innovation of your project. What’s the key component or architecture? Be concise yet detailed enough to showcase the essence of the idea.

  

###  **Technology Stack:**

VIMz is based on multiple programming stacks as follows:

- **Circom:** for defining folding circuits.
- **Rust:** used by our folding scheme backend (nova).
- **Python:** for a user-friendly UI for editing images and creating inputs needed for our circuits.
- **Solidity:** for building C2PA-compatible autonomous media marketplace.

  

###  **Design Mockups/Prototypes (Optional):**

The project is available and accessible publicly as an open-source on-going project in Github: [VIMz Repo](https://github.com/zero-savvy/vimz).

  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

The concept of generating proofs for image authenticity is very new and there are some academic works are available, which most of them have some public implementations. However, the key difference is that VIMz excels in performance compared to them and is the only work that has serious developing repository in terms of industry level. specially, VIMz is the ONLY blockchain-compatible proof system of this kind because its proofs are succinct and the verifier has low complexity.
those projects are:
- https://eprint.iacr.org/2024/1066
- https://eprint.iacr.org/2024/1074
- https://arxiv.org/pdf/2211.04775
  
-  **Unique Contribution:**

All of circuits in VIMz are built purely using Circom. This is the first serious attempt on using folding-based zkSNARKs with Circom DSL in the field of media authenticity.
  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

Core contributors the project (alphabetically ordered): Stefan Dziembowski, Shahriar Ebrahimi, Parisa Hassanizadeh.
  

-  **Contact Information:**

There are two primary contat persons for the project:

-  **Contact Person 1:**
  -  **Name:** Parisa Hassanizadeh
  -  **Email:** parisaa.hassanizadeh@gmail.com
-  **Contact Person 2:**
  -  **Name:** Shahriar Ebrahimi
  -  **Email:** sh.ebrahimi92@gmail.com

### **Prior Work/Research (Optional):**

- https://eprint.iacr.org/2024/1066
- https://eprint.iacr.org/2024/1074
- https://arxiv.org/pdf/2211.04775
  

## [Section 5] Development Roadmap :open_book:

  

>  **Important:** The maximum project duration is 2 months. Outline milestones and timelines accordingly.

  

### Milestone 1 — Basic Functionality

  

-  **Estimated Duration:** (e.g., 1 month)

-  **Description:** A detailed description of the tasks and deliverables for this milestone.

-  **FTE (Full-Time Equivalent):** Indicate the total number of team members and the percentage of time they will contribute (e.g., 1.5 FTE).

-  **Costs:** (e.g., 8,000 USDC) Breakdown of estimated costs (provide a detailed category of expenses if possible).

  

### Milestone 2 — Additional Features

  

-  **Estimated Duration:** (e.g., 1 month)

-  **Description:** A detailed description of tasks to be completed under this milestone.

-  **FTE:** (e.g., 1.5)

-  **Costs:** (e.g., 4,000 USDC)

  
  ### Total Costs: (e.g. 8,000+4,000 = 12,000 USDC)

## [Section 6] Extended Scope

  

-  **Future Plans:**

Explain how you intend to extends, enhances the projects after the initial development phase. Include any plans for collaboration or integration with other projects in the ecosystem, If relevant.

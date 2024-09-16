
# VIMz: Privacy Preserving Verifiable Image Manipulation using Folding-based zkSNARKs
  

## [Section 1] Project Information

  

-  **Project Name:** VIMz

-  **Payment Details:** Provide your wallet address for USDC (on Polygon Network).

-  **Total Amount Requested:** 14,000

  

## [Section 2] Project Overview :page_facing_up:

### **Brief Description:**


Making sure that images shared online are authentic and trustworthy is a big challenge. But let's be real: most images need some tweaking before they go public. **Zero-knowledge proofs (ZKPs)** can help by verifying edited images without needing to reveal the original. The problem? ZKPs are often costly, especially when it comes to prover complexity and proof size. That's where [**VIMz**](https://github.com/zero-savvy/vimz) comes in. VIMz is a framework designed to prove the authenticity of high-resolution images efficiently using _folding-based zkSNARKs_ (powered by the [Nova](https://github.com/microsoft/Nova) proving system). With VIMz, we can verify that both the original and edited images are legit, along with the correctness of the transformations, all without revealing any intermediate versions—only the final image is exposed. Plus, VIMz keeps the identities of the original creator and subsequent editors private while proving the final image's authenticity, making it ideal for privacy-preserving, trustless marketplaces compatible with C2PA standards. It's efficient enough to handle 8K images on a mid-range laptop with minimal memory and proof size, offering fast verification and parallel processing capabilities. We formally prove the security of VIMz on our recent [paper](https://eprint.iacr.org/2024/1063).



###  **Core Idea:**

To address the prover complexity in _"proofs of media provenance,"_ we utilized the efficiency of folding schemes, specifically the [Nova](https://github.com/microsoft/Nova) protocol. More precisely, we leverage [Circom](https://github.com/iden3/circom) to define our folding steps in Nova via the [Nova-Scotia](https://github.com/nalinbhardwaj/Nova-Scotia) frontend. To ensure everything works securely, we developed a new commitment scheme for images, processing them row by row. This approach allows us to map any image transformation to a **_"folding-friendly"_** version that can be proven in Nova while also proving the commitment of the witness, i.e., the original image. For more details on the exact protocol and the formal security analysis of VIMz, refer to our recent [paper](https://eprint.iacr.org/2024/1063). With VIMz, we can verify both the original and edited images, as well as the correctness of the transformations, without revealing intermediate versions—only the final image is shown. Additionally, VIMz protects the identities of both the original creator and subsequent editors while proving the authenticity of the final image.

Our tests show that VIMz is fast and efficient on both the prover and verifier sides. For example, you can prove transformations on **8K (33MP) images** using just **a mid-range laptop**, hitting a peak memory usage of **10 GB**. Verification takes **less than 1 second**, and proof sizes come in at **under 11 KB** no matter the resolution. Plus, the low complexity of VIMz means you can prove multiple transformations in parallel, boosting performance by up to **3.5x** on the same machine.

VIMz is fully open-source and available on our [GitHub repository](https://github.com/zero-savvy/vimz). The repo is organized into several key directories:

- **circuits:** The core ZK circuits for VIMz, written in Circom.
- **contracts:** Solidity smart contracts that help create a C2PA-compatible marketplace on EVM-based blockchains.
- **nova:** The main package for building and running VIMz using the Nova protocol.
- **py_modules:** A Python-based GUI for image editing and preparing input files for the VIMz prover.
- **samples:** Sample images (SD, HD, 4K, etc.) and JSON files with supported edits ready to feed into the VIMz prover.

###  **Technology Stack:**

VIMz is based on multiple programming stacks as follows:

- **Circom:** for defining folding circuits.
- **Rust:** used by our folding scheme backend (nova).
- **Python:** for a user-friendly UI for editing images and creating inputs needed for our circuits.
- **Solidity:** for building C2PA-compatible autonomous media marketplace.

###  **Design Mockups/Prototypes (Optional):**

Project Repo: https://github.com/zero-savvy/vimz
Project Paper: https://eprint.iacr.org/2024/1063
  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

The concept of generating proofs for image authenticity is very new and there are some academic works are available, which most of them have some public implementations. However, the key difference is that VIMz excels in performance compared to them and is the only work that has serious developing repository in terms of industry level. specially, VIMz is the ONLY blockchain-compatible proof system of this kind because its proofs are succinct and the verifier has low complexity.
those projects are:
- https://eprint.iacr.org/2024/1066
- https://eprint.iacr.org/2024/1074
- https://arxiv.org/pdf/2211.04775
  
-  **Unique Contribution:**

All of circuits in VIMz are built purely using Circom. 
To this point, VIMz is the most developed, fastest and most succinct "proofs of media provenance" available. 
This is the first serious attempt on using folding-based zkSNARKs with Circom DSL in the field of media authenticity.
  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

**Core contributors the project (alphabetically ordered):** [Shahriar Ebrahimi](https://github.com/lovely-necromancer), [Parisa Hassanizadeh](https://github.com/orgs/zero-savvy/people/parizad1188).

**Recently joined team member:** [Piotr Mikołajczyk](https://github.com/orgs/zero-savvy/people/pmikolajczyk41).
  

-  **Contact Information:**

There are two primary contat persons for the project:

-  **Contact Person 1:**
   -  **Name:** Parisa Hassanizadeh
   -  **Email:** parisaa.hassanizadeh@gmail.com
-  **Contact Person 2:**
   -  **Name:** Shahriar Ebrahimi
   -  **Email:** sh.ebrahimi92@gmail.com

### **Prior Work/Research:**
Following, are some of the recent related projects that core memebers built with ZKPs (all use Circom):
 - **zRA:** transparent and non-interactive remote attestation based on zkSNARKs
     - Paper: Published on NDSS-24 conference: [Link](https://www.ndss-symposium.org/ndss-paper/from-interaction-to-independence-zksnarks-for-transparent-and-non-interactive-remote-attestation/)
     - Github: [repo](https://github.com/zero-savvy/zk-remote-attestation)
 - **ProvenView:** provable proofs of video trimming
     - Awarads: [best "proof of provenance" in zkHack Krakow by Nethermind](https://devfolio.co/projects/provenview-8e82)
     - Github: [repo](https://github.com/zero-savvy/proven-view)   
  

## [Section 5] Development Roadmap :open_book:

  

>  **We have three active team mebers and working on both milestones will start simultaneously. So, we expect to achieve both milestones by the end of 2 months.**
  

### Milestone 1 — Support of Selective Transformations

-  **Estimated Duration:** 1 month

-  **Description:** While currently we support global transformations in our **Circom** circuits (global means that the effect is done on all of the pixel images, e.g., tuning contrast or sharpness of the entire image), we need to go further and support selective transformations (e.g., you want to blur only a part of an image not the entire image). This requires additional layers of control in our **_"folding-friendly"_** image transformation functions in **Circom**. 

-  **FTE (Full-Time Equivalent):** 1.5 FTE

-  **Costs:** 5,000 USDC
   -  Circuit developements (Circom + porting to Nova + test): 
   -  Benchmarking and quantitative reports: 
   -  Formal proofs: 
  

### Milestone 2 — Integration with Sonobe Folding Library --> Full Integration with EVM

-  **Estimated Duration:** 2 months

-  **Description:** Currently we are using [nova-rs](https://github.com/microsoft/Nova) library for our folding backend. However, a more recent library [Sonobe](https://github.com/privacy-scaling-explorations/sonobe) exists that can generate Solidity verifiers for for our final compressed zkSNARKs. We plan to use our Circom circuits with that library and be able to fully deploy (without any mock contracts) our Solidity verifiers on a mainstream EVM, such as Polygon. The 100% achievement would be successful transactions on Polygon testment/mainnet proving authenticity of an image transformation using the proofs of VIMz. 
 
-  **FTE:** 1.5 FTE

-  **Costs:** 9,000 USDC
   -  Developements (porting to Sobone + finctional tests): 
   -  Writing final contracts: 
   -  Deployment and further tests on Testnet/Mainnet: 
  
  ### Total Costs: (9,000 + 5,000 = 14,000 USDC)

## [Section 6] Extended Scope

We plan to go big enough to make VIMz an standard as a trustless alternative of the C2PA initiative. So, after successfully porting the VIMz to a mainstream EVM, we will starting approaching art and photography marketplaces along with news industry to integrate VIMz with their infrastructure.  

-  **Future Plans:**

Explain how you intend to extends, enhances the projects after the initial development phase. Include any plans for collaboration or integration with other projects in the ecosystem, If relevant.


# VIMz: Privacy Preserving Verifiable Image Manipulation using Folding-based zkSNARKs
  

## [Section 1] Project Information

  

-  **Project Name:** VIMz

-  **Payment Details:** 0xD4F6DC3Ac7AfD370544F307f4A53D6f77Ed4E818 (on Polygon Network).

-  **Total Amount Requested:** 13,000

  

## [Section 2] Project Overview :page_facing_up:

### **Brief Description:**


Making sure that images shared online are authentic and trustworthy is a big challenge. But let's be real: most images need some tweaking before they go public. **Zero-knowledge proofs (ZKPs)** can help by verifying edited images without needing to reveal the original. The problem? ZKPs are often costly, especially when it comes to prover complexity and proof size. That's where [**VIMz**](https://github.com/zero-savvy/vimz) comes in. VIMz is a framework designed to prove the authenticity of high-resolution images efficiently using _folding-based zkSNARKs_ (powered by the [Nova](https://github.com/microsoft/Nova) proving system). With VIMz, we can verify that both the original and edited images are legit, along with the correctness of the transformations, all without revealing any intermediate versions—only the final image is exposed. Plus, VIMz keeps the identities of the original creator and subsequent editors private while proving the final image's authenticity, making it ideal for privacy-preserving, trustless marketplaces compatible with C2PA standards. It's efficient enough to handle 8K images on a mid-range laptop with minimal memory and proof size, offering fast verification and parallel processing capabilities. We formally prove the security of VIMz on our recent [paper](https://eprint.iacr.org/2024/1063).


###  **Core Idea:**

To address the prover complexity in _"proofs of media provenance,"_ we utilized the efficiency of folding schemes, specifically the [Nova](https://github.com/microsoft/Nova) protocol. More precisely, we leverage [Circom](https://github.com/iden3/circom) to define our folding steps in Nova via the [Nova-Scotia](https://github.com/nalinbhardwaj/Nova-Scotia) frontend. To ensure everything works securely, we developed a new commitment scheme for images, processing them row by row. This approach allows us to map any image transformation to a **_"folding-friendly"_** version that can be proven in Nova while also proving the commitment of the witness, i.e., the original image. For more details on the exact protocol and the formal security analysis of VIMz, refer to our recent [paper](https://eprint.iacr.org/2024/1063). With VIMz, we can verify both the original and edited images, as well as the correctness of the transformations, without revealing intermediate versions—only the final image is shown. Additionally, VIMz protects the identities of both the original creator and subsequent editors while proving the authenticity of the final image.

> [!NOTE]
> Our commitment scheme works regardless of the image type. Because as long in any image format, as long as you can retrieve the RGB values of each pixel, then you are good to go and can calculate the **_'folding-friendly'_** hash of the image that we proposed. More precisely, we use RGB values of images in the commitment and in our ZK circuits, so, you can publish the transformed image in any format (PNG, BMP, JPG, . . .) **as long as your format does not change the values of RGB in pixels.** So, very lossy compressions that might be available in jpg formats is not supported, but if the format does not have lossy compression, then VIMz supports it.

Our tests show that VIMz is fast and efficient on both the prover and verifier sides. For example, you can prove transformations on **8K (33MP) images** using just **a mid-range laptop**, hitting a peak memory usage of **10 GB**. Verification takes **less than 1 second**, and proof sizes come in at **under 11 KB** no matter the resolution. Plus, the low complexity of VIMz means you can prove multiple transformations in parallel, boosting performance by up to **3.5x** on the same machine.

Following table provides performance measurements of VIMz executed separately on two different devices (Core-i5 Laptop and a Ryzen 9 Server), while proving transformations on an HD resolution image. More detailed analysis are available in the paper:

| Transformation | Mid-range Laptop<br>(Key. Gen.) | Mid-range Laptop<br>(Proving) | Server<br>(Key. Gen.) | Server<br>(Proving) | Peak<br>Memory |
|:--------------:|:-------------------------------:|:-----------------------------:|:---------------------:|:-------------------:|:--------------:|
| Crop           |              3.8 s              |            187.1 s            |         3.5 s         |       133.0 s       |     0.7~GB     |
| Resize         |              11.5 s             |            187.0 s            |         6.6 s         |       135.7 s       |     2.5 GB     |
| Contrast       |              11.7 s             |            479.4 s            |         6.5 s         |       371.7 s       |     2.4 GB     |
| Grayscale      |              8.2 s              |            279.6 s            |         3.7 s         |       240.6 s       |     1.3 GB     |
| Brightness     |              11.3 s             |            474.0 s            |         6.5 s         |       372.5 s       |     2.4 GB     |
| Sharpness      |              11.8 s             |            614.1 s            |         6.8 s         |       455.8 s       |     2.8 GB     |
| Blur           |              11.5 s             |            555.3 s            |         6.6 s         |       406.0 s       |     2.5 GB     |

VIMz is fully open-source and available on our [GitHub repository](https://github.com/zero-savvy/vimz). The repo is organized into several key directories:

> [!NOTE]  
> More than 53% of the repository is **Circom**.

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

###  **Design Mockups/Prototypes:**

Project Repo: https://github.com/zero-savvy/vimz
Project Paper: https://eprint.iacr.org/2024/1063
  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

The concept of generating proofs for image authenticity is very new and there are some academic works are available, which most of them have some public implementations. However, the key difference is that VIMz excels in performance compared to them and is the only work that has serious developing repository in terms of industry level. specially, VIMz is the ONLY blockchain-compatible proof system of this kind because its proofs are succinct and the verifier has low complexity.
those other academic works are:
- https://eprint.iacr.org/2024/1066
- https://eprint.iacr.org/2024/1074
- https://arxiv.org/pdf/2211.04775
  
-  **Unique Contribution:**

All of circuits in VIMz are built purely using Circom. 
To this point, VIMz is the **most developed**, **fastest** and **most succinct** "proofs of media provenance" available. 
This is the first serious attempt on using **folding-based zkSNARKs with Circom DSL** in the field of media authenticity.
  

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

  

>  **We have three active team mebers and working on both milestones will start simultaneously. So, we expect to achieve both milestones within the time window of 2 months.**
  

### Milestone 1 — Support of Selective Transformations

-  **Estimated Duration:** 1 month

-  **Description:** While currently we support global transformations in our **Circom** circuits (global means that the effect is done on all of the pixel images, e.g., tuning contrast or sharpness of the entire image), we need to go further and support selective transformations (e.g., you want to blur only a part of an image not the entire image). This requires additional layers of control in our **_"folding-friendly"_** image transformation functions in **Circom**. 

-  **FTE (Full-Time Equivalent):** 2 FTE

-  **Costs:** 6,000 USDC
   -  Circuit developements (Circom + porting to Nova + test): 4,500
   -  Benchmarking and quantitative reports: 500
   -  Formal proofs: 1,000
  

### Milestone 2 — Integration with Sonobe Folding Library --> Full Integration with EVM

-  **Estimated Duration:** 1.5 months

-  **Description:** Currently we are using [nova-rs](https://github.com/microsoft/Nova) library for our folding backend. However, a more recent library [Sonobe](https://github.com/privacy-scaling-explorations/sonobe) exists that can generate Solidity verifiers for for our final compressed zkSNARKs. We plan to use our Circom circuits with that library and be able to fully deploy (without any mock contracts) our Solidity verifiers on a mainstream EVM, such as Polygon. The 100% achievement would be successful transactions on Polygon testment/mainnet proving authenticity of an image transformation using the proofs of VIMz. 
 
-  **FTE:** 1.5 FTE

-  **Costs:** 7,000 USDC
   -  Developements (porting Circom contrast to Sobone + functional tests): 2,300
   -  Creating Solidity verifiers for the proofs + tests: 700
   -  Writing final contracts: 2,500
   -  Deployment and further tests on Testnet/Mainnet: 1,500
  
  ### Total Costs: (6,000 + 7,000 = 13,000 USDC)

## [Demo] Details

To fully showcase the practicallity of the proposal, we plan to provide an on-chan Demo that has following phases:
1. **[setup phase]**: A spesific set of smart contracts will be deployed that can verify image manipulations through VIMz proofs.
2. **[Challenge submission]**: any entity/user can post an image of their choice on the smart contract interface as a challenge to be specidifically edited as the challenger described, and then locks a certain amount of ETH or an ERC20  token as the reward. The original image can also be submitted as a blob in case it is large.
3. **[Off-chain proving]**: A user locally edits the image as specified, and then create a zk proof of the image manipulation using VIMz.
4. **[On-chain claim]**: They send a proof of the image manipulation and the resulting edited image and collect their rewards directly from the smart contract.


**[Future Work]:** In future, after series of careful redesigns and gas optimizations done on the deployed contracts, a more involved version will allow users to send multiple specific and more precise challenges on-chain (edit an image in X, Y and Z ways), which can then be proven later on!


## [Section 6] Extended Scope

 **Future Plans:** We plan to go big enough to make VIMz an standard as a trustless alternative of the C2PA initiative. So, after successfully porting the VIMz to a mainstream EVM, we will starting approaching art and photography marketplaces along with news industry to integrate VIMz with their infrastructure. Finally, we plan to launch the first ever authentic trustless media marketplace on the ecosystem. 

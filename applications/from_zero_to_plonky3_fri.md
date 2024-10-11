
# From Zero to Plonky3 FRI
 

## [Section 1] Project Information

  

-  **Project Name:** From Zero to Plonky3 FRI

-  **Payment Details:** 0x850ff718187c15607B939A3fcf11db2B4A0Cc858 (on Polygon Network).

-  **Total Amount Requested:** 3,500 USDC

## [Section 2] Project Overview :page_facing_up:

-  **Brief Description:**

This project will first write some blog articles that demystify the fundamentals of FRI ,STARKs and small field, with a particular focus on security aspects like soundness. Then I will also write to foster a deep understanding of FRI code logic within Plonky3 for individuals, regardless of their prior knowledge of STARKs.

-  **Core Idea:**

This project aims to create blog articles that enable individuals without prior knowledge of STARKs to understand the fundamentals of FRI and STARKs with the aspect of the security, ultimately achieving a comprehensive understanding of the FRI code logic in Plonky3. 

Currently, existing articles on STARKs and FRI provide detailed explanations of the procedures involved. However, they often overlook discussing why these processes are necessary and how malicious provers could cheat without them, particularly in terms of security and soundness.

In addition, Plonky3 gives the developer to select several small finite fields and have to consider which one to use. So some developers might want to understand the security of small field and FRI. In Plonky2 and 3, methods such as parallel repetition and extension fields are combined to enhance soundness when using finite fields of small order, but these aspects are not widely understood.

Therefore, through the content produced by this project, I aim to provide STARK beginners and developers with theoretical knowledge of FRI, STARK, small field that focuses specifically on soundness, beyond what typical explanatory articles offer. 

Furthermore, the ultimate goal of this project is to explain the logic of Plonky3's FRI. It can onboard the reader from basic STARK, the mechanics of FRI and its security to an explanation of Plonky3's implementation.

- Target reader
    - Individuals seeking a basic understanding of STARK and FRI.
    - Those curious about the security aspects of FRI or small fields.
    - Developers interested in the internal coding of Plonky3.
  

-  **References for this project:**
    - [Scalable, transparent, and post-quantum secure computational integrity](https://eprint.iacr.org/2018/046.pdf)
    - [DEEP-FRI: Sampling Outside the Box Improves Soundness](https://eprint.iacr.org/2019/336.pdf)
    - [Proximity Gaps for Reed–Solomon Codes](https://eprint.iacr.org/2020/654.pdf)
    - [A summary on the FRI low degree test](https://eprint.iacr.org/2022/1216.pdf)
    - [Plonky2: Fast Recursive Arguments with PLONK and FRI](https://github.com/0xPolygonZero/plonky2/blob/main/plonky2/plonky2.pdf)
    - [Fiat-Shamir Security of FRI and Related SNARKs](https://eprint.iacr.org/2023/1071.pdf)
    - [ZKP MOOC: FRI-based Polynomial Commitments
and Fiat-Shamir](https://zk-learning.org/assets/lecture8.pdf)
    - [Plonky3 FRI Code](https://github.com/Plonky3/Plonky3/tree/main/fri/src)

## [Section 3] Ecosystem Fit

-  **Similar Projects:**

In terms of the basics of STARK and FRI, I think these contents([STARK101](https://starkware.co/stark-101/), [STARK by Hand](https://dev.risczero.com/proof-system/stark-by-hand#lesson-9-the-deep-technique), [Diving DEEP FRI in the STARK world: learning your daily moon math with a concrete example](https://blog.lambdaclass.com/diving-deep-fri/)) provide clear and detailed explanations of the execution process. However, I found that these materials often don't sufficiently explain why certain steps are necessary from a security and soundness perspective. For a long time, I had difficulty convincing myself why it had to do it in the protocol in terms of security and soundness, based only on those explanatory articles. My goal with this project is to create a step-by-step guide that not only explains how STARK and FRI work, but also emphasizes the importance of security and soundness throughout the process.

In the video of [Introduction to Plonky 1, 2 and 3](https://youtu.be/v9xZrhAuTio?si=Y3lfpqAzTtjmJ56a&t=244), it briefly mentions boosting soundness by combining extension fields and parallel repetition. But I would like to search about it more. The reason is that this information might be judgment material for developers when they choose the size of the finite field.  

Currently, I don't think there is an introductory document that delves into the internal logic of Plonky3, and I aim to fill that gap with this project.

-  **Unique Contribution:**

This project will first clarify the fundamentals of STARK and FRI, supplemented with essential security insights, to lay a strong foundation for understanding. It will then guide the audience through to comprehension of Plonky3’s FRI implementation. This sequential approach ensures that even those new to FRI and STARK can grasp complex concepts for them, ultimately leading to a thorough understanding of Plonky3’s internal logic.

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Member:** 
Yugo Cabrio

-  **Contact Information:** 
yuu5infinity@gmail.com

-  **Prior Work/Research (Optional):**   
I wrote about [Nova folding and Cycle of Curve](https://github.com/privacy-scaling-explorations/nova-by-hand) through the PSE acceleration program.

## [Section 5] Development Roadmap :open_book:

### Milestone 1 — Basic Functionality

-  **Estimated Duration:** 1 month, November

-  **Description:**
    
I am currently planning to incorporate the following, though this is only part of the full explanation. First, when explaining the STARK mechanism step by step, when the element of trace on Fp(P=97) is 4, it reproduce the simple STARK and FRI step by step, using a multiplication cyclic group of 32 whose order is 8 times the element of trace. I have already calculated a set of formulas that can be expressed “by hand”. At this point, I will discuss the reasons for expanding the domain of definition from a probabilistic point of view. 

I will also mention that if without FRI, a malicious prover intentionally chooses a polynomial of large degree, it will pass the Polynomial Identity test by using Fermat's minor theorem without. This makes it clearer why Low degree testing is necessary.

I will then explain the difference between the original FRI and the DEEP-FRI and why and how the DEEP-FRI could be improved.

The FRI code for Plonky3 will be discussed in a blog to be created in Milestone 2, but I will also introduce a snippet of simple code such as `fold_even_odd.rs` in the FRI mechanism to be created in Milestone 1.

Then I am going to read the following papers and references for a detailed explanation of the security and soundness of the FRI and small field. Milestone reports will include summaries for each of the references that I have personally prepared in addition to the blog articles that will be made available to the masses.

- Papers
    - [Proximity Gaps for Reed–Solomon Codes](https://eprint.iacr.org/2020/654.pdf)
    - [A summary on the FRI low degree test](https://eprint.iacr.org/2022/1216.pdf)
    - [Fiat-Shamir Security of FRI and Related SNARKs](https://eprint.iacr.org/2023/1071.pdf)
    - [ZKP MOOC: FRI-based Polynomial Commitments and Fiat-Shamir](https://zk-learning.org/assets/lecture8.pdf)

-  **FTE (Full-Time Equivalent):** 0.7 FTE

-  **Costs:** 2,000 USDC

### Milestone 2 — Additional Features

-  **Estimated Duration:** 1 month, December

-  **Description:** 

I plan to write an in-depth explanatory article that helps the reader understand the [FRI test codes](https://github.com/Plonky3/Plonky3/tree/main/fri/tests);`fri.rs` and `pcs.rs`. I will break down the associated codes within the FRI folder, such as `prover.rs`, `proof.rs`, `verifier.rs`, `fold_even_odd.rs`, and `two_adic_pcs.rs`. 

Recently, I have been working on a simple STARK scratch for study purposes, so I would like to take this opportunity to learn and share about the mechanism of FRI in Plonky3.

The articles developed in Milestone 1 and Milestone 2 will be published on GitHub or my personal blog, and shared across SNS.

-  **FTE:** 0.6

-  **Costs:** 1,500

  
### Total Costs: 2,000 + 1,500 = 3,500 USDC

## [Section 6] Extended Scope
-  **Future Plans:**
I would like to learn and write about how Basefold, STIR and WHIR evolved from FRI. My goal is to learn more about the theory and to be involved in the implementation of primitives related to STARK in the near future.

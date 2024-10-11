
# learning-plonky3: Deep Dive on Implementation and Theories

## [Section 1] Project Information


-  **Project Name:** *learning-plonky3: Deep Dive on Implementation and Theories*

-  **Payment Details:** 0xDfdB606dA76D96948885Da675164688b6Df5ad22

-  **Total Amount Requested:** 10,000 USDC



## [Section 2] Project Overview :page_facing_up:

  

-  **Brief Description:**

    Our project aims to develop comprehensive educational resources focused on the [Plonky3](https://github.com/Plonky3/Plonky3) toolkit. By conducting **in-depth** implementation studies and analyzing the underlying theory and principles, we seek to make Plonky3 more accessible to developers and security researchers. This project aligns with the SoulForge grant's focus on enhancing education within the Plonky3 ecosystem.


-  **Core Idea:**

    We will try to bridge the knowledge gap surrounding Plonky3 by offering a series of implementation studies and theoretical analyses. Our approach includes:

    - Thorough examination of the existing Plonky3 codebase
    - Exploration of the mathematical principles and cryptographic theories underpinning the implementation
    - Comprehensive documentation of our findings and insights

    This approach will help users grasp both the fundamental concepts and advanced features of Plonky3, providing a solid foundation for practical application and theoretical understanding.

-  **Technology Stack:**

    - **Programming Languages:** Rust
    - **Tools & Frameworks:** GitHub
    - **Documentation:** Markdown, LaTeX

-  **Design Mockups/Prototypes (Optional):**

    N/A
  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

    While there are limited tutorials and documentation available for Plonky3, our project differentiates itself by offering a deep dive into both the implementation aspects and the underlying theoretical principles. We aim to bridge the gap between theory and practice, providing a comprehensive analysis that caters to both developers and security researchers.



-  **Unique Contribution:**

    Our project combines implementation studies and theoretical analysis, providing a holistic approach to understanding Plonky3. This approach is particularly valuable for:

    - **Developers:** Beyond simply using Plonky3, developers need to understand the underlying theory to effectively implement and optimize zero-knowledge proof systems in their projects.

    - **Security Researchers and Auditors:** A deep understanding of Plonky3's internals and mathematical foundations is crucial for identifying potential vulnerabilities and ensuring the security of implementations.


    This project aims to draw more attention to the **foundational aspects of Plonky3**, enabling a deeper understanding of the underlying mechanisms. By doing so, we will lower the barrier to entry for both using and learning about Plonky3, encouraging broader participation beyond the current small group of experts. This expanded knowledge base will likely lead to more products confidently adopting Plonky3 in the future. Consequently, we believe this documentation effort will facilitate greater community involvement and contributions to Plonky3.

  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

    Xiaoxue Yang (<yxx@secbit.io>), Shaofan Wang (<sf@secbit.io>)

-  **Contact Information:**

-  **Name:** Shaofan Wang

-  **Email:** sf@secbit.io

  

-  **Prior Work/Research (Optional):**

    We are researchers from [SECBIT Labs](https://secbit.io/), which focuses on ZKP and security research. Our previous work can be found at [https://secbit.io/projects](https://secbit.io/projects).
    
    Our core team member, *Xiaoxue Yang*, has already conducted some initial in-depth studies and research on Plonky3. She has given online live sharing sessions on topics such as:
    
    - "ZKP系列课程｜Plonky3 FRI two_adic_pcs 概述" (ZKP Series Course | Overview of Plonky3 FRI two_adic_pcs)
      Available at: https://www.youtube.com/watch?v=swCjt9YibyE

    - "ZKP系列课程｜Plonky3 FRI 代码讲解" (ZKP Series Course | Explanation of Plonky3 FRI Code)
      Available at: https://www.youtube.com/watch?v=rUQK6j3Bhsk

    - Draft of the Plonky3 implementation diagram
      Available at: https://miro.com/app/board/uXjVNbLn8WU=/?share_link_id=56128048690

    
    These sessions demonstrate our team's existing expertise and commitment to understanding and explaining Plonky3's complex concepts.


    During our review of the Field module's source code in Plonky3, *Shaofan Wang* from our team identified an optimization opportunity in the inverse computation for 4th degree extension fields. He realized that using a conjugate-based method in this specific scenario could potentially be faster than the general Frobenius inverse approach. This observation led us to implement and test an alternative method, which indeed showed promising performance improvements in our benchmarks.

    **This example demonstrates the potential long-term benefits of our project.** By conducting in-depth analysis of the Plonky3 codebase, community members can identify opportunities for optimization that may not be immediately apparent. These improvements can lead to significant performance gains, enhancing the overall efficiency of Plonky3.

    Here's an example of the optimized code we developed:

    ```rust
    fn try_inverse(&self) -> Option<Self> {
            if self.is_zero() {
                return None;
            }

            match D {
                2 => Some(Self::from_base_slice(&qudratic_inv(&self.value, F::w()))),
                3 => Some(Self::from_base_slice(&cubic_inv(&self.value, F::w()))),
                4 => Some(Self::from_base_slice(&quartic_inv(&self.value, F::w()))),
                _ => Some(self.frobenius_inv()),
            }
        }

    fn quartic_inv<F: Field>(a: &[F], w: F) -> [F; 4] {
        let a0_square = a[0].square();
        let a1_square = a[1].square();
        let a2_square = a[2].square();
        let a3_square = a[3].square();

        let b0 = a0_square - w * (a[1] * (a[3] + a[3]) - a2_square);
        let b2 = a[0] * (a[2] + a[2]) - a1_square - w * (a3_square);

        let c = b0.square() - w * b2.square();
        let c_i = c.inverse();

        let b0 = b0 * c_i;
        let b2 = b2 * c_i;

        [
            a[0] * b0 - w * a[2] * b2,
            -a[1] * b0 + w * a[3] * b2,
            -a[0] * b2 + a[2] * b0,
            a[1] * b2 - a[3] * b0,
        ]
    }
    ```

    Our benchmark results showed a performance improvement of approximately 17.3% for the 4th degree extension field. However, further work is needed to verify the security and correctness of this optimization and to assess its impact on the overall system performance.


    
    ![Full Comparison](https://hackmd.io/_uploads/By-R_DI1kl.svg)


    ![Regression](https://hackmd.io/_uploads/rkJJKD8Jyg.svg)


## [Section 5] Development Roadmap :open_book:

### Scope

Recognizing that a comprehensive analysis of all Plonky3 modules would require significantly more than two months, we will focus on three fundamental and crucial components of Plonky3 for this grant: FRI-based PCS, finite fields, and mixed matrix commitment scheme.

-  **FRI-based PCS:** 
   - Module: fri
   - We will analyze the entire code in the fri module, primarily including:
       - two_adic_pcs, encompassing commit, open, and verify functions
       - fri prover, including commit_phase and answer_query
       - fri verifier
   - We will extract the process and principles of the protocol from the code. The key idea involves two steps of batching:
       - The first batching occurs in the PCS's open function, aimed at computing the batched quotient polynomials before feeding them to the FRI protocol. We refer to this process as "rolling horizontally," as illustrated below:
        ![horizontally](https://hackmd.io/_uploads/SkfL0uL1Jx.gif)

       - The second batching takes place in the FRI's commit_phase function. With each fold, we batch again, a process we call "rolling vertically," as shown below:
       ![vertically](https://hackmd.io/_uploads/HJqvWj8yye.gif)


   - We will analyze and visualize the pivotal optimizations in the code to enhance understanding, including:
       - The optimization in the open function for computing the batched quotient polynomial, along with potential optimization suggestions
       - The verifier's code corresponding to three-part checks: fold check, "rolling horizontally" check, and "rolling vertically" check
       - The application of MMCS
       - The reversed bit order 
       - Other relevant optimizations

-   **Finite fields:** 
    -   Modules: field, monty-31, baby-bear, koala-bear, mersenne-31, goldilocks
    -   Analyze the design of modules, including AbstractField, Field, PackedField, PrimeField, AbstractExtensionField, ExtensionField, HasFrobenius, BinomialExtensionField, BinomiallyExtendable, ComplexExtendable, Complex, and others
    -   Analyze key points and innovative algorithms, such as:
        -   Binomial extension
        -   Complex extendable and circle group
        -   Montgomery reduction and Barrett reduction
        -   Frobenius map and fast inversion
        -   The efficient reduction techniques in mersenne31 and goldilocks
        -   Other relevant algorithms

-   **Mixed matrix commitment scheme:** 
    -   Module: merkle_tree
    -   Analyze and visualize the logic of how a batch of matrices is committed as one Merkle tree

### Milestone 1 — FRI-based PCS Analysis

-  **Estimated Duration:** 1 month

-  **Description:** 
   - Complete the analysis of FRI-based PCS in Plonky3, delivering comprehensive documentation including:
       - Complete protocol process description extracted from code
       - Program flow chart
       - Detailed description document of complex functions

-  **FTE (Full-Time Equivalent):** 2.0 FTE

-  **Costs:** 5,000 USDC
   - **Personnel:** 5,000 USDC

### Milestone 2 — Finite Fields and Mixed Matrix Commitment Scheme Analysis

-  **Estimated Duration:** 1 month

-  **Description:** 
   
   - Complete the documentation of module plonky3/merkle-tree:
       - Description of traits
       - Description of functions and pivotal variants, including visual charts
       - Algorithm flow chart
   - Complete the documentation of module plonky3/field:
       - Description of traits in the field module and their relationships
       - Mathematical principles
       - Detailed description of complex algorithms
   - Complete the documentation of modules plonky3/monty-31, plonky3/baby-bear, plonky3/koala-bear
   - Complete the documentation of modules plonky3/mersenne-31, plonky3/goldilocks

-  **FTE:** 2.0 FTE

-  **Costs:** 5,000 USDC
   - **Personnel:** 5,000 USDC

### Total Costs: 5,000 + 5,000 = 10,000 USDC

## [Section 6] Extended Scope

  

-  **Future Plans:**

    Upon successful completion of the initial two-month phase, we aim to:

    1. Expand the project with more advanced topics
    2. Continuously update theoretical analyses and documentation
    3. Establish a collaborative platform for community contributions
    4. Develop workshops or webinars to engage the community and support ongoing education

    This project serves as a foundational step towards fostering a more knowledgeable and active Plonky3 community, encouraging long-term growth and innovation in both the practical and theoretical aspects of zero-knowledge proofs.

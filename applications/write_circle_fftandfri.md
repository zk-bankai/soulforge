
# Write Circle FFT&FRI with Plonky3
 

## [Section 1] Project Information

-  **Project Name:** Write Circle FFT&FRI with Plonky3

-  **Payment Details:** 0x850ff718187c15607B939A3fcf11db2B4A0Cc858 (on Polygon Network).

-  **Total Amount Requested:** 3,500 USDC

## [Section 2] Project Overview :page_facing_up:

-  **Brief Description:**

This project is to put out some blog articles about tutorials that **readers can write Circle FFT and Circle FRI codes using Plonky3 components.** This project combines **hand-calculations and coding tutorials with plonky3 to help readers bridge mathematical concepts with practical code implementations.**

-  **Core Idea:**

In total, I'll publish four articles about: 
- (1) Plonky3 Circle STARK implementation, 
- (2) Implementing Circle domain, 
- (3) Implementing Circle FFT,
- (4) Implementing Circle FRI. 

The reading time for them will be around 20 minutes each.

(1)Plonky3 Circle STARK implementation will be a brief description of the existing code. This will be a Learning Notes article as I study Plonky3's Circle folder and its components.

(2)(3)(4)Implementing Circle domain, Circle FFT, and Circle FRI, For now, I am planning to implement the Mersenne 5 trait and use it to implement Circle FFT, FRI with Plonky3. I would like to provide the hand calculations process  with the Mersenne 5 as well, so that the output of the code matches the hand calculations, which would make it easier to understand.
My primary goal is to use the Plonky3 library for this project. However, if technical constraints or time limitations arise, I will develop an original implementation from scratch while ensuring it aligns closely with Plonky3’s structure and concepts. 

My goal is to have over 100 people read each article within a few weeks of publishing, and for 40 people to view the Plonky3 Circle STARK code or engage with tutorials for my own implementation of the Circle STARK code, achieving over 20 stars on GitHub.

- **Target reader**
    - Developers and people who have basic knowledge of traditional STARK and FFT and want practical knowledge of Circle Group operations and how Circle FFT&FRI works.
    - Those interested in gaining knowledge of Plonky3's internal code.
    
-  **Technology Stack:**
    - [Plonky3](https://github.com/Plonky3/Plonky3)
    - [Circle STARKs paper](https://eprint.iacr.org/2024/278.pdf)
    - Rust


## [Section 3] Ecosystem Fit

-  **Similar Projects:**
    - [Deep dive into Circle-STARKs FFT](https://ihagopian.com/posts/deep-dive-into-circle-starks-fft)
    - [Yet another circle STARK tutorial](https://research.chainsafe.io/blog/circle-starks)
    - [Exploring circle STARKs](https://vitalik.eth.limo/general/2024/07/23/circlestarks.html)
    - [Antalpha Labs's Circle STARK lectures](https://www.youtube.com/@Antalpha_Labs/videos)
    - [An introduction to circle STARKs](https://blog.lambdaclass.com/an-introduction-to-circle-starks/)
    - [STARK by Hand](https://dev.risczero.com/proof-system/stark-by-hand#lesson-9-the-deep-technique)
    - [Diving DEEP FRI in the STARK world: learning your daily moon math with a concrete example](https://blog.lambdaclass.com/diving-deep-fri/)

-  **Unique Contribution:**

There are some comprehensive intoro articles. But I don't think there is any learning material that details the logic of mathmatics and code for the Circle FFT&FRI or Plonky3.

**This project bridges that gap by offering step-by-step tutorials combining mathmatical hand caluculation and practical coding examples with plonky3, making it easier for developers to understand.**

## [Section 4] Team :busts_in_silhouette:

-  **Team Member:** 
Yugo Cabrio

-  **Contact Information:** 
yuu5infinity@gmail.com

-  **Prior Work/Research (Optional):**   
I wrote about [Nova folding and Cycle of Curve](https://github.com/privacy-scaling-explorations/nova-by-hand) through the PSE acceleration program. I have implemented Traditional FRI and Lookup in full scratch as a hobby.

## [Section 5] Development Roadmap :open_book:

### Milestone 1

-  **Estimated Duration:** 1 month

-  **Description:**

    I plan to enhance my knowledge of my Circle STARK and investigate the code in the Plonky3 library.

    - Week 1,2: 
        - Solidify the knowledge of Circle STARK as much as possible
        - Make examples for hand calculations (by using Python's code.)
        - Write personal learning notes.
    - Week 3,4: 
        - Analyze the Plonky3 Circle folder and dependent codes.
        - Write an article that demystifies the Plonky3 Circle STARK implementation.
        - Judge If I implement Circle STARK on the Plonky3 primitive component or build mostly from scratch.

    - Submission
        - Personal notes about Circle STARK.
        - Article about Plonky3 Circle STARK implementation.

-  **FTE (Full-Time Equivalent):** 0.7 FTE

-  **Costs:** 1,750 USDC (About 15 USD/hour)

### Milestone 2

-  **Estimated Duration:** 1 month

-  **Description:** 

    I plan to write code to reproduce the same example as the manual calculation using the Plonky3 library.
    
    - Week 1: Implement Circle Group and Domain and Write an article about it.
    - Week 2: Implement Circle FFT and Write an article about it.
    - Week 3: Implement Circle FRI and Write an article about it.
    - Week 4: Complete everything. Publish articles.
    - I'll publish them in my blog.

- Submission
    - Three articles for Circle Group, Circle FFT, Circle FRI.
    - Implementation codes.

-  **FTE:** 0.7

-  **Costs:** 1,750 USDC (About 15 USD/hour)

### Total Costs: 1,750 + 1,750 = 3,500 USDC

## [Section 6] Extended Scope
- I would like to write articles in my native language version, and talk about them at community events.
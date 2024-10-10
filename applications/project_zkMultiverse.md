# ZK Multiverse: Soulforge Grant Application

## Project Information

**Project Name:** ZK Multiverse

**Tagline:** Demystifying Zero-Knowledge Proofs through Interactive Learning

**Payment Details:** matic:0x08145FbBc669B49688d83cF5E1D24D99DF15F884

**Total Amount Requested:** 10,000 USDC

## Project Overview 📄

### Brief Description

ZK Multiverse is an innovative, gamified platform designed to make learning about zero-knowledge proofs (ZKPs) accessible and engaging. Our interactive environment allows developers of all skill levels to explore, practice, and master ZKP concepts through hands-on puzzles and circuit development using Circom and Plonky3. By bridging the gap between theory and practice, ZK Multiverse aims to accelerate adoption and innovation in the ZKP ecosystem.

![Captura de pantalla 2024-10-09 a la(s) 11.39.21 p. m.](https://hackmd.io/_uploads/SkesOkr1Jl.png)


### Core Idea

ZK Multiverse democratizes ZKP learning through:

1. **Interactive Challenges:** Users progress through levels, solving increasingly complex ZKP puzzles and building circuits.
2. **Gamification:** A point system, achievement badges, and leaderboards to motivate continued learning.
3. **Adaptive Learning:** Challenges tailored to user skill levels, from beginner to advanced.
4. **Community Engagement:** Forums for discussion and user-generated content to foster a collaborative learning environment.

### Technology Stack

- **Frontend:** Next.js - Chosen for its performance and SEO benefits
- **Starknet** For onchain data.
- **Authentication:** Web3 Wallet
- **ZK Circuits:** Circom and Plonky3 - Core technologies for challenge implementation

This stack was chosen for its scalability, performance, and alignment with modern web development practices. It allows for easy integration of additional features and supports our future plans for expansion.

## Ecosystem Fit

ZK Multiverse uniquely contributes to the Plonky3 and Circom ecosystems by:

1. **Bridging the Learning Gap:** While existing resources focus on theoretical aspects, ZK Multiverse provides a practical, hands-on approach to learning ZKPs.
2. **Technology Comparison:** By implementing challenges in both Circom and Plonky3, users can directly compare these tools, understanding their strengths and use cases.
3. **Lowering Entry Barriers:** Our gamified approach makes ZKPs more approachable, potentially expanding the developer base for these technologies.
4. **Fostering Innovation:** As users become more proficient, they're encouraged to create their own challenges, potentially leading to novel applications of ZKPs.

We plan to collaborate with the Circom and Plonky3 development teams to ensure our content aligns with the latest updates and best practices. Additionally, we aim to integrate real-world ZKP projects as advanced challenges, providing practical application scenarios.

## Team 👥

### Team Members

1. **Alfredo Bonilla** - Full Stack Developer & ZKP Enthusiast
   - 13+ years of experience in web development
   - Completed PSE Core Program on ZK Technology
   - GitHub: [github.com/brolag](https://github.com/brolag)
   - Role: Lead Developer, responsible for overall architecture and Circom implementations

2. **Mairen Chavarría** - Backend Specialist & ZKP Enthusiast
   - 10+ years of experience in backend development
   - Completed PSE Core Program on ZK Technology
   - GitHub: [github.com/maicvcr](https://github.com/maicvcr)
   - Role: ZKP Engineer, focusing on Plonky3 implementations and Circom challenge design

### Contact Information

- Name: Alfredo Bonilla
- Email: info@alfredobonilla.com

## Development Roadmap 📖

### Milestone 1: Foundation and Basic Challenges

**Estimated Duration:** 1 month
**FTE:** 2 team members working part-time (50% each), equivalent to 1 FTE
**Costs:** 4,000 USDC

**Description:**

1. Set up project infrastructure (2 week)
   - Adjust Next.js frontend and Node.js backend
   - Setup integration with Starknet
   - Implement user authentication system

2. Develop basic game mechanics (2 week)
   - Implement point system and user progress tracking
   - Create leaderboard functionality
   - Design and implement user interface for challenge navigation

**Deliverables:**
- Functional game platform with user authentication
- Three implemented beginner challenges with solution verification
- Leaderboard system
- Basic user guide and documentation


### Milestone 2: Advanced Challenges and Platform Enhancement

**Estimated Duration:** 1 month
**FTE:** 1 person working full-time (100%) and 1 person working part-time (50%), equivalent to 1.5 FTE
**Costs:** 6,000 USDC

**Description:**


-  **Add simpler Circom challenges with Plonky3**: To facilitate gradual learning, more basic Circom challenges will be introduced, allowing users to progressively improve their skills. Existing challenges will also be refined for a smoother learning curve.

-  **List of simpler challenges**:

- Simple Addition Circuit: Create a Circom circuit that takes two inputs and outputs their sum.
- Multiplication Circuit: Create a circuit that multiplies two numbers together.
- Multiplication Circuit: Create a circuit that multiplies three numbers together.
- Equality Check Circuit: Build a circuit that checks whether two given numbers are equal.
- Less Than Circuit: Implement a circuit that determines if one number is less than another.
- Bitwise AND Circuit: Write a circuit that performs a bitwise AND operation on two binary numbers.
- Bitwise OR Circuit: Create a circuit that performs a bitwise OR operation on two binary numbers.
- Parity Check Circuit: Create a circuit that checks if a binary number has an even or odd number of 1s.
- Poseidon Hash Circuit: Create a circuit that takes an input value and outputs its Poseidon hash using the Poseidon hash function.
- Double Input Poseidon Hash Circuit: Create a circuit that takes two input values and outputs their combined Poseidon hash using the Poseidon hash function.
- Array Input Poseidon Hash Circuit: Create a circuit that takes an array of five input values and outputs their combined Poseidon hash using the Poseidon hash function.
- Hash Preimage Circuit: Given a hash, create a circuit that verifies if an input is the preimage of that hash using a simple hash function like Poseidon.
- Array Sum Circuit: Construct a circuit that takes an array of numbers as input and outputs the sum.
- Password Matching Circuit: Create a circuit that verifies if an input password matches a stored hash of a password.
- Simple Voting Circuit: Build a circuit where users can cast a vote, and the circuit verifies that the vote is valid and tallies the votes.

-  **FTE (Full-Time Equivalent):** 1 person working full-time (100%) and 1 person working part-time (50%), equivalent to 1.5 FTE.

## Total Costs: 4,000 + 6,000 = 10,000 USDC

## Extended Scope

-  **Future Plans:** 

   In the future, we plan to add more challenges not only for Circom but also for other circuit-specific languages. Additionally, we aim to include a quiz section where users can earn bonus points for extra challenges.  
   We will also adjust the design of the website to make it more interactive and engaging for users.
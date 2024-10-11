# [zk-Assets]

## [Section 1] Project Information

- **Project Name:** zk-Assets

- **Payment Details:** 0x7AAe4f27F2e724e471a8e4ABcBfB62c2D015b906

- **Total Amount Requested:** 9,000 USDC

## [Section 2] Project Overview

- **Brief Description:**

  With the development of blockchain, more and more people choose to hold crypto assets, and cryptocurrencies are gradually becoming an important part of many people's asset portfolios. In reality, if a person wants to travel or study abroad, they often need to provide the visa officer with proof of assets that meet certain requirements. Currently, mainstream asset proof methods still focus on traditional financial assets, such as bank statements. However, converting between crypto assets and traditional fiat currency presents certain obstacles, especially for countries with foreign exchange controls, making asset conversion more difficult. Many crypto asset holders are unwilling to convert their crypto assets into fiat assets just for the sake of asset proof.

  Currently, most solutions on the market are designed for exchanges to provide proof of crypto assets, and there is no solution targeted at individual users. Therefore, we hope to implement a crypto asset proof project aimed at individual users.

- **Core Idea:**

  This project aims to provide a solution for individual crypto asset proof, using Plonky3 as the proof system and exploring the combination of WebGPU and Plonky3 to accelerate proof generation on user terminals.

  Unlike exchange asset proofs, individual user asset proofs are only needed in certain specific scenarios, with low query frequency. Therefore, we choose to complete proof generation and verification entirely on the user terminal, without deploying it on-chain. This method effectively reduces the gas costs required for on-chain verification, lowering the overall solution cost.

  In the proof generation phase, the project currently only supports the Ethereum mainnet and its L2 extensions, without involving other blockchain networks. This phase only involves proof for a single account address, so there is no need to construct a Merkle tree, only generating a commitment for a single leaf node. In the future, a Merkle tree and aggregated proof will be introduced when supporting multiple chains.

  **Detailed Solution Design**:

  **Proof Generation Phase:**

  1. **Asset Query and Signing Process**:
     The user connects their wallet and inputs the account address and asset amount that need to be proved on the webpage. The webpage sends a query request to the server of the website constructed for this project via JavaScript, submitting the address information. The server uses the public OKX API to obtain the total asset valuation of the address and digitally signs the query result, returning the signature and the specific total valuation to the user. The communication between the server and OKX API uses HTTPS to ensure data transmission security.

  2. **Verify User's Asset Valuation**:
     When the front end receives the total valuation information, it determines whether the asset amount the user wants to prove is less than the total valuation. If the condition is met, the program continues; otherwise, proof generation fails.

  3. **Generate Account Ownership Proof**:
     The user calls the wallet API to generate a signature for the address to be proved and inputs the address and signature as private inputs into the zk digital signature verification circuit to generate an account ownership proof. In this step, the address and signature are private inputs to protect user privacy and ensure that the user's control of the address is not publicly disclosed.

  4. **Verify the Reasonableness of Total Valuation Information**:
     The front end takes the asset amount the user wants to prove and the server's public key as public inputs, which are transparent to the verifier for public verification. The server's digital signature and total valuation are used as private inputs, and the zk digital signature verification circuit verifies the reasonableness of the total valuation information and whether the total valuation is greater than the asset amount the user wants to prove.

  5. **Generate Commitment and Save**:
     The user generates the commitment (calculated as `hash[hash(address) || assets]`) and deploys the proof on-chain. The purpose of using `hash[hash(address) || assets]` is to ensure the uniqueness and integrity of the asset proof. By double hashing the address and asset information (i.e., hashing the address first, then concatenating the result with the asset information and hashing again), the original information is prevented from leaking, and the generated commitment is unique and non-forgeable.

     To save on-chain storage gas costs, only the commitment and a link to the IPFS network are stored on-chain, while the actual proof is stored on IPFS. The webpage reminds the user to save the previously generated commitment (data format `[[hash(address), assets]]`), for example, by generating a QR code for the user to screenshot and save.

  **Verification Phase:**

  1. **Submit Commitment for Verification**:
     The verifier (e.g., visa officer's personal computer) requires the user to submit the commitment. After the user shows the QR code, the webpage JavaScript automatically parses the QR code to extract the commitment, obtains the specific value of the assets, and then calculates the actual commitment stored on-chain based on `hash[hash(address) || assets]`. This ensures that the information submitted by the user is consistent with the data stored on-chain.

  2. **On-Chain Verification and Proof Download**:
     Find the corresponding commitment and proof on-chain, and the verifier downloads the proof and performs verification on their terminal. The content addressing of IPFS ensures that the downloaded proof has not been tampered with. Once verification is passed, it indicates that the user's crypto assets meet the requirements.

- **Technology Stack:**

  - **Website Design**: Built using Next.js, React, and TypeScript for creating an interactive website UI, with the entire website hosted on Vercel for continuous integration and deployment.

  - **Calculation Acceleration**: Uses the wgpu framework, WGSL, and WebAssembly to improve proof generation speed on the browser side.

  - **Smart Contract**: Smart contracts are written in Solidity.

  - **zk Proof System**: Plonky3 is used as the proof system.

## [Section 3] Ecosystem Fit

- **Similar Projects:**

  Currently, there are projects that provide asset proof solutions for exchanges, but no solutions are available for individual users' crypto asset proof.

- **Unique Contribution:**

  1. Explore the application of Plonky3 on user terminal devices.

  2. Explore the combination of Plonky3 and WebGPU to perform parallel computation on user terminal devices.

## [Section 4] Team :busts_in_silhouette:

- **Team Members:**

  - Fanka

- **Contact Information:**

  - **Name:** Fanka

  - **Email:** [einstellungsu@gmail.com](mailto:einstellungsu@gmail.com)

- **Prior Work/Research (Optional):**

  Fanka: Won third place in the Web3 URL Hackathon organized by Eth Storage and has shared insights on [CairoVM design](https://www.youtube.com/watch?v=mfuHY45pVQs&t=3154s&ab_channel=DappLearning) and [lambdaclass zk-STARK design](https://www.youtube.com/watch?v=wEIiSuaMH4o&ab_channel=AntalphaLabs) within the community, with in-depth knowledge of zk proof system design.

## [Section 5] Development Roadmap :open_book:

### Milestone 1 — Basic Functionality

- **Estimated Duration:** 1 month

- **Description:** Implement the MVP functionality of zk-Assets, including:

  1. Development of Ethereum digital signature verification circuit

  2. Development of server-side message digital signature verification circuit

  3. zk-Assets website development

  4. Smart contract writing

- **FTE (Full-Time Equivalent):** 1 FTE

- **Costs:** 5,000 USDC

  - Development labor: 5,000 USDC

### Milestone 2 — Additional Features

- **Estimated Duration:** 1 month

- **Description:** Optimize interactions and fix bugs for zk-Assets, and attempt to integrate Plonky3 with WebGPU to improve computational efficiency for proof generation:

  1. Integration testing

  2. WebGPU parallel computation optimization for FFT calculations

  3. WebGPU parallel computation optimization for hash calculations

  4. Write benchmarks and documentation, deploy online

- **FTE:** 1 FTE

- **Costs:** 4,000 USDC

  - Development labor: 4,000 USDC

### Total Costs: 9,000 USDC

## [Section 6] Extended Scope

- **Future Plans:**

  In the future, we plan to support asset proofs for Bitcoin and Solana networks. When supporting multiple chains, we plan to introduce a Merkle tree to construct commitments for multiple addresses, thereby better managing the proofs of assets across different chains. Using zk aggregation proof technology, we will aggregate the signatures of Ethereum, Bitcoin, and Solana into one proof to reduce on-chain verification and data storage costs. This will involve the following aspects:

  1. **Signature Verification for Bitcoin and Solana Networks**: Both Bitcoin and Ethereum use the `ECDSA` signature algorithm, but there are differences in specific implementation and address generation logic, while Solana uses the `Ed25519` signature algorithm. Therefore, we need to write specialized zk circuits for each blockchain network to support different signature verification logic.

  2. **Aggregation of Multi-Chain Signature Verification**: Generate signatures for Ethereum, Bitcoin, and Solana respectively, and then aggregate these signatures through zk circuits so that only one verification is needed during the verification phase, reducing on-chain operations and gas fees.
     These extensions will make zk-Assets applicable to a wider range of crypto assets and cross-chain proof requirements.

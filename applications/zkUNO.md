
# zkUNO - UNO on chain

## [Section 1] Project Information
  

-  **Project Name:** zkUNO - UNO on chain powered by Plonky3

-  **Payment Details:** Provide your wallet address for USDC (on Polygon Network).

-  **Total Amount Requested:** 40000 USDC

  

## [Section 2] Project Overview :page_facing_up:

  

-  **Brief Description:**

zkUNO is an innovative blockchain-based adaptation of the popular UNO card game, leveraging zero-knowledge proofs to ensure privacy, fairness, and transparency in gameplay. It will be built on zkVM/zkEVM and  **Plonky3** will be used to write the game's proofing mechanisms, ensuring that sensitive information, like players' hands and the deck, remains confidential. 

The project excites us because it represents a significant leap forward in decentralized card gaming, providing a fair, tamper-proof, and privacy-preserving experience. Our **objective with this grant is to rewrite the contract and implement the proving system using Plonky3**. This is an effort to fully realize zkUNO's potential as a **reference architecture** for privacy-focused decentralized card games, driving **broader adoption** of both the game and the underlying technology.

The goals we'd like to achieve by the end of the grant period are:

- Update the contract to implement criticial onchain functionality (e.g., card shuffling, dealing, and turn management)

- Write the proving and verifier system to generate zkps for player's hands and the deck

- A funky frontend to integrate the contract actions, proving and verifier system and websocket to create a multiplayer card game
  

-  **Core Idea:**

The primary goal of zkUNO is to create a fully decentralized and privacy-preserving version of the UNO card game on chain. The core innovation lies in zkUNO’s **hybrid architecture**, which integrates on-chain game logic with an advanced off-chain proving system. The game logic covering actions such as shuffling, dealing, and turn management will be implemented directly on-chain using Solidity, ensuring transparency and preventing tampering. The **privacy layer** is powered by **Plonky3**, a cutting-edge zero-knowledge proof system, which generates proofs that verify game actions, including the cryptographic shuffling of the deck, without revealing sensitive information like players' hands and the order of the deck.

Key components of this architecture include:

**On-chain Smart Contracts:** The core game mechanics will be implemented in Solidity

**Plonky3 Proving System:** This will be used off-chain to generate zero-knowledge proofs for game actions, including deck shuffling and hand validation, ensuring privacy.

**WebSockets for Real-time Synchronization:** This module will sync the game state across all clients while periodically committing updates to the blockchain.

**Optimistic UI:** This will aggregate player actions off-chain and commit them in batches to the blockchain, improving efficiency.

This approach ensures that no player can gain an unfair advantage, as the game state remains transparent and verifiable to all participants while keeping critical game data confidential. Excited to build this project because we and our social media followers believe that it will not only **showcase the potential of zero-knowledge proofs in real-world applications** but also aims to serve as a **reference architecture for future blockchain based card games**, driving broader adoption of the technology.


-  **Technology Stack:**

  Frontend: nextJS
  Backend: websockets
  Smart contract: Solidity
  Prover circuit: Plonky3
  L2 Chain: Polygon
  Transaction cache: Redis


-  **Design Mockups/Prototypes (Optional):**

The card game will be built in a hybrid architecture mode where the game logic will reside onchain while some of the validation / verification ops will happen off chain. The state management across clients will be through websockets and will be sync'd peridocally to the chain. 

Below are the high level blocks of the dapp:

**Smart Contract:** The entire game logic (shuffle, card dealing, turn management) will be handled by the smart contract.

**Game State Management:** Each player's turn, remaining cards, and game state transitions will be periodically synced with the chain.

**Privacy Layer:** Responsible for generating succinct proofs of hands and deck and associated cryptographic algorithms.

**State Reconstruction and Verification:** While the private elements are hidden, the state of the game remains verifiable by all players through cryptographic commitments, ensuring fairness without exposing sensitive information.

**Optimistic Client Rollup:** A queue, off chain, will keep record of all transactions and at a particular time or trasnaction cadence it will commit a transaction encompassing all the other ones.

**Backend Websockets:** Websocket layer running in the backend will be responsible for syncing the discard pile, hands and deck across clients.


**Below are the sequence diagrams of each module.**

**Game Play**

![zkUNO-gameplay-sequence](https://hackmd.io/_uploads/ryOoKLna0.png)

**Prover & Verifier**

![zkuno-proof-verify-sequence](https://hackmd.io/_uploads/rJSTK83pR.png)

**Backend websockets**

![zkuno-backend-websockets](https://hackmd.io/_uploads/rye1q8npR.png)

**Optimistic client rollup**

![zkuno-optimistic-client rollup](https://hackmd.io/_uploads/HyP8cU2pA.png)


  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

As of today, a game of UNO does not exist in web3. This is an effort to take the next big leap in card gaming. We have built a prototype (without zk proofs) already. In this grant we plan to re-write parts of the contract and build the proving and verifier system using ***plonky3***.
[zkUNO](https://gameofuno.vercel.app/) | [GitHub](https://github.com/ronykris/gameofuno) | [ X (Twitter)](https://x.com/zk_UNO) 
  

-  **Unique Contribution:**

zkUNO brings significant value to the **Plonky3** ecosystem by demonstrating the practical application of zero-knowledge proofs in a real-time, interactive gaming environment. Here’s how it contributes uniquely:

**Innovative Use Case:** zkUNO applies **Plonky3** in a novel context by utilizing zero-knowledge proofs to maintain the confidentiality of players’ hands and the deck while ensuring transparency and fairness of the game. This goes **beyond the typical financial or identity-based applications of zero-knowledge proofs**, showcasing their versatility in a gaming environment.

**Real-Time interaction with ZK-Proofs:** The project introduces a real-time, multiplayer game that relies on **Plonky3** to **generate and verify proofs on the fly**. This dynamic use of zero-knowledge proofs in an interactive setting **demonstrates the efficiency and scalability of Plonky3 for applications requiring quick proof generation and verification.**

**Reference Architecture for Future Projects:** zkUNO could serve as a **reference architecture** for developers looking to build privacy-preserving applications on Plonky3. By open-sourcing the project and providing detailed documentation, **it lowers the barrier to entry** for other developers and **encourages further innovation and adoption** within the ecosystem.

**Expanding the Use Cases for Plonky3 Beyond Finance:** The project extends the **use cases of Plonky3 beyond traditional financial applications**, demonstrating its potential in new domains like gaming. This diversification will help position Plonky3 as a versatile solution for various privacy-centric applications, thus broadening its appeal and utility.

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

Saurabh, Krishanu, Nikhil, Ayush

  

-  **Contact Information:**

-  **Name:** Krishanu 

-  **Email:** rony.kris@gmail.com

  

-  **Prior Work/Research (Optional):**

Share any relevant previous work or research that highlights your expertise.

**Krishanu:** 7 years of web3 developer experience across numerous chains. Experienced in writing proving systems & building distributed scalable solutions including zk circuits in zokrates, O1js and noir. Built zknonogram and zkpoker type of games on Aztec and a wallet on Aztec's Alpha Build cohort.
[GitHub](https://github.com/ronykris/)

**Ayush Kumar Singh:** A full stack developer with several wins and two years of experience in the web3 ecosystem. He has won Filecoin track prizes at ethIndia and worked in the Mina ecosystem. As a Core Member of the UniDAO program led by Devfolio, he fosters blockchain innovation on his campus by hosting weekly sessions on DeFi, DAOs, IPFS, NFTs, and hands- on projects.
[Devfolio](https://devfolio.co/@Ayush4345) | [GitHub](https://github.com/ayush4345)

**Nikhil Shrivas:** Ace designer and frontend developer with expertise in scaling protocols and managing product. He has 4+ years of web3 experience on chains with marketing and Content. He is an Abassador in **Arbitrum** and several crypto exchanges. 
[GitHub](https://github.com/nshri1609) | [Linkedin](https://www.linkedin.com/in/nikhilshrivass/)

**Saurabh Shetty:** Web3 and blockchain developer relations professional with 5+ years of experience. Skilled in developer outreach, technical writing, and community management, Director of TPG_Karnataka, Web3 Developer community, Mina Navigator Hackathon Winner.
[GitHub](https://github.com/Saurus9290) | [Linkedin](https://www.linkedin.com/in/saurabhshettyofficial/)

  

## [Section 5] Development Roadmap :open_book:
  
>  **Important:** The maximum project duration is 2 months. Outline milestones and timelines accordingly.

### Milestone 1 — Basic Functionality

-  **Estimated Duration:** 1 month

-  **Description:** Implement key infra pieces and begin frontend integration
                    * Smart contract with game play features
                    * Proving circuits and Verifier system
                    * Backend service to sync hands
                    * Frontend integration

-  **FTE (Full-Time Equivalent):** 2 FTE

-  **Costs:** 20k USD


### Milestone 2 — Additional Features

-  **Estimated Duration:** 1 month

-  **Description:** Implement backend services and frontend integration.
                    * Backend service to sync hands across clients
                    * Optimistic client rollup for transactions
                    * Frontend integration

-  **FTE:** 2 FTE

-  **Costs:** 20k USD

  
  ### Total Costs: 20K + 20k = 40k USD

## [Section 6] Extended Scope

  

-  **Future Plans:**

We could enjoy the first mover advantage with zkUNO and our social media presence is promising too [ X (Twitter)](https://x.com/zk_UNO). To super charge distribution we also have a telegram bot built [Telegram](https://t.me/zkcard_bot). Therefore, our goal is to take this app to the next level and be the pioneers of decentralised card gaming. Post the MVP we'd have to spend considerable time 
* testing and fixing bugs
* run benchmarks to ascertain performance (**Plonky3** should give us better results)
* a better user experience 
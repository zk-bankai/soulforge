# SilentBid - Bringing Sealed-Bid Auctions On-Chain

## [Section 1] Project Information

- **Project Name:** SilentBid - On-chain Sealed-Bid Highest Auction
- **Payment Details:** 0x9efE53369D4894Ca22C63f489023B324C3D519BA (Polygon Network)
- **Total Amount Requested:** 12,000 USDC

## [Section 2] Project Overview :page_facing_up:

### Brief Description

**SilentBid** is a [**Sealed-Bid Auction**](https://www.investopedia.com/terms/s/sealed-bid-auction.asp) platform built using the
**Plonky3** toolkit. The project aims to facilitate secure and private auctions by leveraging **zero-knowledge proofs (ZKPs)** to
determine the highest bidder without revealing individual bid amounts. This ensures both privacy and fairness in the bidding process.

Additionally, **SilentBid** serves as a **reference model** for developers interested in building decentralized applications (dApps)
using **Plonky3** and **ZKPs**.

### Core Idea

Bidders submit encrypted bids to a smart contract, which only the auction owner can decrypt using their secret key. At the conclusion
of the auction, the owner publishes the winner. **ZKPs** ensure that the auction owner reads all bids and selects the highest one
without revealing their private key or any bid details.

Key components of the project include:

- **Proving Service**: Powered by **Plonky3**, this service generates a **zero-knowledge proof** from the execution trace of a program
  that decrypts bids and computes the winner, while preserving the confidentiality of individual bid amounts and the owner's private
  key.
- **Smart Contract**: The smart contract verifies the ZK proof and manages the entire auction lifecycle, including setup, bidding, and
  settlement.

### Technology Stack

- **Smart Contract**: Solidity
- **Circuit**: Rust, Plonky3

### Design Mockups/Prototypes (Optional)

The core logic of **SilentBid** operates on-chain, while off-chain processes handle the winner calculation and proof generation. The
auction process follows four main phases:

1. **Initial Setup**: The auction owner creates the auction, sets the required deposit amount, transfers assets to the smart contract,
   and defines the auction's start and end times.
2. **Bid Phase**: Bidders submit their bids to the smart contract by depositing the required amount.
3. **Open Phase**: After the bidding window closes, the auction owner calculates the winner and generates a zero-knowledge proof.
4. **Verify Phase**: The owner submits the winner and the proof to the smart contract for verification, concluding the auction.

**Sequence diagrams for each module are shown below:**

#### Auction Flow:

![auction_flow](https://raw.githubusercontent.com/VanhGer/soulforge/refs/heads/vjp/auction_flow.png)

#### Prover & Verifier Flow:

![prover_verifier_flow](https://raw.githubusercontent.com/VanhGer/soulforge/refs/heads/vjp/prover_verifier_flow.png)

#### Circuit Pseudo Code:

```ts
function get_winner(
    witness: {
        owner_private_key: string
    },
    public_params: {
        encrypted_bids: EncryptedBid[]
    }
): { winner: address, input_hash: string } {

    // Decrypt all encrypted bids using the owner's private key
    const bids: Bid[] = public_params.encrypted_bids.map(enc_bid =>
        decrypt_bid(witness.owner_private_key, enc_bid)
    );

    // Find the winning bid based on auction criteria
    const winner_bid: Bid = find_max(bids);

    // Generate a hash of the input parameters for verification
    const input_hash: string = hash(public_params);

    // Return the winner's address and the input hash for verification
    return {
        winner: winner_bid.bidder,
        input_hash
    };
}

// Define the Bid type
type Bid = {
    bidder: address,
    amount: number
};
```

#### Smart Contract Pseudo Code

```solidity
// SPDX-License-Identifier: Apache-2.0.
pragma solidity ^0.8.20;

contract ZkAuction {
    struct Auction {
        address owner;
        bytes ownerPublicKey;
        Asset asset;
        Bid[] bids;
        Winner winner;
    }

    struct Bid {
        address bidder;
        bytes encryptedPrice;
    }

    struct Asset {
        string name;
    }

    struct Winner {
        address bidder;
        uint256 price;
    }

    mapping(uint256 => Auction) auctions;

    /**
     * @notice Creates a new auction with specific parameters.
     * @dev Initializes a new auction.
     */
    function createAuction(Auction memory auction) public {
        // Logic for creating an auction
    }

    /**
     * @notice Allows users to place bids.
     * @dev Bids are encrypted for ZK-based auctions.
     */
    function bid(uint256 auction, Bid memory bid) public {
        // Logic for placing a bid
    }

    /**
     * @notice Reveals the winner after the auction ends.
     * @dev Uses a ZK-proof to reveal the highest valid bid.
     */
    function revealWinner(uint256 auction, Winner memory winner, bytes32 inputHash, bytes memory proof) public {
        verifyProof(winner, inputHash, proof);
    }

    /**
     * @notice Auction winner claims the item.
     */
    function claim() public {
        // Logic for claiming the auction item
    }

    /**
     * @notice Verifies a zero-knowledge proof.
     */
    function verifyProof(Winner memory winner, bytes32 inputHash, bytes memory proof) private {
        // ZK-proof verification logic
    }
}
```

## [Section 3] Ecosystem Fit

### Similar Projects

Several research papers have explored sealed-bid auctions on the blockchain,
including [Anonymous Fair Auction on Blockchain](https://ieeexplore.ieee.org/document/9432664)
and [A Blockchain-Based Sealed-Bid e-Auction Scheme with Smart Contract and Zero-Knowledge Proof](https://www.researchgate.net/publication/351717293_A_Blockchain-Based_Sealed-Bid_e-Auction_Scheme_with_Smart_Contract_and_Zero-Knowledge_Proof).
However, these solutions often assume the verifier holds both a private and public key, which is impractical for smart contracts.
Projects like [AuctionContract](https://github.com/HSG88/AuctionContract) focus on developing business logic inside a smart contract
but do not provide a complete solution for secure and private auctions.

### Unique Contribution

**SilentBid** provides a **practical reference** for developers aiming to build **ZK-based dApps**, demonstrating how **Plonky3**can
address real-world problems.

## [Section 4] Team :busts_in_silhouette:

- **Team Members:** We are part of [SotaZK Labs](https://sotazk.org/), a team focused on pioneering zero-knowledge solutions to enhance
  security and privacy in the decentralized world.
- **Number of Members**: 7
- **Contact Information:**
    - **Name:** Steve Nguyen
    - **Email:** zk.steve.nguyen@gmail.com
    - **Telegram:** @zk_steve
- **Prior Work/Research (Optional):**
    - [ZKP Documentation](https://github.com/sota-zk-labs/zkp-documents): A repository dedicated to demystifying zero-knowledge proof
      technology, including KZG, GKR, FRI, Plonk, Groth16, lattice-based commitment schemes, sum-check protocol, Nova, EIP-4844, etc.
    - [ZKP Implementation](https://github.com/sota-zk-labs/zkp-implementation): Various ZKP protocols, including KZG, FRI, and Plonk.
    - [Apstark](https://github.com/sota-zk-labs/apstark): A layer 2 ZK rollup blockchain built on the Aptos network using the Starknet
      tech stack.

## [Section 5] Development Roadmap :open_book:

> **Important:** The maximum project duration is 2 months. Milestones and timelines are outlined accordingly.

### Milestone 1 — Basic Functionality

- **Estimated Duration:** 1 month
- **Description:** Implement the core functionalities, including the smart contract with auction and verification features, and the
  proving service on the client side.
- **FTE (Full-Time Equivalent):** 4 FTE
- **Costs:** 6,000 USDC

### Milestone 2 — Additional Features

- **Estimated Duration:** 1 month
- **Description:** Develop the front-end, refine the code, fix bugs, and create tutorials (documents and videos) for developers.
- **FTE:** 4 FTE
- **Costs:** 6,000 USDC

### Total Costs: 12,000 USDC

## [Section 6] Extended Scope

### Future Plans

Post-development, we plan to integrate additional auction types, such as **Unique Lowest Bid Auctions** and **Dutch Auctions**. We also
aim to collaborate with other **dApps**, potentially with **DeFi platforms**, to allow for automatic asset management following auction
outcomes.
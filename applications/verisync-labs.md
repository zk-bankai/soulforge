
# VeriSync Labs
  

## Project Information

  

-  **Project Name:** VeriSync Labs

-  **Payment Details:** 0x84F58F6dd7E84c9864A2f37D73ADeBe71613fd83

-  **Total Amount Requested:** 15000 USDC

  

## Project Overview :page_facing_up:

  

-  **Brief Description:**

At VeriSync Labs, we are tackling the challenge of making AI models verifiable and trustworthy. Our solution uses Zero-Knowledge Machine Learning (ZKML) to ensure that both models and their predictions are provably accurate without compromising privacy, providing a robust verifiability layer for AI infrastructure.

-  **Core Idea:**

We are currently building Verisync Prover SDK which aims to abstract ZK complexities from ML devs, making it easy to onboard ML devs to ZKML. Previously we have built our SDK for Starky and Plonky2, but we would like to experiment with Plonky3 which can increase the performance of our SDK.The prover SDK is designed to act as a plug and play tool. ML engineers have to know very little about ZK and make minimal changes to their model to make it verifyable. The prover SDK takes the ONNX model along with the input and output to be proved. Based on the architecture of the models we have provided  ZKML solutions which utilizes combination of proving schemes.

![image](https://github.com/user-attachments/assets/94b722e4-d31d-45c2-8297-732022759cb8)
  
Any inference from a conventional ML model can be proven using our SDK. However doing so needs quantization of inputs to the prover.
The transpiler module is used to quantize the weights and biases to be made compatible with the prover inputs. These quantized weights and biases are then used inside the ZKML circuits to prove the inference. Once the model is quantized with the transpiler module you can directly call the Prover SDK in python itself. You need to pass in your quantized weights, biases, inputs, and inferred output as arguments. And then you can make a function call and get the generated proof with a set of public inputs.

These models are  divided into multiple layers and then we generate proofs for each of these layers. Later, these proofs are batched together in a Merkle tree structure which helps us to achieve a single proof for the whole computation. To improve efficiency, we have implemented parallel computing for the prover. Each layer's proof is computed in parallel, significantly reducing the overall proof generation time.
In future releases, we aim to include GPU optimizations within our ZKML circuits, which will further enhance our parallel computing environments.

-  **Technology Stack:**

We are already using Starky and Plonly2 for our prover SDK and through this program we would like to integrate Plonky3 into our SDK increasing overall performance of the SDK with the new toolkit.

-  **Design Mockups/Prototypes (Optional):**

Here's a prototype to prove a dense layer in deep learning using Plonky3.
https://gist.github.com/armanthepythonguy/aba9de42886341c1129a4091a90bb50f
  

## Ecosystem Fit

  

-  **Similar Projects:**

A few projects working on ZKML are EZKL and Orion(GizaTech).
EZKL uses Halo2 and Orion uses Cairo (Starkware) to build their proofs, but with our prover SDK, we have been able to prove ZKML much faster than our competition. Even with our Plonky version we were able to get the following :- 
  These benchmarks were tested on different machines. The EZKL test were done on a standard Google Collab notebook (Intel Xeon CPU with 2 vCPUs (virtual CPUs) and 13GB of RAM), VeriSync’s SDK were tested on a M1 Macbook Air with 8GB RAM, while Orion was tested on Orion’s deployed server with the maximum specs(XL version).
  
Linear Regression

EZKL :- 120ms
VeriSync SDK :- 130ms
Orion :- 830ms

Deep Learning Model (Three Layers: (4x20), (20x20), (20x3))
EZKL :- 7sec
VeriSync SDK :- 2.5sec
Orion :- >30sec

-  **Unique Contribution:**

VeriSync Labs is the first team building core ZKML projects in the Plonky2 and Plonly3 ecosystem, and with the great advancements happening in the toolkit, we are aiming to bring ZKML to mainstream ML devs very soon. With the new hashing functions and hardware optimizations getting introduced with Plonky3 we are achieving the best benchmarks ever recorded for ZKML prover SDKs.

## Team :busts_in_silhouette:

  

-  **Team Members:**

Arman Aurobindo, Shreyas Padmakiran, Sudeep Kamat

  

-  **Contact Information:**

-  **Name:** Arman Aurobindo

-  **Email:** armanityours@gmail.com

  

-  **Prior Work/Research (Optional):**

**Arman Aurobindo**
 - Currently working on VeriSync SDK
 - Previously worked with Lucidity Finance, Hyperlane India
 - Some of the hackathons project built around Plonky2
   - https://github.com/armanthepythonguy/ZKMLVaultX-ETHSingapore
   - https://github.com/armanthepythonguy/zkAuthX-ETHOnline2024
  
**Shreyas Padmakiran**
 - Currently working as devrel @ Nil Foundation
 - Previously worked with ChaiDex, Hyperlane India
 - Previous StarkNet grantee

**Sudeep Kamat**
 - Currently working as devrel @ Inco
 - Previously worked with ChaiDex, Hyperlane India
 - Previous StarkNet grantee

## Development Roadmap :open_book:
  

### Milestone 1 — Developing basic ML models and Deep Learning layers

  

-  **Estimated Duration:** 1 month

-  **Description:** We are planning to build the basic ML models along with some deep learning layers for the prover SDK.
-  Planned ML models:- Linear Regression, Logistic Regression, SVM, Decision Tree Classifier, Random Forest Classifier, XGBoost
-  Planned Deep learning layers:- Dense, Dropout, Flatten, CNN

-  **Costs:** 7500 USDC
-   We are planning to use these funds to develop the above-mentioned circuits for the Prover SDK. We will need some high CPU and memory resources to develop this SDK, so we are planning to host our remote servers with AWS or GCP. Moreover, we will also use some funds to make a small alpha release to private group of devs to try out the SDK.
  

### Milestone 2 — Additional Features

  

-  **Estimated Duration:** 1 month

-  **Description:** In this milestone, we will be planning to build some more complex ML models for our SDK, we will be mostly building ensemble circuits for our ML SDK. And for our deep learning SDK, will be building circuits for LSTM, GRU, Embedding, etc.

-  **Costs:** 7500 USDC
  
  ### Total Costs: 15000 USDC

## Extended Scope

  

-  **Future Plans:**

The end goal of our project is to make AI verifiable. We have been exploring a lot around new innovations in ZKML. Recently we have got Polygon's Community Grants to release the first POC of our project. Moreover we are also looking into fields like teeML and ZKML on Miden VM etc.

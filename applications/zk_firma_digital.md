
# ZK Firma Digital

## [Section 1] Project Information

-  **Project Name:** ZK Firma Digital

-  **Payment Details:** 0x86E67a05324A55AF6B2b3bF1A5cBA1778C56A8bE (on Polygon Network). 

-  **Total Amount Requested:** 11,200 USD

## [Section 2] Project Overview :page_facing_up:

-  **Brief Description:**

  The project aims to develop a zero-knowledge proof infrastructure solution for enhancing Costa Rica's digital identity system. Our goal is to strengthen citizen privacy by minimizing data collection, enabling individuals to access a wide range of valuable services without disclosing sensitive information. For this we plan to use Circom and the Polygon Blockchain network.

  We already have developed an initial Proof-of-concept you can find here: [zk-firma-digital](https://github.com/kuronosec/zk-firma-digital) . The project is Open Source under the Apache-2.0 license. As a next step for our project, and proposal for this grant, we want to show the capabilities of our approach by allowing Costa Rican citizens to participate in voting proposals in an anonymous way while keeping the ability to authenticate their identities and therefore proving that they are enabled to vote, all by using blockchain technologies.

-  **Core Idea:**

  The Costa Rican government offers an advanced digital identity system (Firma Digital) that allows residents or entities to sign documents with a digital identity validated by the central bank as CA and authenticate themselves on various public or private websites and services. However, there is a significant privacy concern related to sensitive data in Costa Rica. A small amount of identity information, such as a national ID number or car plate number, can lead to extensive data collection. Private companies can use this kind of data to harvest citizen data, for instance, by calling and offering them products or services without any previous request or permission. This fact is exceptionally relevant now that big corporations harvest indiscriminate user data to train AI models. Even worse, criminals are collecting this same data to perform identity theft and fraud, sometimes even making fraudulent calls from the jails.

  Our project aims to address these privacy issues by developing a zero-knowledge proof infrastructure using Polygon blockchain technology and ZK Circom circuits. This solution will enable citizens to verify their identity and provide specific information without revealing actual personal details. By minimizing the distribution of sensitive data across various institutions and companies, we can significantly reduce the risk of data theft. Additionally, this system can authenticate users for diverse services, ensuring they are real individuals and not bots, without requiring sensitive information such as email addresses or phone numbers.

**Core Components and Architecture:**

- **Data Extraction and Validation (PoC available)**:
  - **Libraries and Applications**: Develop libraries in Javascript and Python to extract data from the Firma Digital certificate and validate signatures issued by the Certification Authority (CA).

  - **Certificate Validation:** Ensure that the certificate information and signature are authentic and belong to a Costa Rican resident and citizen.

- **Zero-Knowledge Proof Generation (PoC available)**:
  - **Data Extraction for ZK Proofs**: Extract necessary information from Firma Digital certificates to generate zero-knowledge proofs for identity.
  - **Off-Chain Management**: Manage identity validation off-chain (via web interfaces).

- **User Interfaces (To improve)**:
  - **Graphical Interfaces**: Develop intuitive graphical interfaces for users and administrators to interact with the system seamlessly.
- **Allow users to anonymously participate in voting proposals (TODO)**.
- **Integration with Polygon Blockchain (TODO)**.

**Technology Stack:** The project will employ a diverse and robust technology stack to achieve its objectives. Key technologies include:
  - **Javascript**: For developing front-end interfaces and certain back-end functionalities.
  - **Python**: For data extraction, validation, and interaction with the Firma Digital certificate system.
  - **Circom (ZK Proofs)**: To enable privacy-preserving identity verification and voting.
  - **Firma Digital**: Costa Rica’s digital identity infrastructure, providing the basis for identity verification.
  - **Polygon Blockchain**: To ensure secure, decentralized handling of identity and voting data.
  - **Solidity**: For creating smart contracts to manage identity validation and voting proposals on the Polygon blockchain. 

**Design Mockups/Prototypes:**

[authentication.png](https://github.com/kuronosec/zk-firma-digital/blob/main/images/authentication.png).

[signature.png](https://github.com/kuronosec/zk-firma-digital/blob/main/images/signature.png).

## [Section 3] Ecosystem Fit

**Projects from which we have taken inspiration:**

- **Circom**: A compiler allowing developers to create ZK circuits with its programming language intuitively.
- **Anon Aadhaar**: The Anon Aadhaar libraries, a project built for the Indian citizen Identity using the Circom utilities, share common goals and specifications with our current project. As the website describes, "Anon Aadhaar is a protocol for proving ownership of an Aadhaar identity (Indian Residence ID) in a privacy-preserving manner. It lets users generate a ZK proof of their identity by only revealing the information they want to share (to an application)." This definition aligns perfectly with our commitment to privacy and security, making it an ideal foundation for our proposed project.
- **Constancias Municipales**: A project where Andres advised on integrating Costa Rican digital identity with blockchain for issuing signed tax certifications, demonstrating expertise in similar initiatives.
- **Polygon ID Verifier**: An infrastructure we have set up based on Polygon ID to authenticate users with digital credentials while maintaining privacy, utilizing zero-knowledge proofs to reveal only necessary information [polygon-id-verifier](https://github.com/edenia/polygon-id-verifier).

**Mention any similar projects, How is the idea of this project different or better?**

We were inspired both by Anon Aadhaar and ZK Passport to create our ZK Firma Digital project. However, those projects only allow users to validate government digital signatures by QR codes and X509 certificates, while ours allow users to use their ID smart cards to also sign arbitrary data. This makes our approach even more powerful and flexible allowing different people and entities to create their own type of authenticated data taking advantage of already built PKI infrastructures. It can be extended to other countries with similar technologies other than Costa Rica.

There is still no system like this in the Circom ecosystem. In addition, we want to provide an integration for Verifiable Credentials and Decentralized Identities using existing PKI infrastructure, while taking advantage of the ZKP capabilities to keep sensitive information private.
## [Section 4] Team :busts_in_silhouette: 

-  **Team Members:**

Andres Gomez Ramirez, Francis Adrian Gomez Ramirez
 
-  **Contact Information:**

-  **Name:** Andres Gomez Ramirez.

-  **Email:** andres.gomez@sakundi.io.
 

-  **Prior Work/Research:**

**Dr. Andres Gomez Ramirez** - [Linkedin](https://www.linkedin.com/in/andres-gomez-ramirez-bb7226156/) Ph.D. in cybersecurity from the University of Frankfurt and CERN. PhD thesis: Deep Learning and Isolation-Based Security for Intrusion Detection and Prevention in Grid Computing: [Thesis](https://cds.cern.ch/record/2686424/files/CERN-THESIS-2018-441.pdf)

**Francis Adrian Gomez Ramirez** - [Linkedin](https://www.linkedin.com/in/francis-adrian-gomez-ramirez-599598138/) Specialist in project management and computer scientist.

Our team possesses a rich portfolio of diverse projects, showcasing our extensive expertise across multiple domains. Andres has made significant contributions to the Tails project, the Linux-based OS that enabled Snowden to reveal NSA spying capabilities. As a developer and security researcher for Tails, Andres contributed to advancing privacy protection, which remains a core passion and area of expertise for our team.
Our capability to undertake substantial projects is further underscored by securing an academic scientific research grant from the Ethereum Foundation, amounting to $102,000 USD. This grant facilitated the creation of Tikuna, an AI-driven security monitoring system designed for the Ethereum P2P network. This has been the only grant for scientific research provided by EF to a team in Latin America. Additionally, our active participation in the Forta network bounty demonstrates our commitment to enhancing blockchain security, by leveraging AI algorithms, we detect malicious smart contracts across Ethereum and other Layer 2 networks.
We also participate in the Nym network, focusing on user privacy through mixnets. Operating a Nym mixnode and establishing Costa Rica's only gateway, we have become key players in Latin America. We further contributed by developing a monitoring system for Nym mixnodes, enhancing the project's infrastructure. Our extensive experience and proven track record underscore our capability to successfully deliver this project.
This diverse experience, ranging from privacy-focused operating systems to AI-driven security systems and blockchain privacy initiatives, underscores our team's comprehensive expertise and unwavering commitment to advancing security and privacy technologies. 

## [Section 5] Development Roadmap :open_book:

### Milestone 1 — Allow users to participate in voting proposals 

**Estimated Duration:** 4 weeks

-  **Description:**
  - **Verifiable Credential Signature**: Enable users to sign voting data formatted as VC (JSON).
  - **Signature Validation**: Validate the signed voting data and citizen’s signature to confirm authenticity and eligibility.
  - **Circom vote privacy**: add circuits to validate the user ability to emit votes in a proposal and then allow them to vote in an anonymous way.

**FTE (Full-Time Equivalent):** 1 FTE.

**Costs:** 5,600 USD
 
These costs include 40 hours of work per week x 4 weeks x 35 USD per hour = 5,600 USD

### Milestone 2 — Integration with Polygon Blockchain 

**Estimated Duration:** 4 weeks

-  **Description:** 
  - **Smart Contracts**: Develop required smart contracts for user anonymous identity verification and vote proposal administration, such as counting and publication of results.
  - **Front End for voting process**: Create front end interfaces for users to interact with the voting system, see proposals options and results.

**FTE:** 1 FTE

**Costs:** 5,600 USD

These costs include 40 hours of work per week x 4 weeks x 35 USD per hour = 5,600 USD 

  ### Total Costs: 5,600+ 5,600 = 11,200 USD

## [Section 6] Extended Scope 

-  **Future Plans:**

We plan to extend the functionality of our proof-of-concept system to allow several use cases such as: 
- Anonymous proof of humanity
- Health data privacy
- Know Your Customer
- Privacy-Preserving Verification
- Anti-Sybil Mechanisms
- DAO Governance
- Quadratic Funding (QF)
- Wallet Recovery
- And more

Also we want to extend the usage of ID smart cards to other countries. For instance, the EU has similar kinds of IDs for their residents.
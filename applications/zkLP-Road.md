# ZKLP-Road: Zero-Knowledge Location Privacy for Road Safety

  

  

## [Section 1] Project Information

  

-  **Project Name:** zkLP-Road

-  **Payment Details:** Wallet Address for USDC (on Polygon Network)]

-  **Total Amount Requested:** (e.g., 12,000 USDC)

  

## [Section 2] Project Overview :page_facing_up:

  

-  **Brief Description:**

The project leverages zero-knowledge proofs (ZKPs) to develop a privacy-preserving road safety system by using Plonky3 and CIRCOM. It will enable users to report road anomalies such as accidents, car fires, fights, and robberies, while proving their proximity to the anomaly location without revealing their exact GPS coordinates. The system will detect and verify road anomalies using GPS-based location data and machine learning model.

  

-  **Core Idea:**

- **Problem Statement:**
How can users report road safety issues (anomalies) without exposing their exact location, while ensuring authorities trust the validity of the report?

  1. **Road Anomaly Detection with Location Privacy:**
As more systems adopt smart infrastructure to monitor road conditions, a significant issue arises: users may need to share their exact GPS location when reporting road anomalies. This requirement raises privacy concerns, especially when users might not feel comfortable revealing their precise whereabouts just to report an issue. Traditional systems often sacrifice user privacy for functionality, which creates a barrier for adoption.

  2. **Trust and Verifiability in Anomaly Reports:**
When road authorities receive reports of road anomalies, they often rely on users' honest reporting, which can lead to inaccuracies or spam. There's a need for verifiable, trusted information—something that guarantees the user was in the area without revealing unnecessary details. Current systems often lack this layer of trust, leading to wasted resources when following up on faulty reports.

- **Proposed Solution:**

The primary goal is to apply zero-knowledge proofs to road anomaly detection using camera sensors while preserving location privacy . The system will:

  - Detect road anomalies (accidents, car fires, fighting, and snatching) using the camera feed and GPS data.

  - Build a zero-knowledge proof system using Plonky3 and CIRCOM that generates location proofs without revealing exact GPS coordinates.

  - Enable users to securely and anonymously report road anomalies to authorities, ensuring data integrity and preventing misuse of location information.



- **Technology Stack:**

  -	**Plonky3:** For generating fast recursive proofs, particularly useful when verifying multiple anomaly reports

  -	**CIRCOM:** For writing circuits that define the zero-knowledge proofs. SnarkJS to compile Circom circuits, generating witnesses, and creating/verifying ZKPs

  -	**Polygon zkEVM:** For testing and deploying smart contracts, scalable on-chain verification

  -	**Python/Deep Learning:** For training and integrating model for road anomaly detection (using TensorFlow)

  -	**Geolocation API/GPS Module:** To capture and send GPS coordinates for ZKP creation without revealing exact locations

  -	**Smartphone Sensor APIs/Camera Module/OpenCV:** For image processing and video analysis, useful for preprocessing camera footage and detecting road anomalies in real-time.
  -	**Solidity:** For writing the smart contracts
  -	**Hardhat/Remix IDE:** For developing, testing, and deploying Solidity contracts in a local or testnet environment before deployment on Polygon
  
-  **Design Mockups/Prototypes (Optional):**

![alt text](image-1.png)

  

## [Section 3] Ecosystem Fit

  

-  **Similar Projects:**

There are few projects that focus on privacy-preserving solutions, but none specifically target road safety using real-time road anomaly detection. Some relevant projects include:

  -  **Zk proofs for electric vehicle subsidy terms:** Cybernetica and Galois developed a privacy-preserving technology using ZKPs that allows Estonian electric vehicle (EV) drivers to verify their eligibility for government subsidies by covering a certain mileage in the defined territory without disclosing detailed travel data. The service provider receives the proof and validates the zero-knowledge proof, learning the aggregates, but not the GPS trail (user gains even better confidentiality). https://cyber.ee/resources/stories/ZKP-Dan-Bogdanov/  https://galois.com/blog/2024/09/advancing-the-state-of-the-art-in-zero-knowledge-proofs-sieve-wrap-up/
  -  **Zero-Knowledge Proof of Traffic (zk-PoT):** It enables vehicles to generate zk blind proofs to their independent observation, without leveraging the ground truth or trust evaluation. zk-PoT https://www.researchgate.net/publication/376578187_Zero-Knowledge_Proof_of_Traffic_A_Deterministic_and_Privacy-Preserving_Cross_Verification_Mechanism_for_Cooperative_Perception_Data will not reveal any information about any particular vehicle, thereby preserving the location privacy of the vehicles.
  - **A zkSNARK Proof Approach for Authentication and Location Proof:** This approach allows unmanned aerial vehicles (UAVs) to prove their authenticity or location without disclosing sensitive information. https://www.mdpi.com/1424-8220/24/17/5838

  

+  **Unique Contribution:**

This project addresses the gap in privacy-preserving road anomaly reporting systems. It introduces a ZKP-based system to enable road users and authorities to interact without revealing sensitive location data. This could foster increased adoption in privacy-conscious sectors, such as delivery services or fleet management, where sharing exact routes is problematic.

  - **New Use Case for Zero-Knowledge Proofs:** By extending the use of ZKPs into the road safety domain, ZKLP-Road demonstrates how these cryptographic techniques can be applied to real-world problems like road anomaly reporting and incident detection. 
  - **Efficient Proof Generation with Plonky3:** Leveraging Plonky3’s recursive proofs, ZKLP-Road can handle multiple road anomaly reports and efficiently verify them on-chain.
  - **Privacy-Preserving Anomaly Detection:** Unlike traditional road safety applications, which require users to disclose their exact location and upload footage to centralized servers, ZKLP-Road fills the gap in privacy protection. 
  - **Decentralized Road Safety Data:** With integration into the blockchain ecosystem, ZKLP-Road provides a decentralized platform for road anomaly reporting, where data integrity and user privacy are guaranteed. 

  

## [Section 4] Team :busts_in_silhouette:

  

-  **Team Members:**

Emmanuel Aroso, Agu Dike

  

-  **Contact Information:**

-  **Name:** Emmanuel Aroso
-  **Email:** emarc.aroso@outlook.com

  

-  **Prior Work/Research Emmanuel (Optional):**

    - 1+ year as Blockchain/Web3 developer @Web3Bridge writing Solidity, FE integration with Ethers & TypeScript, ReOwn/WalletConnect, Subgraph, zksync
    - 3+ years as Backend (Django) developer
    - 3+ years as a Cyber Security/Network Engineer 
    - 4+ years building AI Projects such as Face Recognition System using Computer Vision, Detection and Recognition of Road Anomalies (Using Deep Learning and Smartphone), Phishing Detection System using machine learning models, etc.
    - 5+ years building Robotics & IoT Projects including Remote Controlled Smart Home Automation System, IoT-based Smart Irrigation System, etc
    - B.E. Computer Engineering ’23, Quantum Computing at The Coding School ’24 - ‘25

-  **Prior Work/Research Ike (Optional):** 
    - 1+ year as Blockchain/Web3 Developer @Web3Bridge, writing Solidity smart contracts, developing decentralized applications (dApps), and integrating production-ready frontends with Web3 libraries such as Ethers.js, Web3.js, and Appkit.
    - 2+ years as a Fullstack Web Developer, specializing in building scalable APIs and microservices, database management, user authentication and creating end-to-end applications. Graduated as a software engineer with a specialization in Backend development from ALX/Holberton Inc.
    - 2+ Time Web3 Hackathon Bounty Winner, recognized for innovative solutions involving identity, education, and decentralized governance models. Experience in auditing contracts, testing them with Hardhat and Foundry, and integrating Subgraph for querying blockchain data and working on Layer 2 solutions like zkSync and optimistic rollups for scalability.
    - AI and Blockchain researcher, with contributions to decentralized healthcare platforms, exploring the intersection of AI-driven diagnostics and blockchain for secure patient data management. 
    - Passionate about cybersecurity, IoT and Robotics as a hobbyist, with hands-on experience building IoT-based monitoring systems using Raspberry Pi, Arduino, and sensors for real-time data collection and analytics.



  

## [Section 5] Development Roadmap :open_book:

  

  

### Milestone 1 — Research and Development

  

-  **Estimated Duration:** 1 month

-  **Description:**

    - Research and design zero-knowledge circuits using Plonky3 and CIRCOM for privacy-preserving road anomaly detection based on camera data.
    -	Develop prototype ZK circuits for verifying road anomaly occurrences without revealing the exact GPS location.
    -	Train a deep learning model for detecting road anomalies (e.g., accidents, car fires, fights, gunpoint snatchings) using the [RAD dataset](https://www.kaggle.com/datasets/sarfaraznatha/road-anomaly-dataset).
    -	Develop a prototype system with Raspberry Pi, camera and GPS sensors.



-  **FTE (Full-Time Equivalent):**  1.5 FTE

-  **Costs:** 5,000 USDC
  -	**Workmanship:** 3,000 USDC
  -	**Hardware components:** 1,500 USDC
  -	**Miscellaneous expenses:** 500 USDC


  

### Milestone 2 — Completion

  

-  **Estimated Duration:** 1 month

-  **Description:** 

    -	Implement and optimize the Plonky3 circuits developed in Milestone **1**.
    -	Integrate privacy-preserving location proofs into the prototype system.
    -	Deploy the system on Polygon zkEVM Cardona testnet for end-to-end testing.

-  **FTE:** 2 FTE

-  **Costs:** 4,000 USDC
-  **Workmanship:** 3,000 USDC
-	 **Testing and quality assurance:** 500 USDC
-	 **Documentation and deployment costs:** 500 USDC

  
  ### Total Costs: 5,000 + 4,000 = 9,000 USDC

## [Section 6] Extended Scope

  

-  **Future Plans:**

After the initial development phase, we plan to extend the ZKLP-Road project by enhancing its scalability and functionality. Future developments include:
1. **Expanded Anomaly Detection:**
We will integrate more advanced machine learning models to detect a wider range of road anomalies, such as weather-related hazards, road infrastructure issues, and traffic congestion. This will provide a more comprehensive solution for road safety monitoring.

2. **Cross-Platform Deployment:**
The project will be adapted to support multiple platforms, including smart cameras, vehicle dashcams, and drones, broadening its real-world application and reach.

3. **Ecosystem Integration:**
We aim to collaborate with public road authorities and urban planners by integrating the system into existing smart city infrastructure, allowing for automated road maintenance alerts and real-time hazard updates. Additionally, partnerships with insurance companies could streamline claims processes for road incidents, providing verifiable, privacy-preserving proof of incidents.


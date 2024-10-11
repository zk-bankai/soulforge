# Safe Wallet Anonymous Email Management Module (SAMM)

## [Section 1] Project Information



-  **Project Name:** Safe Wallet Anonymous Email Management Module (SAMM)

-  **Payment Details:** 0x526C65A161cD93d9E59371A677e6D4D8092Ee00c

-  **Total Amount Requested:** 15,000 USDC

## [Section 2] Project Overview :page_facing_up:

-  **Brief Description:**
Our proposal introduces an innovative approach to **anonymous and secure multisig wallet management through email**, building upon the [Safe Anonymization Module](https://www.notion.so/1d2253bee3984ce7bccba19720c7410b?pvs=21) (SAM) developed by our team previously under a [SafeDAO grant](https://x.com/safegovernance/status/1728053329219981496). Inspired by the concept of the [emailwallet.org](http://emailwallet.org/), which leverages zkMail technology we aim to transfer these ideas to our SAM. Our proposal, allows users to manage their multisig Safe wallets privately via email, combining the simplicity of email communication with the advanced security and privacy of Zero-Knowledge proofs through native and seamless integration with Safe Ecosystem.

The key concept is the creation of a Safe Anonymous Mail Module (SAMM) for Safe multisig that ensures the anonymity of all its participants using **Circom** language and **ZK Email** architecture.

-  **Core Idea:**
Our goal is to advance the Safe Anonymization Module by integrating innovative user experience solutions. We believe that implementing the zkEmail concept for managing Safe Wallets represents a breakthrough in secure and private email-based multisig asset management.
This project builds on the ideas behind [emailwallet.org](http://emailwallet.org/), adapting them to the Safe Wallet standard by developing the SAM Module. This plug-in module enables private asset management and transaction execution within Safe via email, offering a seamless integration of zkEmail concept for enhanced security and privacy.
Breaf overview about how SAMM works (a lot of details about each step in the next sections):
1. To initiate a transaction, one of the SAMM members sends an email to the relayer's email address with all transaction information (`to, data, amount`).
2. To approve a transaction, all SAMM members send emails to the relayer's email address with the `msgHash` specified in the email header. Each email includes a **DKIM** signature.
3. Upon receiving an email, the relayer stores the approval data in the DB.
4. When the voting threshold is reached, the relayer generates a zk proof and stores it in the DB. After that, the relayer sends the transaction data with the proof to the on-chain SAMM contract.
5. SAMM contract checks that proof is valid and threshold is reached. A transaction can only be executed once the threshold is met.

![image.png](https://i.imgur.com/lxV05Iv.png)

***Smart contracts***

SAMM smart contract serves as a module for the Safe wallet and is developed following [recommendations](https://docs.safe.global/advanced/smart-account-modules) from the Safe wallet documentation. Modules are compatible with Safe wallet version 1.3.0 and above.

Contracts will be written in Solidity and utilize the Foundry development framework.

Previous version of the smart contracts can be found [here](https://github.com/oxor-io/sam-contracts) (SAM contracts). This version is used as a base for the SAMM contracts.

***SAMM permissions***

The multisig has a standard set of EOA owners who have full control over the multisig, including managing the permissions of the SAMM module.

The SAMM module has restrictions on what actions it can perform on behalf of the multisig (security policies). These restrictions are implemented and verified in the smart contract code. For example, the SAMM module cannot change the owners of the Safe multisig or can only call specific smart contracts.

Thus, the SAMM module is used to conveniently manage routine operations, while the standard set of owners is used to handle critically important tasks.

![image.png](https://i.imgur.com/PSIIoJ4.png)

Restrictions on permissions for the SAMM module include a whitelist of contract addresses and function signatures with which the SAMM module can interact on behalf of the Safe multisig.

```jsx
mapping(address to => mapping(bytes4 selector => bool)) public isTxAllowed;
```

Additionally, there is a limit on the amount of ETH that can be transferred to a single address in the whitelist.

```jsx
mapping(address to => uint256) public allowance;
```

This whitelist is initialized when creating the SAMM instance and can be modified by the associated Safe wallet (see the Changing SAMM Parameters section).

***Deployment and initialization of SAMM***

Our module incorporates a proxy pattern; deployment of new SAMM instances occurs through the SAMM factory contract.

![image.png](https://i.imgur.com/ZZMqvOu.png)

For initialization, you can pass a payload when calling `deployProxy` function, which will then be executed by the newly created module. The information provided must align with the function call:

```jsx
function setup(address safe, uint256 root, uint64 threshold, Action[] calldata allowedActions, string relayerEmail, uint256 expirationPeriod) external;

struct Action {
	address to;
	bytes4[] selectors;
  uint256 allowance;
}
```

Here are the explanations of the initialization parameters:

- `safe` - the address of the associated Safe wallet
- `root` - the Merkle root of participant email addresses
- `threshold` - the minimum number of approvals required to execute a transaction
- `allowedActions` - a whitelist of contract addresses and function signatures with which the SAMM module can interact, with a limit on the amount of ETH that can be transferred to a single address.
- `relayerEmail` - the email address of the associated relayer
- `expirationPeriod` - the duration during which the DKIM signature is considered valid

***Connection SAMM to Safe wallet***

To link a module to Safe, Safe must invoke `enableModule` function, passing the address of the created proxy as an argument.

![image.png](https://i.imgur.com/pksn52x.png)

***SAMM transaction execution***

When the relayer receives enough votes to reach the threshold, the relayer sends the transaction data along with zk proof to the SAMM smart contract. There are two transaction execution functions:

```jsx
function executeTransaction(
    address to,
    uint256 value,
    bytes memory data,
    ISafe.Operation operation,
    Proof calldata proof
) external returns (bool success);

function executeTransactionReturnData(
    address to,
    uint256 value,
    bytes memory data,
    ISafe.Operation operation,
    Proof calldata proof
) external returns (bool success, bytes memory returnData);
```

The primary distinction is that the second function also returns the data from the transaction execution, while the first only returns the execution status.

A transaction can only be executed once the threshold is met.
These functions have no restrictions on who can call them, as the address executing the transaction does not matter as long as zk proof is valid.

Additionally, the contract includes a `nonce` counter that increments with each transaction execution. It is needed to prevent the re-execution of the same transaction and to maintain the order of transaction execution.


***Changing SAMM parameters***

Next contract parameters can be modified:

- `threshold` - the required number of votes to execute a transaction
- `root` - the root of the Merkle tree containing all participant addresses
- `allowedActions` - a whitelist of contract addresses and function signatures with which the SAMM module can interact, with a limit on the amount of ETH that can be transferred to a single address.
- `relayerEmail` - the email address of the associated relayer
- `expirationPeriod` - the duration during which the DKIM signature is considered valid

For each parameter, there is a setter function that can only be called by the associated Safe wallet.

***Circuits***

Circuits will be written in **Circom** and utilize the *Groth16** proving scheme.
The implementation of the circuit will utilize the DKIM signature verification logic from the [zkMail](https://github.com/zkemail/zk-email-verify/tree/main/packages/circuits) project on Circom and part of the logic for checking the module membership from the [SAM](https://github.com/oxor-io/sam-circuits) project.

***SAMM members’ root***

The list of email addresses of SAMM members is formed at the creation of the module and can be changed by the decision of the associated Safe wallet.

A Merkle tree is used to store the email addresses of the SAMM module members.

![image.png](https://i.imgur.com/jHObtcD.png)

The height of the tree is a parameter that can be chosen by the user depending on the business case, with a default value of 5 (32 members).

****msgHash****

To identify the transaction, the parameter `msgHash` is used in the email header and during verification within the circuit. It is calculated as follows:

```jsx
bytes32 calldataHash = keccak256(data);
bytes32 msgHash = keccak256(abi.encode(to, value, calldataHash, operation, nonce, address(this), block.chainid));
```

****Proof****

Upon receiving an email from a SAMM module participant, the Relayer generates a ZK proof using the Barretenberg proving library.

ZK proof checks the following points for each approval:

1. The sender's email address (`from` field of header) is SAMM module participant. Checking of Merkle tree inclusion proof. Needed circuit’s inputs:
    - `private header`
    - `private member`
    - `public root`
    - `private pathElements[levels]`
    - `private pathIndices[levels]`
2. The recipient's email address (`to` field of header) is the relayer's email address. Needed circuit’s input:
    - `private header`
    - `public relayer`
3. The email header contains the correct multisig `msgHash` in `subject` field. Needed circuit inputs:
    - `private header`
    - `public msgHash`
4. There is a DKIM signature verifying the validity of the email, and less than the `expirationPeriod` has passed since the signature was made. Needed circuit inputs:
    - `private header`
    - `private pubkey`
    - `private signature`
    - `public currentTimestamp`
    - `public expirationPeriod`

***Relayer infrustructure***

An [open-source solution](https://github.com/zkemail/email-wallet/tree/main/packages/relayer) by ZK Email is used as the basis for our off-chain relayer infrastructure. We are planning to adapt this solution for our project.

![image.png](https://i.imgur.com/0WQXJCm.png)

It consists of the following main components:

- **SMTP Server**: The entry point for emails, which the Relayer monitors for incoming messages that trigger blockchain transactions.
- **Relayer**: The core service that listens for emails from the SMTP server, communicates with the Prover to create proofs, and then sends the validated transactions to the blockchain.
- **Prover**: A separate service that the Relayer relies on to create zk proofs.
- **Database**: A database to store the relayer's state, including lists of wallets, emails, transactions, signatures, and so on.
- **API Service**: This service is designed to transfer transaction information from the database to the user interface.

It's important to highlight the privacy assumptions of all Relayer infrastructure. In fact, all these off-chain components handle privacy data about members' approvals. It is assumed that no external parties have access to this infrastructure. And it should be considered that if a third-party Relayer infrastructure is used, privacy data is accessible to the provider of this infrastructure.

****SMTP Server****

A reliable open-source SMTP server will be used (we have not yet decided on a specific one).

****Initiation email****

The initiation email contains the following significant fields:

- The subject of the email header stores only the `msgHash`.
- The email body contains all the transaction information:
    - **to** - The target address to be called by the Safe.
    - **value** - The amount in wei to be sent.
    - **data** - The data payload of the transaction.
    - **operation** - The type of Safe operation (CALL, DELEGATECALL).
    - **nonce** - The SAMM nonce used for the transaction.
    - **safe** - The address of the associated Safe wallet.
    - **chainid** - The blockchain chain ID used.

All parameters in the body and subject are generated for the user on a special UI page (see the UI section).

****Approve email****

Upon receiving the initiate email, the relayer verifies the transaction's validity and sends an email to other SAMM participants notifying them of the new transaction creation. Thus, other participants receive all information from the initiate email and can confirm the transaction by sending an approve email to the relayer's email address.

The approve email contains only one significant field:

- The subject of the email header stores only the `msgHash`.

****Relayer****

A backend service that connects with an SMTP Server, Prover, Database, and SAMM smart contract. Its main functions include:

1. Listen to the SMTP Server for new messages from SAMM members. Upon receiving a new message, it checks its validity (sender, nonce, allowedActions, expirationPeriod etc.) and stores it in the database. Upon receiving an initiation email, it sends emails to other SAMM participants with complete information about the new transaction.
2. When the required number of approvals for a new `msgHash` is reached, it generates a zk proof. It sends all circuit inputs to the Prover and receives a ready zk proof in return, which it then saves in the DB.
3. Listen to the SAMM contract for events about module parameter updates (threshold, root, relayerEmail). Upon receiving an event, update the data in the database.

****Prover****

The [ZK Email Prover](https://github.com/zkemail/email-wallet/tree/main/packages/prover) is taken as the base. Primarily, it's a simple service that does just one thing - it takes all circuit inputs, generates a zk proof, and returns it in response.

****Database****

**Postgres** is used as the database.

The main tables for storing data look as follows:

- SAMM instances table - this table contains information about each individual SAMM instance:

```sql
CREATE TABLE IF NOT EXISTS samms (
	id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
	samm_addres TEXT NOT NULL,
	safe_address TEXT NOT NULL,
	threshold INTEGER NOT NULL,
	expiration_period INTEGER NOT NULL,
	root TEXT NOT NULL,
	nonce INTEGER NOT NULL,
	chainid INTEGER NOT NULL,
);
```

- SAMM members table:

```sql
CREATE TABLE IF NOT EXISTS members (
	id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
	email_address TEXT NOT NULL,
	samm_id INTEGER NOT NULL REFERENCES samms (id),
	is_acctive BOOLEAN NOT NULL
);
```

- Emails table:

```sql
CREATE TYPE email_type AS ENUM ('initiate', 'approve', 'new_tx', 'executed_tx');

CREATE TABLE IF NOT EXISTS emails (
	id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
	type email_type NOT NULL,
	from TEXT NOT NULL,
	to TEXT NOT NULL,
	tx_id INTEGER NOT NULL REFERENCES txns (id),
	created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

- Transactions table:

```sql
CREATE TYPE tx_status AS ENUM ('pending', 'confirmed', 'sent', 'success', 'failed');

CREATE TABLE IF NOT EXISTS txns (
	id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
	msg_hash TEXT NOT NULL,
	to TEXT NOT NULL,
	value NUMERIC NOT NULL,
	data TEXT NOT NULL,
	operation INTEGER NOT NULL,
	nonce INTEGER NOT NULL,
	proof TEXT NOT NULL,
	samm_id INTEGER NOT NULL REFERENCES samms (id),
	status tx_status NOT NULL,
	created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

- Approvals table:

```sql
CREATE TABLE IF NOT EXISTS approvals (
	id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
	tx_id INTEGER NOT NULL REFERENCES txns (id),
	member_id INTEGER NOT NULL REFERENCES members (id),
	signature TEXT NOT NULL,
	created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

****API Service****

This service is designed to transfer transaction information from the database to the user interface.

In fact, it has read access to all database tables because information from all tables is necessary for various UI logic (see UI section).

It's important to emphasize that the UI is only accessible to SAMM members' emails, so no private information will be disclosed to unauthorized users.

***Final workflow***

![image.png](https://i.imgur.com/qdkSU71.png)


-  **Technology Stack**

1. **Frontend**: React.js / Vite for building the user interface.
2. **Backend**: Python or Rust for server-side logic and processing.
3. **Blockchain**: Ethereum (or EVM compatible) as the underlying blockchain platform.
4.  **ZK Proofs**: Circom for creating zero-knowledge circuits.

-  **Design Mockups/Prototypes (Optional):**
The UI is available only to SAMM members' emails and allows them to:

1. Monitor the status of each SAMM transaction.
2. Generate tx data for the Initiation email.
3. Generate tx data for changing SAMM parameters (these transactions will be executed through the classic Safe Wallet UI on behalf of associated Safe owners).

Mockups are available here: [https://miro.com/app/board/uXjVLZkZPN0=/](https://miro.com/app/board/uXjVLZkZPN0=/)

## [Section 3] Ecosystem Fit



-  **Similar Projects:**

The closest solution is [emailwallet.com](https://emailwallet.com) with the safe 2fa feature described [here](https://rove.email/blog/2fa). However, the main idea of our solution is to bring a privacy option for Safe multisig as part of the original [SAM project](https://github.com/oxor-io/sam-circuits).


-  **Unique Contribution:**

Our project demonstrates how Circom can be applied to address real-world scenarios for key technologies, such as Safe Wallet and ZkMail.



## [Section 4] Team :busts_in_silhouette:



-  **Team Members:**

**Oxorio** is a blockchain security firm that specializes in smart contracts, ZK solutions, and security consulting. With a decade of blockchain development and five years in smart contract auditing, our expert team delivers premier security services for projects at any stage of maturity and development.

*   Website: [https://oxor.io/](https://oxor.io/)
*   Github: [https://github.com/oxor-io](https://github.com/oxor-io)
*   Email: [grants@oxor.io](mailto:wei@oxor.io)

**Team members involved in the project:**

*   **Alexander Mazaletskiy ([CV](https://docsend.com/view/qssknr6bh6a4wkrf)):** With over 10 years of experience in blockchain development and auditing, coupled with extensive expertise in ZK proofs, he has led the development and audit of ZK-based cryptographic modules. His work spans the implementation and audit of ZK-Stark, ZK-Snark, Plonk, and Halo algorithms, with a strong focus on enhancing security and privacy in blockchain projects through advanced ZK techniques.
*   **Alexander Drygin ([CV](https://docsend.com/view/htjdn65yukgi5ers)):** with over 5 years of experience in blockchain development and auditing and specializing in ZK proofs, he has been pivotal in developing and auditing ZK-focused projects, with key contributions to Tornado Cash, Tornado Nova’s fork Privacy Pools and Safe DAO Anonymous Module, enhancing privacy and security through advanced cryptographic methods.

-  **Contact Information:**

-  **Name:** Aleksandr Avdonin

-  **Email:** [wei@oxor.io](mailto:wei@oxor.io)

**Our past experience:**


*   Our team was a finalist of ETHGlobal 2023 hackathon with [ZKvote application](https://ethglobal.com/showcase/zkvote-cc-rsvkt) utilizing ZK proofs for cross-chain L2 voting. Awarded a sponsorship prize from Scroll for the utilization of recursive SNARKs in Noir.
*   [Circom Contracts](https://github.com/oxor-io/sam-circuits/tree/main/circuits/circom) for the Safe Anonymization Module, developed as part of the SafeDAO grant work.
*   [Safe Wallet Anonymous Email Management Module research project powered by zkEmail in Noir](https://github.com/orgs/noir-lang/discussions/5813).



## [Section 5] Development Roadmap :open_book:

Since our project is under implementation using the Noir framework, we expect that some of the services other than circuits will already be ready by the time we start working with Circom, so we are considering work that will be designed to port code from Noir to Circom.

**Potential Start Date: 1 December, 2024**

### Milestone 1 — Circuits

-  **Estimated Duration:** 2 weeks

-  **Description:**
	- Development of the SAMM circuits in Circom
-  **FTE (Full-Time Equivalent):** 1.5 FTE

-  **Costs:** 10,000 USDC.

### Milestone 2 — UI and Relayer

-  **Estimated Duration:** 2 weeks

-  **Description:**
	- Development of the Relayer service
	- Connecting to the UI
	- Testing and preparation of final documentation

-  **FTE (Full-Time Equivalent):** 1.5 FTE

-  **Costs:** 5,000 USDC.

### Total Costs: (e.g. 10,000+ 5,000 = 15,000 USDC)



## [Section 6] Extended Scope



-  **Future Plans:**

We expect that as part of the open-source project, the module will continue to develop and its capabilities will improve, both in terms of user interface and in terms of safe management capabilities using the module. For example, we are considering using [Relay Kit](https://docs.safe.global/sdk/relay-kit) to make transactions using tokens from the Safe Wallet.
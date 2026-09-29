# Unit 3 --- Blockchain Implementation

> **Exam-focused notes:** Simple language, definitions, step-by-step
> explanations, examples, important points, and short exam answers.

------------------------------------------------------------------------

# 1. Bitcoin

## Definition

**Bitcoin** is a decentralized digital currency and a blockchain network
that allows people to transfer value directly over a peer-to-peer
network without requiring a traditional central authority such as a
bank.

Bitcoin was introduced through the **Bitcoin whitepaper in 2008**, and
its network became operational in **2009**.

## Main Features

-   Decentralized
-   Peer-to-peer
-   Uses blockchain
-   Uses cryptography
-   Uses Proof of Work (PoW)
-   Uses miners to add blocks
-   Has a fixed maximum supply of 21 million BTC under the protocol
    rules

## Basic Bitcoin Transaction Flow

``` text
User creates transaction
        ↓
Transaction is digitally signed
        ↓
Broadcast to network
        ↓
Nodes verify transaction
        ↓
Miner includes transaction in a block
        ↓
Proof of Work
        ↓
Block is accepted
        ↓
Blockchain is updated
```

------------------------------------------------------------------------

# 2. Bitcoin Block

A **Bitcoin block** is a collection of valid transactions together with
information required by the Bitcoin protocol.

A simplified block contains:

``` text
Bitcoin Block
│
├── Block Header
│   ├── Version
│   ├── Previous Block Hash
│   ├── Merkle Root
│   ├── Timestamp
│   ├── Difficulty Target
│   └── Nonce
│
└── Block Transactions
```

## Important Block Header Fields

### Previous Block Hash

Stores the hash of the previous block header.

It connects the current block to the previous block.

``` text
Block 100 → Block 101 → Block 102
```

### Merkle Root

A single hash that summarizes the transactions included in the block.

### Timestamp

Records the approximate time associated with the block.

### Nonce

A value miners change while searching for a valid Proof of Work.

### Difficulty Target

Defines the required threshold that a valid block hash must satisfy.

------------------------------------------------------------------------

# 3. Merkle Root

## Definition

The **Merkle root** is the top hash of a Merkle tree and provides a
compact cryptographic summary of the transactions in a block.

## Example

Suppose a block contains four transactions:

``` text
TX1    TX2    TX3    TX4
 ↓      ↓      ↓      ↓
H1     H2     H3     H4
 \     /       \     /
  H12             H34
     \           /
       Merkle Root
```

The transaction hashes are combined and hashed repeatedly until one
final hash remains.

That final hash is the **Merkle root**.

## Why is Merkle Root Important?

It helps:

-   Summarize all transactions in a block
-   Detect changes in transactions
-   Verify transaction inclusion efficiently
-   Reduce the amount of data required for certain proofs

## Exam Definition

> The Merkle root is the single hash at the top of a Merkle tree that
> represents the transactions contained in a blockchain block.

------------------------------------------------------------------------

# 4. Eventual Consistency and Bitcoin

## Definition of Eventual Consistency

**Eventual consistency** means that replicas of a distributed system may
temporarily have different states, but if no new updates occur, they can
eventually converge to the same state.

## Eventual Consistency in Bitcoin

Bitcoin operates in a distributed environment.

Different nodes may temporarily see different information because:

-   Network messages take time to propagate.
-   Two miners may find valid blocks close to each other.
-   Some nodes may receive one block before another.

This can temporarily create different views of the latest blockchain
tip.

## Example

Suppose two miners find competing blocks:

``` text
        Block 100
        /       \
Block 101A     Block 101B
```

Some nodes may see `101A` first while others see `101B`.

As additional blocks are produced and nodes follow the protocol's
chain-selection rules, the network converges toward a common accepted
history.

## Important Point

Bitcoin does **not** require every node to see every update at exactly
the same instant.

Instead, the protocol is designed so that honest nodes can converge on a
common history.

## Exam Definition

> Eventual consistency in Bitcoin refers to the tendency of distributed
> nodes to converge on a common blockchain history over time, even
> though they may temporarily have different views.

------------------------------------------------------------------------

# 5. Byzantine Fault Tolerance (BFT)

## Definition

A **Byzantine fault** occurs when a participant in a distributed system
behaves incorrectly, inconsistently, or maliciously.

A system is **Byzantine fault tolerant** when it can continue to reach
an acceptable agreement despite some faulty or malicious participants,
within the assumptions of the protocol.

## Simple Example

Suppose there are several computers in a network:

``` text
Node A → Honest
Node B → Honest
Node C → Malicious
Node D → Honest
```

The malicious node may send incorrect information.

A Byzantine fault-tolerant system is designed to prevent such a node
from causing the honest participants to accept an invalid state,
assuming the protocol's fault threshold is respected.

------------------------------------------------------------------------

# 6. Byzantine Fault Tolerance and Bitcoin

Bitcoin does not use a classical BFT protocol such as PBFT.

Instead, Bitcoin uses **Proof of Work and Nakamoto consensus** to allow
a decentralized network to agree on transaction history despite the
presence of potentially malicious participants.

## How Bitcoin Handles Malicious Participants

Bitcoin uses:

-   Proof of Work
-   Cryptographic signatures
-   Transaction validation
-   Economic incentives
-   Decentralized verification
-   Chain-selection rules

## Important Concept

Bitcoin's security model assumes that an attacker cannot control enough
hash power to consistently dominate the network.

The commonly discussed **51% attack** refers to an attacker controlling
a majority of the network's mining hash rate. Such control can enable
certain forms of transaction-history manipulation, such as reorganizing
recent blocks or censoring transactions, but it does not allow arbitrary
creation of valid coins outside the protocol's rules.

## Exam Point

> Bitcoin achieves decentralized consensus using Proof of Work rather
> than using a traditional Byzantine Fault Tolerant protocol such as
> PBFT.

------------------------------------------------------------------------

# 7. Bitcoin Block Size

## Definition

**Block size** refers to the amount of transaction data that can be
included in a Bitcoin block under the protocol's rules.

Block capacity affects:

-   Number of transactions that can fit
-   Transaction throughput
-   Network propagation
-   Storage requirements
-   Scalability

## Why Block Size Matters

If blocks are too small:

-   Fewer transactions can fit in each block.
-   Users may experience more competition for block space.

If blocks are larger:

-   More transactions can fit.
-   Blocks may take longer to propagate across the network.
-   Resource requirements for nodes can increase.

Therefore, block capacity involves trade-offs between:

``` text
Scalability ↔ Decentralization ↔ Network Resource Requirements
```

## Bitcoin Block Size and SegWit

Bitcoin's **Segregated Witness (SegWit)** upgrade changed how block
capacity is measured by separating witness data from the traditional
transaction data structure and introducing the concept of **block
weight**.

Therefore, modern Bitcoin discussions often use **block weight** rather
than simply referring to a fixed byte-size limit.

## Exam Definition

> Bitcoin block capacity determines how much transaction data can be
> included in a block and directly affects transaction throughput,
> propagation, and scalability.

------------------------------------------------------------------------

# 8. Bitcoin Mining

## Definition

**Bitcoin mining** is the process by which participants called miners
use computational power to compete to add new blocks to the Bitcoin
blockchain through Proof of Work.

## Mining Process

``` text
Transactions
      ↓
Miner selects transactions
      ↓
Creates candidate block
      ↓
Builds block header
      ↓
Changes nonce / other permitted fields
      ↓
Computes hash repeatedly
      ↓
Finds hash satisfying target
      ↓
Broadcasts block
      ↓
Other nodes verify
      ↓
Block added to blockchain
```

## What Does a Miner Do?

A miner:

1.  Collects valid transactions.
2.  Creates a candidate block.
3.  Calculates the Merkle root.
4.  Builds the block header.
5.  Searches for a valid Proof of Work.
6.  Broadcasts the block.
7.  Receives the block reward and transaction fees if the block is
    accepted and the protocol rules provide the corresponding reward.

## Mining Reward

Bitcoin miners can receive:

-   **Block subsidy**
-   **Transaction fees**

The block subsidy is reduced periodically through Bitcoin's halving
mechanism.

## Why Mining is Important

Mining helps:

-   Add new blocks
-   Order transactions
-   Secure the network
-   Make rewriting recent history computationally expensive
-   Incentivize participants to provide hash power

------------------------------------------------------------------------

# 9. Bitcoin Mining Difficulty

## Definition

Mining difficulty controls how difficult it is to find a valid Proof of
Work.

Bitcoin adjusts its difficulty periodically so that blocks are produced
at approximately the protocol's target rate, historically around **10
minutes per block on average**.

## Simple Idea

``` text
More total mining power
        ↓
Difficulty adjusts upward

Less total mining power
        ↓
Difficulty adjusts downward
```

The goal is to keep block production close to the protocol's target over
time.

------------------------------------------------------------------------

# 10. Collaborative Blockchain Implementations

## Definition

**Collaborative blockchain implementations** are blockchain or
distributed ledger systems designed for multiple organizations or known
participants to work together.

They are commonly used in:

-   Banking
-   Supply chains
-   Trade
-   Insurance
-   Enterprise data sharing

Two important platforms in this syllabus are:

-   Hyperledger
-   Corda

------------------------------------------------------------------------

# 11. Hyperledger

## Definition

**Hyperledger** is an open-source umbrella project hosted by the Linux
Foundation that supports enterprise distributed ledger technologies.

One well-known Hyperledger project is **Hyperledger Fabric**.

## Hyperledger Fabric

Hyperledger Fabric is a **permissioned distributed ledger platform**
designed for enterprise use.

## Main Features

-   Permissioned network
-   Known participants
-   Identity management
-   Modular architecture
-   Smart contracts called chaincode
-   Channels for privacy between selected participants
-   Suitable for enterprise applications

## Example

Suppose several companies in a supply chain want to share transaction
information.

``` text
Manufacturer
     ↓
Distributor
     ↓
Wholesaler
     ↓
Retailer
```

A permissioned ledger can allow approved organizations to share and
verify relevant records.

## Advantages

-   Privacy
-   Access control
-   Enterprise-oriented architecture
-   Flexible consensus and components
-   Suitable for multi-organization networks

## Exam Definition

> Hyperledger is an open-source enterprise blockchain and distributed
> ledger ecosystem, with projects such as Hyperledger Fabric designed
> for permissioned business networks.

------------------------------------------------------------------------

# 12. Corda

## Definition

**Corda** is a distributed ledger platform designed primarily for
business transactions between known parties.

It was developed with strong focus on financial and enterprise use
cases.

## Main Features

-   Permissioned environment
-   Known participants
-   Privacy-oriented transaction sharing
-   Smart contracts
-   Point-to-point data sharing
-   Suitable for business networks

## Important Difference from Traditional Blockchain

In many blockchain systems, transactions are broadly broadcast across
the network.

Corda is designed so that transaction information is shared primarily
with the parties that need to know it.

## Example

``` text
Bank A ←→ Bank B
   ↓         ↓
Transaction shared with relevant parties
```

Not every participant needs to receive every transaction.

## Exam Definition

> Corda is an enterprise distributed ledger platform designed to record
> and automate business agreements between known parties while limiting
> transaction data to relevant participants.

------------------------------------------------------------------------

# 13. Hyperledger vs Corda

  -----------------------------------------------------------------------
  Feature                 Hyperledger Fabric      Corda
  ----------------------- ----------------------- -----------------------
  Type                    Permissioned DLT        Permissioned DLT

  Main focus              Enterprise networks     Business/financial
                                                  agreements

  Data sharing            Controlled              Mainly relevant parties

  Smart contracts         Chaincode               Contract + flow model

  Participants            Known/authorized        Known/authorized

  Typical use             Supply chain,           Finance, trade,
                          enterprise networks     business workflows
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 14. Ethereum

## Definition

**Ethereum** is a decentralized blockchain platform designed to support
programmable smart contracts and decentralized applications.

Unlike Bitcoin, which was primarily designed around decentralized
digital money, Ethereum provides a general-purpose programmable
environment.

## Main Concepts

-   Ether (ETH)
-   Smart contracts
-   Ethereum Virtual Machine (EVM)
-   Tokens
-   Decentralized applications (DApps)
-   Decentralized organizations

------------------------------------------------------------------------

# 15. ERC-20

## Definition

**ERC-20** is a widely used Ethereum token standard that defines a
common interface for fungible tokens.

**ERC** means **Ethereum Request for Comments**.

ERC-20 defines standard functions and events that token contracts can
implement.

## Common ERC-20 Functions

-   `totalSupply()`
-   `balanceOf()`
-   `transfer()`
-   `approve()`
-   `allowance()`
-   `transferFrom()`

## Simple Example

Suppose a project creates a token called `ABC`.

The token can follow the ERC-20 standard:

``` text
ABC Token
   ↓
ERC-20 Smart Contract
   ↓
Ethereum Blockchain
```

Wallets and applications can interact with the token using the standard
interface.

## Fungible Token

A fungible token means each unit of the same token is generally
interchangeable with another unit of that token.

Example:

``` text
1 ABC = 1 ABC
```

assuming they represent the same token contract and units.

------------------------------------------------------------------------

# 16. ERC-20 Token Explosion

## Meaning

The term **token explosion** refers to the large growth in the number of
Ethereum-based tokens and token projects enabled by reusable token
standards such as ERC-20.

Because developers can create tokens using smart contracts and
standardized interfaces, creating and distributing new tokens became
much easier.

## Why Did It Happen?

### 1. Standard Interface

ERC-20 provided common functions.

### 2. Smart Contracts

Developers could program token rules.

### 3. Existing Ethereum Infrastructure

Tokens could use existing:

-   Wallets
-   Exchanges
-   Smart contract tools
-   Developer libraries

### 4. Fundraising

Tokens were widely used in **Initial Coin Offerings (ICOs)** and other
fundraising models.

## Important Point

ERC-20 made token creation easier, but the existence of an ERC-20 token
does **not** by itself guarantee that the project is legitimate,
valuable, or secure.

------------------------------------------------------------------------

# 17. Full Ecosystem Decentralization

## Definition

**Decentralization** in a blockchain ecosystem means distributing
control, validation, infrastructure, and decision-making across multiple
independent participants rather than relying on one central authority.

A blockchain ecosystem can involve decentralization at different layers:

``` text
Users
  ↓
Wallets
  ↓
DApps
  ↓
Smart Contracts
  ↓
Blockchain Network
  ↓
Nodes / Validators
```

## Important Point

A project can use blockchain technology without being fully
decentralized.

For example, a smart contract may be deployed on a decentralized
blockchain while important administrative controls remain with a small
group.

------------------------------------------------------------------------

# 18. Smart Contract

## Definition

A **smart contract** is a program deployed on a blockchain that
automatically executes predefined rules when specified conditions are
met.

In simple words:

> **A smart contract is blockchain-based code that executes according to
> programmed rules.**

## Example

Suppose:

``` text
IF payment = received
THEN transfer digital asset
```

The blockchain executes the programmed logic when the required
conditions are satisfied.

## Features

-   Programmable
-   Deterministic execution
-   Runs according to predefined rules
-   Can interact with other contracts
-   Can manage digital assets

## Advantages

-   Automation
-   Reduced need for manual processing
-   Transparent code execution
-   Can operate without a traditional central intermediary

## Limitations

-   Bugs can cause serious problems
-   Smart contracts cannot automatically know real-world information
    without external data sources
-   Transaction execution can require network fees
-   Code quality and security are critical

------------------------------------------------------------------------

# 19. Decentralized Autonomous Organization (DAO)

## Definition

A **DAO** is an organization whose rules and decision-making processes
are implemented partly through blockchain-based smart contracts and
decentralized governance mechanisms.

## Basic Structure

``` text
Members
   ↓
Governance / Voting
   ↓
Smart Contracts
   ↓
Blockchain
   ↓
Execution of Approved Actions
```

## Features

-   Blockchain-based governance
-   Rules can be implemented through smart contracts
-   Members may participate in voting
-   Decisions can be recorded transparently
-   Does not necessarily rely on a traditional centralized management
    structure

## Example

A DAO may allow token holders or members to vote on a proposal such as:

``` text
Should the organization spend 100 ETH
on Project X?
```

The governance system records and processes the decision according to
its rules.

## Limitations

-   Governance can be complicated
-   Voting power may be concentrated
-   Smart contract bugs can cause losses
-   Legal status varies by jurisdiction

------------------------------------------------------------------------

# 20. Decentralized Applications (DApps)

## Definition

A **DApp (Decentralized Application)** is an application that uses
blockchain-based smart contracts as part of its backend or core logic.

## Traditional Application

``` text
User
 ↓
Frontend
 ↓
Central Server
 ↓
Database
```

## DApp

``` text
User
 ↓
Frontend
 ↓
Blockchain / Smart Contracts
 ↓
Distributed Network
```

A DApp may still have centralized components such as a frontend website
or external services, so "decentralized" does not necessarily mean every
component is decentralized.

## Features

-   Uses smart contracts
-   Interacts with blockchain
-   Can use blockchain tokens/assets
-   Provides transparent on-chain logic where applicable
-   Users may interact through blockchain wallets

## Examples of DApp Categories

-   Decentralized exchanges
-   Lending applications
-   Games
-   NFT marketplaces
-   Governance applications

------------------------------------------------------------------------

# 21. Smart Contract vs DAO vs DApp

  Concept          Meaning
  ---------------- -------------------------------------------------------------
  Smart Contract   Blockchain program that executes predefined rules
  DAO              Organization/governance system using blockchain-based rules
  DApp             Application that uses blockchain/smart contracts

### Easy Example

``` text
Smart Contract → Code
DAO            → Organization/Governance
DApp           → Application
```

------------------------------------------------------------------------

# 22. Bitcoin vs Ethereum

  -----------------------------------------------------------------------
  Feature                 Bitcoin                 Ethereum
  ----------------------- ----------------------- -----------------------
  Main purpose            Decentralized digital   Programmable blockchain
                          money                   platform

  Native asset            BTC                     ETH

  Smart contracts         Limited scripting       General-purpose smart
                          functionality           contracts

  DApps                   Not its primary focus   Major part of ecosystem

  Token standards         Not based on ERC-20     Supports standards such
                                                  as ERC-20

  Consensus               Proof of Work           Proof of Stake
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 23. Important Exam Questions

## Q1. What is a Merkle root?

> A Merkle root is the single hash at the top of a Merkle tree that
> summarizes the transactions in a block.

## Q2. What is Bitcoin mining?

> Bitcoin mining is the process of using computational power to perform
> Proof of Work and propose new blocks according to Bitcoin's protocol.

## Q3. What is eventual consistency?

> Eventual consistency means that distributed replicas may temporarily
> have different states but can converge to a common state over time
> when updates stop.

## Q4. Does Bitcoin use PBFT?

> No. Bitcoin does not use classical PBFT. It uses Proof of Work and
> Nakamoto-style consensus to coordinate its decentralized network.

## Q5. What is a Bitcoin block?

> A Bitcoin block is a collection of valid transactions together with
> block-header information required by the Bitcoin protocol.

## Q6. What is block size?

> Block size/capacity refers to the amount of transaction data that can
> be included in a Bitcoin block under the protocol's rules.

## Q7. What is Hyperledger?

> Hyperledger is an open-source enterprise distributed ledger ecosystem
> hosted by the Linux Foundation, including projects such as Hyperledger
> Fabric.

## Q8. What is Corda?

> Corda is an enterprise distributed ledger platform designed for
> business transactions between known parties with controlled data
> sharing.

## Q9. What is ERC-20?

> ERC-20 is an Ethereum token standard that defines a common interface
> for fungible tokens.

## Q10. What is a smart contract?

> A smart contract is a blockchain-based program that executes
> predefined rules automatically according to its code.

## Q11. What is DAO?

> A DAO is an organization whose governance and rules are implemented
> partly through blockchain-based smart contracts and decentralized
> decision-making mechanisms.

## Q12. What is a DApp?

> A DApp is an application that uses blockchain and smart contracts as
> part of its core functionality.

------------------------------------------------------------------------

# 24. One-Line Revision

``` text
Bitcoin       → Decentralized digital currency/network
Block         → Transactions + block information
Merkle Root   → Single hash summarizing block transactions
Mining        → PoW-based block production
Miner         → Participant performing PoW
Eventual Consistency → Nodes can converge to common state over time
BFT           → Tolerating certain faulty/malicious participants
Block Capacity → Amount of transaction data a block can contain
Hyperledger   → Enterprise DLT ecosystem
Fabric        → Permissioned enterprise DLT platform
Corda        → Business-focused distributed ledger
Ethereum      → Programmable blockchain platform
ERC-20        → Fungible token standard
Token Explosion → Large growth of Ethereum-based tokens
Smart Contract → Blockchain program
DAO           → Blockchain-based organization/governance
DApp          → Application using blockchain/smart contracts
```

------------------------------------------------------------------------

# 25. Last-Minute Exam Revision

Remember these key points:

1.  **Merkle Root → Summary hash of transactions**
2.  **Previous Hash → Connects blocks**
3.  **Mining → Proof of Work**
4.  **Miner → Performs computational work**
5.  **Bitcoin → PoW**
6.  **Bitcoin does not use PBFT**
7.  **Eventual Consistency → Temporary differences can converge**
8.  **BFT → Handles certain faulty/malicious participants**
9.  **Hyperledger → Enterprise DLT ecosystem**
10. **Fabric → Permissioned enterprise platform**
11. **Corda → Business/financial DLT**
12. **ERC-20 → Fungible Ethereum token standard**
13. **Smart Contract → Blockchain program**
14. **DAO → Organization + decentralized governance**
15. **DApp → Application using blockchain/smart contracts**

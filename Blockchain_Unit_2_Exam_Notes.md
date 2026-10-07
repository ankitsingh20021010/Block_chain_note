# Unit 2 --- Blockchain Functionality

> **Exam-focused notes:** Simple language, clear definitions, examples,
> important points, and comparisons.

------------------------------------------------------------------------

# 1. Distributed Identity

## Definition

**Distributed identity** is an identity system where a person's identity
information is not completely controlled by one central organization.
The user can have greater control over their identity and credentials.

In simple words:

> **Distributed identity allows users to control and use their digital
> identity across different services without depending completely on one
> central identity provider.**

## Traditional Identity vs Distributed Identity

### Traditional Identity

``` text
User → Central Authority → Identity Verification
```


Example:

A government department or company stores and manages your identity
information.

### Distributed Identity

``` text
User
 ↓
Digital Identity / Wallet
 ↓
Different Services
```

The user can present required credentials to different services.

## Main Features

-   User-centric identity
-   Reduced dependence on a single identity provider
-   Cryptographic keys can be used to control access
-   Credentials can be digitally verified
-   Can improve privacy when only required information is shared

## Example

A student can have a digital credential proving that they are enrolled
at a university and present that credential to another service without
repeatedly submitting physical documents.

------------------------------------------------------------------------

# 2. Digital Identification

## Definition

**Digital identification** is the process of identifying or verifying a
person, organization, device, or account in a digital environment.

Examples include:

-   Username and password
-   Digital certificates
-   Government digital identity systems
-   Biometric authentication
-   Cryptographic credentials

## Digital Identification in Blockchain

Blockchain can help verify digital credentials using:

-   Public/private key cryptography
-   Digital signatures
-   Verifiable credentials
-   Distributed ledgers

## Benefits

-   Faster verification
-   Reduced document handling
-   Tamper-evident records
-   Can support secure digital authentication

------------------------------------------------------------------------

# 3. Public and Private Keys

Blockchain systems commonly use **public-key cryptography**.

There are two related keys:

1.  Public Key
2.  Private Key

## Public Key

A **public key** can be shared with others.

It can be used for:

-   Identifying an account/address in cryptographic systems
-   Verifying digital signatures
-   Supporting encryption in systems that use public-key encryption

## Private Key

A **private key** must be kept secret.

It can be used to:

-   Create digital signatures
-   Authorize transactions
-   Prove control over cryptographic assets or accounts

## Simple Example

``` text
Private Key
     ↓
Creates Signature
     ↓
Transaction
     ↓
Network
     ↓
Public Key
     ↓
Verifies Signature
```

## Important Rule

> **Never share your private key.**

If another person gets control of your private key, they may be able to
authorize transactions or actions associated with it.

------------------------------------------------------------------------

# 4. Decentralized Network

## Definition

A **decentralized network** is a network in which control and
decision-making are distributed among multiple independent participants
rather than being controlled by a single central authority.

Blockchain networks use multiple computers called **nodes**.

## Centralized vs Decentralized

### Centralized

``` text
       Central Server
       /    |    \
     User User User
```

One central system controls the network.

### Decentralized

``` text
Node ←→ Node
 ↑  \    /  ↑
 ↓   \  /   ↓
Node ←→ Node
```

Multiple nodes communicate and maintain the network.

## Advantages

-   No single point of control
-   Better resistance to failure of one node
-   Network can continue operating when individual nodes fail
-   Can reduce dependence on a central authority

## Challenges

-   Consensus can be difficult
-   Communication between many nodes creates overhead
-   Performance and scalability can be challenging

------------------------------------------------------------------------

# 5. Permissioned Distributed Ledger

## Definition

A **permissioned distributed ledger** is a distributed ledger in which
only authorized participants can join the network or perform specific
activities.

Unlike an open public blockchain, participation is controlled.

## Example

Suppose five banks share a ledger:

``` text
Bank A ─┐
Bank B ─┤
Bank C ─┼── Permissioned Ledger
Bank D ─┤
Bank E ─┘
```

Only approved banks can participate.

## Features

-   Authorized users
-   Identity-based access
-   Controlled participation
-   Greater privacy
-   Suitable for organizations
-   Can provide high performance depending on design

## Uses

-   Banking
-   Supply chains
-   Healthcare
-   Government
-   Inter-company data sharing

------------------------------------------------------------------------

# 6. Digital Identification and Wallets

## Digital Wallet

A **digital wallet** is software or hardware that manages cryptographic
keys and allows users to interact with blockchain networks.

A wallet may contain or manage:

-   Private keys
-   Public keys
-   Addresses
-   Transaction information
-   Digital assets or credentials

## Important Concept

> A blockchain wallet does not usually "store coins" in the same way a
> physical wallet stores cash. The blockchain records ownership/control
> information, while the wallet manages the keys used to access and
> authorize transactions.

## Types of Wallets

### Hot Wallet

Connected to the internet.

Examples:

-   Mobile wallet
-   Browser wallet
-   Desktop wallet

### Cold Wallet

Kept offline or isolated from the internet for stronger protection
against some online threats.

Examples:

-   Hardware wallet
-   Offline storage

## Wallet + Digital Identity

A wallet can be used to manage:

``` text
Private Key
Public Key
Digital Credentials
Blockchain Addresses
Digital Assets
```

------------------------------------------------------------------------

# 7. Blockchain Data Structure

## Definition

A blockchain stores records in a sequence of blocks.

Each block is linked to the previous block using cryptographic
information, typically including a hash.

``` text
Block 1 → Block 2 → Block 3 → Block 4
```

## Typical Block Structure

A block can contain:

### Block Header

Common fields include:

-   Previous block hash
-   Timestamp
-   Merkle root
-   Consensus-related information such as a nonce in proof-of-work
    systems

### Block Body

Contains:

-   Transactions
-   Other protocol-specific data

## Previous Block Hash

The previous block's hash helps connect the blocks.

If data in an earlier block is changed, its hash changes, which can
break the expected chain relationship.

------------------------------------------------------------------------

# 8. Merkle Tree

A **Merkle tree** is a tree structure used to efficiently summarize and
verify a large set of transactions or data items.

## Structure

``` text
             Merkle Root
             /         \
          Hash AB      Hash CD
          /   \        /   \
       Hash A Hash B Hash C Hash D
          ↓     ↓      ↓     ↓
         TX1   TX2    TX3   TX4
```

The final top hash is called the **Merkle root**.

## Advantages

-   Efficient transaction verification
-   Compact summary of many transactions
-   Helps detect data changes
-   Reduces the amount of information needed for certain proofs

------------------------------------------------------------------------

# 9. Double Spending

## Definition

**Double spending** is an attempt to spend the same digital currency or
asset more than once.

## Example

Suppose Ankit has 1 digital coin.

He tries to send the same 1 coin to:

``` text
Transaction 1 → Rahul
Transaction 2 → Amit
```

Both transactions cannot legitimately spend the same available unit.

## How Blockchain Prevents Double Spending

Blockchain systems use mechanisms such as:

-   Consensus
-   Transaction ordering
-   Validation rules
-   Cryptographic signatures
-   Confirmation/finality mechanisms

The network determines which valid transaction is included in the
accepted ledger history.

## Exam Definition

> Double spending is the fraudulent or conflicting attempt to use the
> same digital asset in more than one transaction.

------------------------------------------------------------------------

# 10. Network Consensus

## Definition

**Consensus** is the process by which distributed network participants
agree on the valid state or history of the blockchain.

In simple words:

> **Consensus helps independent nodes agree on which transactions and
> blocks should be accepted.**

## Why is Consensus Needed?

There is no single central server deciding everything in a decentralized
blockchain.

Therefore, nodes need rules to agree on:

-   Valid transactions
-   Valid blocks
-   Transaction order
-   The accepted chain/state

## Examples of Consensus Mechanisms

-   Proof of Work (PoW)
-   Proof of Stake (PoS)
-   Practical Byzantine Fault Tolerance (PBFT)
-   Proof of Authority (PoA)

------------------------------------------------------------------------

# 11. Sybil Attack

## Definition

A **Sybil attack** occurs when an attacker creates or controls many fake
identities or nodes in a network to gain disproportionate influence.

## Example

Suppose a network has:

``` text
100 genuine nodes
```

An attacker creates:

``` text
10,000 fake nodes
```

If the system simply counted identities, the attacker could gain
excessive influence.

## Prevention

Blockchain networks can use mechanisms such as:

-   Proof of Work
-   Proof of Stake
-   Identity-based permission systems
-   Resource or economic costs for participation

## Exam Definition

> A Sybil attack is an attack in which one entity creates multiple fake
> identities or nodes to gain influence over a distributed network.

------------------------------------------------------------------------

# 12. Block Rewards and Miners

## Block Reward

A **block reward** is an incentive given to participants who
successfully perform the required work to add a valid block, depending
on the blockchain's consensus rules.

In Bitcoin's proof-of-work system, miners receive a block subsidy and
applicable transaction fees.

## Miners

**Miners** are participants in proof-of-work blockchains who use
computational power to solve the network's consensus puzzle and propose
valid blocks.

## Basic Process

``` text
Transactions
     ↓
Miner collects transactions
     ↓
Performs Proof of Work
     ↓
Valid Block
     ↓
Network Verification
     ↓
Block Added
     ↓
Reward + Fees
```

## Why Rewards are Important

Rewards can:

-   Incentivize participation
-   Encourage miners to provide computational resources
-   Help maintain network security
-   Encourage honest participation under the protocol's economic model

------------------------------------------------------------------------

# 13. Forks

## Definition

A **fork** occurs when the blockchain's rules or chain history diverge.

Forks can be broadly divided into:

1.  Soft Fork
2.  Hard Fork

------------------------------------------------------------------------

## 13.1 Soft Fork

A **soft fork** is a protocol rule change that is generally
backward-compatible with older software under the relevant consensus
rules.

It can make previously valid blocks or transactions invalid under the
new rules.

## 13.2 Hard Fork

A **hard fork** is a protocol rule change that is not
backward-compatible with the old rules.

If participants do not upgrade, the network can split into different
chains.

## Comparison

  -----------------------------------------------------------------------
  Feature                 Soft Fork               Hard Fork
  ----------------------- ----------------------- -----------------------
  Compatibility           Generally               Not backward-compatible
                          backward-compatible     

  Rule change             More restrictive rules  Can introduce
                                                  incompatible rules

  Chain split             Not necessarily         Can result in a
                                                  permanent split
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 14. Consensus Chain

## Definition

A **consensus chain** is the accepted blockchain history determined by
the network's consensus rules.

Nodes use protocol rules to decide which chain or state should be
accepted.

## In Proof of Work

A node may follow the valid chain with the greatest accumulated
proof-of-work, according to the protocol's chain-selection rule.

## Why It Matters

It helps nodes agree on:

-   Transaction history
-   Block order
-   Current ledger state

------------------------------------------------------------------------

# 15. Sharding

## Definition

**Sharding** is a blockchain scalability technique that divides the
network's workload or state into smaller sections called **shards**.

Instead of every participant processing every operation, different parts
of the network can handle different subsets of work, depending on the
protocol.

## Simple Example

Without sharding:

``` text
All nodes
   ↓
Process all transactions
```

With sharding:

``` text
Transactions
      ↓
 ┌────┼────┐
 ↓    ↓    ↓
Shard 1 Shard 2 Shard 3
```

## Advantages

-   Can increase transaction processing capacity
-   Can reduce the amount of work each participating node must handle
-   Can improve scalability

## Security Consideration

Sharding must be carefully designed to prevent attacks such as an
attacker concentrating control over a particular shard.

Blockchain protocols can use techniques such as **random validator
assignment** and cross-shard security mechanisms to reduce these risks.

------------------------------------------------------------------------

# 16. Finality

## Definition

**Finality** means the point at which a blockchain transaction or state
is considered sufficiently irreversible under the protocol's rules.

In simple words:

> **Finality tells us when a transaction can be treated as permanently
> accepted.**

## Types of Finality

### Probabilistic Finality

A transaction becomes increasingly difficult to reverse as more blocks
are added.

This is associated with many Nakamoto-style proof-of-work systems.

### Deterministic / Economic Finality

The protocol can provide a stronger rule that marks a block or state as
finalized once specific consensus conditions are met.

This is common in many proof-of-stake or Byzantine fault-tolerant
designs.

## Importance

Finality is important for:

-   Payments
-   Smart contracts
-   Asset transfers
-   Business applications

------------------------------------------------------------------------

# 17. Limitations of Proof of Work

## Definition of Proof of Work

**Proof of Work (PoW)** is a consensus mechanism in which participants
compete using computational work to propose valid blocks.

Bitcoin uses PoW.

## Limitations

### 1. High Energy Consumption

Mining can require significant electricity, especially in large
competitive networks.

### 2. Hardware Requirements

Competitive mining can require specialized hardware.

### 3. Lower Throughput

Many PoW blockchains process transactions at a limited rate compared
with some alternative designs.

### 4. Confirmation Time

Users may need to wait for additional blocks for stronger confidence in
a transaction's acceptance.

### 5. Mining Centralization Risks

Mining can become concentrated among participants with access to large
amounts of hardware, electricity, or capital.

### 6. Environmental Concerns

When mining uses carbon-intensive electricity, it can create
environmental concerns.

------------------------------------------------------------------------

# 18. Alternatives to Proof of Work

There are several alternatives to PoW.

## 18.1 Proof of Stake (PoS)

Validators lock or stake cryptocurrency according to the protocol's
rules.

The protocol selects validators to propose and/or attest to blocks.

### Advantages

-   Usually much lower energy consumption than PoW
-   Does not require large-scale mining hardware
-   Can support strong economic security

------------------------------------------------------------------------

## 18.2 Proof of Authority (PoA)

A limited set of approved validators are responsible for validating
blocks.

### Suitable For

-   Permissioned networks
-   Enterprise systems
-   Networks where validator identities are known

### Advantage

-   Fast and efficient

### Limitation

-   More centralized than open permissionless systems

------------------------------------------------------------------------

## 18.3 Proof of History (PoH)

Proof of History is a cryptographic time-ordering technique used in the
Solana ecosystem.

It helps establish an efficient ordering of events and is used together
with other consensus components.

------------------------------------------------------------------------

## 18.4 Practical Byzantine Fault Tolerance (PBFT)

PBFT is a consensus approach designed for networks where participants
may include known or authenticated nodes and some nodes may behave
incorrectly or maliciously.

It is particularly useful in permissioned distributed systems.

------------------------------------------------------------------------

# 19. PoW vs PoS

  --------------------------------------------------------------------------
  Feature                   Proof of Work            Proof of Stake
  ------------------------- ------------------------ -----------------------
  Main resource             Computing power          Staked assets

  Validators/participants   Miners                   Validators

  Energy use                Generally high           Generally much lower

  Hardware                  Mining hardware can be   Specialized mining
                            required                 hardware not required

  Attack cost               Computational/economic   Economic stake and
                                                     protocol penalties

  Example                   Bitcoin                  Ethereum
  --------------------------------------------------------------------------

------------------------------------------------------------------------

# 20. Important Exam Differences

## Public vs Permissioned

  Public                   Permissioned
  ------------------------ --------------------------
  Open participation       Authorized participation
  Usually permissionless   Permission required
  Greater openness         Greater access control
  Example: Bitcoin         Example: enterprise DLT

## Private Blockchain vs Permissioned Ledger

-   **Private blockchain** usually refers to a blockchain controlled by
    a particular organization.
-   **Permissioned ledger** refers to a ledger where participation or
    activities require authorization.
-   A permissioned ledger can be controlled by **one organization or
    multiple organizations**.

## Soft Fork vs Hard Fork

-   **Soft fork** → generally backward-compatible rule change.
-   **Hard fork** → incompatible rule change that can result in a chain
    split.

## PoW vs PoS

-   **PoW** → security through computational work.
-   **PoS** → security through economic stake and validator rules.

------------------------------------------------------------------------

# 21. Important Short Questions

## Q1. What is distributed identity?

> Distributed identity is an identity model in which users can control
> and use digital identity information across services without relying
> completely on a single central identity provider.

## Q2. What is a public key?

> A public key is a cryptographic key that can be shared and can be used
> for functions such as signature verification.

## Q3. What is a private key?

> A private key is a secret cryptographic key used for functions such as
> creating digital signatures and authorizing transactions.

## Q4. What is double spending?

> Double spending is an attempt to spend the same digital asset more
> than once.

## Q5. What is consensus?

> Consensus is the process by which distributed participants agree on
> the valid blockchain state or history.

## Q6. What is a Sybil attack?

> A Sybil attack occurs when an attacker creates multiple fake
> identities or nodes to gain disproportionate influence in a network.

## Q7. What are miners?

> Miners are participants in proof-of-work blockchains who use
> computational work to propose and validate blocks according to the
> protocol.

## Q8. What is a fork?

> A fork is a divergence in blockchain protocol rules or chain history.

## Q9. What is finality?

> Finality is the point at which a transaction or blockchain state is
> considered sufficiently irreversible according to the protocol.

## Q10. What is sharding?

> Sharding is a scalability technique that divides blockchain workload
> or state into smaller sections so that different parts can process
> different work.

## Q11. Give two limitations of Proof of Work.

> High energy consumption and the need for substantial computational
> resources are two major limitations of Proof of Work.

## Q12. Give two alternatives to Proof of Work.

> Proof of Stake and Proof of Authority are examples of alternatives to
> Proof of Work.

------------------------------------------------------------------------

# 22. One-Line Revision

``` text
Distributed Identity → User-controlled digital identity
Digital Identification → Identifying/verifying entities digitally
Public Key → Can be shared; used for verification and other public-key functions
Private Key → Secret; used to sign/authorize
Decentralization → Control distributed among multiple nodes
Permissioned DLT → Only authorized participants
Wallet → Manages cryptographic keys and blockchain interactions
Double Spending → Spending the same digital asset twice
Consensus → Agreement on valid blockchain state/history
Sybil Attack → Many fake identities controlled by one attacker
Miner → PoW participant that performs computational work
Block Reward → Incentive for block production under protocol rules
Fork → Divergence in rules or chain history
Sharding → Divides workload/state for scalability
Finality → Point of sufficient/defined irreversibility
PoW → Consensus based on computational work
PoS → Consensus based on economic stake
PoA → Consensus using approved/authorized validators
PBFT → Byzantine fault-tolerant consensus approach
```

------------------------------------------------------------------------

# 23. Last-Minute Exam Revision

Remember these:

1.  **Private Key = Secret**
2.  **Public Key = Shareable**
3.  **Consensus = Agreement**
4.  **Double Spending = Same asset spent twice**
5.  **Sybil Attack = Fake identities**
6.  **Miner = PoW participant**
7.  **Fork = Chain/rule divergence**
8.  **Sharding = Divide workload**
9.  **Finality = Accepted and sufficiently irreversible state**
10. **PoW = Computing power**
11. **PoS = Stake**
12. **PoA = Approved validators**
13. **Permissioned = Authorized access**
14. **Wallet = Manages keys, not physical coins**

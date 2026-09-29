# Unit 1 --- Blockchain and Distributed Ledger Fundamentals

> **Exam-focused notes:** Simple language, definitions, key points,
> examples, and differences.

------------------------------------------------------------------------

# 1. Blockchain

## Definition

A **blockchain** is a distributed digital ledger that records
transactions or data in a sequence of blocks. Each block is connected to
the previous block using cryptographic techniques.

In simple words:

> **Blockchain is a shared digital record book in which data is stored
> in connected blocks and is difficult to change once recorded.**

## Why is it called Blockchain?

It is called a **blockchain** because:

-   Data is grouped into **blocks**.
-   Every block is connected to the previous block.
-   Cryptographic hashes are used to link the blocks.
-   Together, the blocks form a **chain**.

### Simple Structure

``` text
Block 1 → Block 2 → Block 3 → Block 4
```

Each block generally contains:

-   Transaction/data information
-   Timestamp
-   Previous block hash
-   Its own hash
-   Other information required by the blockchain protocol

## Main Features

### 1. Decentralization

There is generally no single central authority controlling a public
blockchain.

### 2. Transparency

On many public blockchains, transactions can be viewed by participants.

### 3. Immutability

Once data is confirmed and recorded, changing it is difficult because
later blocks depend on earlier blocks.

### 4. Security

Cryptographic hashing, digital signatures, and consensus mechanisms help
protect the network.

### 5. Distribution

Copies of the ledger are maintained by multiple computers called
**nodes**.

## Example

Bitcoin uses blockchain technology to maintain a distributed record of
cryptocurrency transactions.

------------------------------------------------------------------------

# 2. Distributed Ledger Technology (DLT)

## Definition

**Distributed Ledger Technology (DLT)** is a technology in which a
ledger containing records is distributed among multiple participants or
computers.

> **DLT is the broader concept; blockchain is one type of DLT.**

## Blockchain vs DLT

  -----------------------------------------------------------------------
  Blockchain                          DLT
  ----------------------------------- -----------------------------------
  A type of distributed ledger        Broader technology

  Usually stores records in linked    Does not necessarily use blocks
  blocks                              

  Uses a chain-like structure         Can use other data structures

  Example: Bitcoin                    Blockchain and other distributed
                                      ledger systems
  -----------------------------------------------------------------------

## Important Point

**All blockchains are DLTs, but not all DLTs are blockchains.**

------------------------------------------------------------------------

# 3. Growth of Blockchain Technology

Blockchain technology has developed through several stages.

## Stage 1 --- Cryptographic Foundations

Before blockchain, researchers developed important cryptographic
concepts such as:

-   Hash functions
-   Public-key cryptography
-   Digital signatures
-   Merkle trees

These concepts became building blocks for later blockchain systems.

## Stage 2 --- Bitcoin

In **2008**, the Bitcoin whitepaper introduced a peer-to-peer electronic
cash system.

In **2009**, the Bitcoin network became operational.

Bitcoin demonstrated how a decentralized network could maintain a shared
transaction history without depending on a traditional central
authority.

## Stage 3 --- Smart Contracts and Ethereum

Ethereum expanded blockchain use beyond simple payments.

It introduced programmable **smart contracts**, allowing applications
and agreements to run using blockchain-based programs.

## Stage 4 --- Enterprise Blockchain

Organizations began exploring permissioned blockchain platforms for
applications such as:

-   Supply chain management
-   Banking
-   Healthcare
-   Identity management
-   Record sharing

Examples include **Hyperledger Fabric** and **Corda**.

## Stage 5 --- Modern Blockchain Ecosystem

Blockchain technology is now associated with areas such as:

-   Cryptocurrencies
-   Smart contracts
-   Decentralized applications (DApps)
-   Tokens
-   Decentralized finance (DeFi)
-   Digital assets
-   Enterprise applications

------------------------------------------------------------------------

# 4. Cryptographic Basics for Cryptocurrency

Cryptography is essential for protecting blockchain systems.

It helps provide:

-   Security
-   Authentication
-   Data integrity
-   Confidentiality where encryption is used
-   Ownership/control through cryptographic keys

The important cryptographic concepts for cryptocurrency are:

1.  Hashing
2.  Digital signatures
3.  Encryption
4.  Public and private keys

------------------------------------------------------------------------

# 5. Hashing

## Definition

A **hash function** converts input data of arbitrary size into a
fixed-length output called a **hash** or **digest**.

``` text
Data
  ↓
Hash Function
  ↓
Fixed-length Hash
```

## Example

``` text
"Hello"
   ↓
Hash Function
   ↓
A unique-looking hash value
```

Even a small change in the input normally produces a very different
hash.

## Important Properties

A cryptographic hash function should provide:

-   **One-way property** --- it should be computationally difficult to
    recover the original input from the hash.
-   **Deterministic output** --- the same input produces the same hash.
-   **Collision resistance** --- finding two different inputs with the
    same hash should be computationally difficult.
-   **Avalanche effect** --- a small input change can produce a
    significantly different hash.

## Uses in Blockchain

Hashing is used for:

-   Linking blocks
-   Identifying data
-   Maintaining data integrity
-   Merkle trees
-   Supporting proof-of-work in applicable blockchains

------------------------------------------------------------------------

# 6. Digital Signature Scheme

## Definition

A **digital signature scheme** is a cryptographic technique used to
prove that a transaction was authorized by the holder of a private key
and that the signed data has not been changed.

## Main Components

### Private Key

A secret key that must be kept safe by its owner.

### Public Key

A key that can be shared and is used to verify signatures.

### Digital Signature

A cryptographic value created using the private key.

## Basic Process

``` text
Transaction
     ↓
Hash / Signing Process
     ↓
Private Key
     ↓
Digital Signature
     ↓
Network
     ↓
Public Key
     ↓
Signature Verification
```

## Main Purposes

### Authentication

Helps verify that the transaction was authorized by the holder of the
private key.

### Integrity

Helps detect whether signed data has been changed.

### Non-repudiation

Provides cryptographic evidence associated with the signing key,
although legal meaning can depend on the system and jurisdiction.

## Simple Example

If Ankit owns a cryptocurrency account, he uses his **private key** to
authorize a transaction. Other network participants can use the
corresponding **public key** to verify the signature.

## Exam Definition

> A digital signature is a cryptographic mechanism that uses a private
> key to sign data and a corresponding public key to verify the
> signature.

## Easy Rule

``` text
Private Key → Sign
Public Key  → Verify
```

------------------------------------------------------------------------

# 7. Encryption Schemes

## Definition

**Encryption** is the process of converting readable data
(**plaintext**) into an unreadable form (**ciphertext**) using an
encryption algorithm and a key.

``` text
Plaintext
    ↓
Encryption + Key
    ↓
Ciphertext
    ↓
Decryption + Key
    ↓
Plaintext
```

The main purpose of encryption is **confidentiality**.

------------------------------------------------------------------------

## 7.1 Symmetric Encryption

In symmetric encryption, the **same secret key** is used for encryption
and decryption.

``` text
Plaintext
   ↓
Encryption
   ↓
Secret Key
   ↓
Ciphertext
   ↓
Decryption
   ↓
Same Secret Key
   ↓
Plaintext
```

### Examples

-   AES
-   DES
-   3DES

### Advantages

-   Fast
-   Efficient for large amounts of data
-   Requires relatively less computational power

### Disadvantage

The secret key must be securely shared between the communicating
parties.

------------------------------------------------------------------------

## 7.2 Asymmetric Encryption

Asymmetric cryptography uses a **key pair**:

-   Public key
-   Private key

A public key can be shared, while the private key must remain secret.

``` text
Plaintext
   ↓
Encryption
   ↓
Receiver's Public Key
   ↓
Ciphertext
   ↓
Decryption
   ↓
Receiver's Private Key
   ↓
Plaintext
```

### Examples

-   RSA
-   ECC
-   ElGamal

### Advantages

-   Avoids directly sharing one secret encryption key
-   Useful for secure communication and key exchange

### Disadvantage

-   Generally slower than symmetric encryption
-   Requires more computational resources

## Important Difference

> **Encryption mainly provides confidentiality, while digital signatures
> mainly provide authentication and integrity.**

------------------------------------------------------------------------

# 8. Categories of Blockchain

Blockchain networks can be categorized according to **access,
permission, control, and the type of assets/data handled**.

The topics in this syllabus are:

1.  Public Blockchain
2.  Private Blockchain
3.  Permissioned Ledger
4.  Tokenized Blockchain
5.  Tokenless Blockchain

------------------------------------------------------------------------

# 9. Public Blockchain

## Definition

A **public blockchain** is a blockchain that is generally open for
anyone to access and participate in according to its protocol rules.

It is usually **permissionless**, meaning a central organization does
not have to approve every participant.

## Features

-   Open participation
-   High transparency
-   Distributed control
-   Anyone can generally verify the public ledger
-   Uses a consensus mechanism
-   No single organization normally controls the entire network

## Examples

-   Bitcoin
-   Ethereum

## Advantages

-   High transparency
-   Open participation
-   Strong decentralization
-   No single central authority

## Disadvantages

-   Can have scalability limitations
-   Transaction processing can be slower depending on the consensus
    mechanism and network load
-   Public visibility may reduce privacy

------------------------------------------------------------------------

# 10. Private Blockchain

## Definition

A **private blockchain** is a blockchain where access is restricted and
controlled by a particular organization or authority.

Only approved participants can join or perform certain activities.

## Features

-   Restricted access
-   Controlled by an organization or authority
-   Higher privacy
-   Faster processing may be possible
-   Participants are identified or approved

## Example

An organization can use a private blockchain to share records between
its departments.

## Advantages

-   Better access control
-   Greater privacy
-   Faster processing can be achieved in many designs
-   Suitable for enterprise use

## Disadvantages

-   More centralized than a public blockchain
-   Requires trust in the controlling organization
-   Less open participation

------------------------------------------------------------------------

# 11. Permissioned Ledger

## Definition

A **permissioned ledger** is a distributed ledger where participation
and access to specific functions are restricted to authorized users.

In simple words:

> **Only approved users can participate in the network or perform
> particular actions.**

## Important Point

A permissioned ledger is a **permission-based model**, not simply
another word for private blockchain.

A permissioned network can be controlled by:

-   One organization
-   Several organizations

## Features

-   Identity-based access
-   Authorized participants
-   Access control
-   Greater privacy
-   Suitable for business and enterprise applications

## Example

A group of banks can operate a shared ledger where only approved banks
can validate and submit transactions.

## Advantages

-   Better privacy
-   Controlled participation
-   Easier regulatory and organizational control
-   Efficient for enterprise environments

------------------------------------------------------------------------

# 12. Tokenized Blockchain

## Definition

A **tokenized blockchain** is a blockchain ecosystem in which digital
tokens are used to represent value, rights, assets, or utility.

A token can represent:

-   Digital currency
-   Ownership or claims
-   Utility
-   Access rights
-   Real-world assets represented digitally

## Examples

-   Cryptocurrency tokens
-   Stablecoins
-   Utility tokens
-   Tokenized real-world assets

## Basic Idea

``` text
Real-world value / Digital value
          ↓
       Token
          ↓
      Blockchain
          ↓
Transfer / Ownership / Access
```

## Advantages

-   Digital representation of assets
-   Easy transfer through blockchain transactions
-   Programmability through smart contracts
-   Can enable fractional ownership in some applications

## Example

A company can represent a digital asset or a claim on an asset using
blockchain-based tokens.

------------------------------------------------------------------------

# 13. Tokenless Blockchain

## Definition

A **tokenless blockchain** is a blockchain or distributed ledger system
that does not require a native cryptocurrency/token as the main
mechanism for its operation.

Its primary purpose may be maintaining shared records rather than
transferring a native digital currency.

## Features

-   No required native cryptocurrency
-   Focus on data or record sharing
-   Can use permissioned access
-   Suitable for enterprise applications
-   Participants may be known entities

## Example

An enterprise network can use a distributed ledger to share supply-chain
records without requiring a publicly traded native token.

## Advantages

-   No need to manage a native cryptocurrency
-   Useful for business applications
-   Can provide controlled access
-   Easier to design around organizational processes

------------------------------------------------------------------------

# 14. Public vs Private Blockchain

  Feature        Public Blockchain        Private Blockchain
  -------------- ------------------------ --------------------------
  Access         Open                     Restricted
  Permission     Usually permissionless   Permissioned
  Control        Distributed              Usually one organization
  Transparency   High                     Controlled
  Privacy        Relatively lower         Higher
  Participants   Open                     Approved users
  Example        Bitcoin, Ethereum        Enterprise blockchain

------------------------------------------------------------------------

# 15. Public vs Permissioned Ledger

  -----------------------------------------------------------------------
  Feature                 Public Blockchain       Permissioned Ledger
  ----------------------- ----------------------- -----------------------
  Participation           Generally open          Restricted

  Identity                May be pseudonymous     Usually known/managed

  Access                  Open                    Authorized

  Control                 Distributed             One or more
                                                  organizations

  Typical Use             Cryptocurrency, open    Enterprise/business
                          networks                networks
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 16. Tokenized vs Tokenless Blockchain

  -----------------------------------------------------------------------
  Feature                 Tokenized               Tokenless
  ----------------------- ----------------------- -----------------------
  Native/issued tokens    Used                    Not required

  Main purpose            Value, rights, assets,  Shared records/data
                          utility                 

  Payments                Can use tokens          May use conventional
                                                  payment systems

  Common use              Crypto, digital assets, Enterprise records
                          DeFi                    

  Example                 Token-based blockchain  Enterprise distributed
                          applications            ledger without a native
                                                  token
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 17. Important Exam Questions

## Short Questions

### Q1. What is blockchain?

> Blockchain is a distributed digital ledger that stores records in
> linked blocks using cryptographic techniques.

### Q2. What is DLT?

> Distributed Ledger Technology is a technology that distributes a
> shared ledger among multiple participants. Blockchain is one type of
> DLT.

### Q3. What is a digital signature?

> A digital signature is a cryptographic mechanism that uses a private
> key to sign data and a public key to verify the signature.

### Q4. What is encryption?

> Encryption converts plaintext into ciphertext so that unauthorized
> users cannot understand the protected data.

### Q5. What is a public blockchain?

> A public blockchain is an open blockchain where anyone can generally
> participate according to the network rules.

### Q6. What is a private blockchain?

> A private blockchain is a restricted blockchain controlled by an
> organization or authority.

### Q7. What is a permissioned ledger?

> A permissioned ledger allows only authorized participants to access or
> perform specific activities on the network.

### Q8. What is a tokenized blockchain?

> A tokenized blockchain uses digital tokens to represent value, assets,
> rights, or utility.

### Q9. What is a tokenless blockchain?

> A tokenless blockchain does not require a native cryptocurrency or
> token as the main mechanism of the network.

------------------------------------------------------------------------

# 18. One-Line Revision

``` text
Blockchain      → Linked blocks containing distributed records
DLT             → Distributed shared ledger technology
Hashing         → Data → fixed-length hash
Digital Sign.   → Private key signs, public key verifies
Encryption      → Plaintext → Ciphertext
Public          → Open participation
Private         → Controlled by one organization
Permissioned    → Only authorized participants
Tokenized       → Uses digital tokens
Tokenless       → No required native token
```

------------------------------------------------------------------------

# 19. Most Important Points for Exam

Remember these five differences:

1.  **Blockchain vs DLT**
    -   Blockchain is a type of DLT.
2.  **Hashing vs Encryption**
    -   Hashing is generally one-way.
    -   Encryption is designed to be reversible using the appropriate
        key.
3.  **Encryption vs Digital Signature**
    -   Encryption → Confidentiality.
    -   Digital signature → Authentication and integrity.
4.  **Public vs Private**
    -   Public → Open participation.
    -   Private → Restricted participation.
5.  **Tokenized vs Tokenless**
    -   Tokenized → Uses tokens.
    -   Tokenless → No required native token.

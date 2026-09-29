# Digital Signature Scheme in Blockchain

## Definition

A **digital signature scheme** in blockchain is a cryptographic technique used to prove that a transaction or message was created by the **actual owner of a private key** and has **not been modified**.

## Main Components

A digital signature scheme uses three main components:

1. **Private Key**
   - A secret key kept only by the owner.
   - Used to create the digital signature.

2. **Public Key**
   - Can be shared with others.
   - Used to verify the digital signature.

3. **Digital Signature**
   - Generated using the private key.
   - Proves that the transaction was authorized by the private-key holder.

## How Digital Signature Works

Suppose Ankit wants to send cryptocurrency to Rahul.

```text
Transaction
     ↓
Hash the Transaction
     ↓
Sign the Hash using Private Key
     ↓
Digital Signature
     ↓
Broadcast to Blockchain Network
     ↓
Verification using Public Key
     ↓
Valid / Invalid

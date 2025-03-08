---
title: "Ethereum Unpacked"
date: 2025-03-08
---
# How Ethereum Works Practically

Currently, I am taking a course on blockchain technology, and one of the topics I am studying concerns the state-of-the-art of well-known systems, such as Bitcoin, Cosmos, and Hyperledger Fabric. In upcoming posts, I will dive deeper into each of these technologies, but today I want to focus on Ethereum and its practical functioning.

## Prerequisites for Understanding This Article

To follow this in-depth explanation, you should be familiar with some fundamental concepts:

- The basic structure of a blockchain.
- The block election mechanism in a blockchain.
- The main challenges related to blockchain and their solutions (e.g., double-spending, 51% attack, consensus, etc.).
- Basic cryptographic techniques for ensuring authentication and integrity (such as digital signatures).

## What is Ethereum?

Ethereum can be seen as a large, deterministic state machine whose state changes over time based on the operations performed. The "state" refers to the current condition of the network, while "deterministic" means that, given the same initial conditions and performed operations, the same result will always be obtained.

The state of the Ethereum network is a "singleton," meaning there is a single state shared by the entire network. Each node keeps a copy of this state and updates it based on transactions and blocks added to the blockchain.

## Differences Between Bitcoin and Ethereum

Bitcoin was created with the primary goal of being a decentralized digital currency, whereas Ethereum was designed to offer a platform for running decentralized programs.

Ethereum’s native cryptocurrency, ether (ETH), is not intended exclusively as a medium of payment but also acts as "fuel" for executing code on the blockchain.

Another key difference is the programming language: Bitcoin uses a deliberately limited language to avoid the creation of complex programs. Ethereum, on the other hand, allows the execution of more sophisticated programs through Solidity, a Turing-complete language, meaning it can perform any type of computation.

## Ethereum Accounts

Ethereum has two main types of accounts:

1. **Externally-Owned Accounts (EOA):** Controlled by a user who holds the private key.
2. **Contract Accounts:** Controlled by the code of a smart contract. These accounts cannot initiate transactions autonomously but can respond to transactions received from EOAs.

## Smart Contracts
Smart contracts are programs that execute automatically when certain conditions are met. They consist of code (functions) and data (state) and reside at a specific address on the blockchain.

Here’s a simple example of a smart contract written in Solidity:

```pragma solidity ^0.8.0;

contract Counter {
    uint public count;

    function increment() public {
        count += 1;  
    }

    function getCount() public view returns (uint) {
        return count;  
    }
}
```
Users can interact with this contract via transactions, modifying its state.

Creating a smart contract incurs a cost, as it uses storage space on the blockchain. Additionally, executing functions in a smart contract requires the user to pay a fee in ETH called "gas."

## Transactions on Ethereum

A transaction on Ethereum can be used to send ETH, transfer tokens, or interact with smart contracts. Each transaction contains information such as the sender, the receiver, the value transferred, and the digital signature.

There are three main types of transactions:

- **Regular**: Sending ETH between two accounts.
- **Contract deployment**: Creating a new smart contract on the blockchain.
- **Execution**: Interacting with an already deployed smart contract.

## The Concept of Gas

Gas measures the amount of computational work required to execute a transaction or function on Ethereum. Each operation has a gas cost, which is paid in ETH.

The gas cost depends on the complexity of the operation and network congestion. Two key parameters control this:

- **Gas limit**: The maximum amount of gas the user is willing to pay.
- **Gas price**: The cost per unit of gas, determined by the market.

If a transaction doesn’t have enough gas, the operation fails, but the gas spent up to that point is not refunded.

## Ethereum Virtual Machine (EVM)

The EVM is the execution environment for smart contracts on Ethereum. Every node in the network runs a copy of the EVM and uses it to validate transactions.

Gas is used to measure the computational power required for each operation within the EVM.

## Consensus on Ethereum: Proof of Stake (PoS)

Ethereum switched from Proof of Work (PoW) to Proof of Stake (PoS) in 2022, adopting a more efficient and sustainable consensus mechanism.

Validators are responsible for adding new blocks to the blockchain. To become a validator, a user must deposit 32 ETH into a dedicated smart contract (deposit contract). Validators:

- Propose new blocks of transactions.
- Validate blocks proposed by others by re-executing the transactions and ensuring blockchain consistency.

## Transaction Finality

Ethereum uses a supermajority mechanism to validate blocks. A block is considered final when at least 2/3 of validators attest to its validity. After about 12.8 minutes, the block becomes immutable.

The consensus system is managed by the **Beacon Chain**, which randomly selects validators responsible for creating and verifying blocks.


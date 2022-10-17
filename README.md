---
description: 'Getting started with understanding Diamond Standard: EIP-2535'
---

# Introduction To Diamonds

It is a common knowledge that the blockchain is an immutable digital ledger of transactions which implies that once a smart contract is deployed, it can not be modified that is why we have test networks where you make all your necessary testing before deploying to mainnet.

Let's look at a scenario where a developer discovers a bug in a contract that is being used and holds a large amount of funds, that bug can't be fixed because of the immutable nature of the blockchain, hence the need for smart contract upgradability became pertinent.

Let's look at another scenario where you have a smart contract with a large codebase (many lines of code) or possibly a smart contract that inherited many other contracts. When compiling such contract it may fail to compile because the size exceeds the contract size limit which is 24KB. This limitation is not possible when using the Diamond Standard because contracts are separated as facets (individual contracts) and the functions they contain are called from one main/parent contract called the Diamond contract.

#### What is Diamond?

A diamond is a contract with external functions that are supplied by contracts called facets. While facets are separate, independent contracts that can store internal functions, libraries and state variables.

A diamond contains a fallback function which delegatecall into its facets to execute function calls.

#### Fallback Function

A fallback function is a function that get triggered when an external function call is made to a contract which doesn't contain the function that was called.

When an external function is called on a diamond, its fallback function is executed. This is because a fallback function is executed when a function call is made on a contract where the function that was called doesn't exist.

The logic in the fallback function determines which facet to call based on the first four bytes of the calldata (known as the function selector) and then it executes that function from the facet using delegatecall.

The power of the diamond is in the fallback function and delegatecall which enables the diamond to execute facet's function as if it was implemented by the diamond itself.

> The msg.sender and msg.value values do not change and only the diamond's storage is read and written to.

#### Delegatecall

Delegatecall is a low level call that enables you to call functions from other contracts, but the state or storage of the calling contract gets updated or set.\
\
Let's say we have two contracts A and B, when contract `A` executes `delegatecall` to contract `B`, contract `B`'s code is executed with contract `A`'s storage, `msg.sender` and `msg.value`. This means, the logic and code execution takes place in contract B, but the storage of contract A get modified.

```
```






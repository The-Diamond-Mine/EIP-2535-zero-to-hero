---
description: >-
  In this section we would be building the NFT facet, this facet would be
  handling all the logic for the NFT operations. The model of NFT we would be
  using is the URLStorage. In this model.
---

# Let's get our hands dirty | NFT facet

In this model, the minter of the NFT would be providing the link to the metadata. We are doing this for flexibility and simplicity.&#x20;

From the previous section, you have been made to understand that when working with a diamond, you have about two options on storage patterns to apply, App Storage and Diamond Storage.

During the course of this implementation, we would be using the NFT contract would be using the App Storage to handle storage and the Marketplace would be handling its storage using Diamond storage.

First, we would be setting up our storage for the NFT contract.

Create a file called AppStorage.sol and a File called Counter.so

The Counter.sol is a library gotten from openzeppelin&#x20;

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
import "./Counter.sol";



struct AppStorage {
    string _name;
    string _symbol;
    mapping(uint256 => address) _owners;
    mapping(address => uint256) _balances;
    mapping(uint256 => address) _tokenApprovals;
    mapping(address => mapping(address => bool)) _operatorApprovals;
    mapping(uint256 => string) _tokenURIs;
    Counters.Counter _myCounter;
    uint256 MAX_SUPPLY;
}
```

So these are all the state variables we would be needing in the NFT facet.


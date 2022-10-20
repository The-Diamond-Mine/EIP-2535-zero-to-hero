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

The Counter.sol is a library gotten from openzeppelin. This would help us handle the counting of minted NFT and token ID.

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

```
// SPDX-License-Identifier: MIT
// OpenZeppelin Contracts v4.4.1 (utils/Counters.sol)

pragma solidity ^0.8.0;

/**
 * @title Counters
 * @author Matt Condon (@shrugs)
 * @dev Provides counters that can only be incremented, decremented or reset. This can be used e.g. to track the number
 * of elements in a mapping, issuing ERC721 ids, or counting request ids.
 *
 * Include with `using Counters for Counters.Counter;`
 */
library Counters {
    struct Counter {
        // This variable should never be directly accessed by users of the library: interactions must be restricted to
        // the library's function. As of Solidity v0.5.2, this cannot be enforced, though there is a proposal to add
        // this feature: see https://github.com/ethereum/solidity/issues/4637
        uint256 _value; // default: 0
    }

    function current(Counter storage counter) internal view returns (uint256) {
        return counter._value;
    }

    function increment(Counter storage counter) internal {
        unchecked {
            counter._value += 1;
        }
    }

    function decrement(Counter storage counter) internal {
        uint256 value = counter._value;
        require(value > 0, "Counter: decrement overflow");
        unchecked {
            counter._value = value - 1;
        }
    }

    function reset(Counter storage counter) internal {
        counter._value = 0;
    }
}
```




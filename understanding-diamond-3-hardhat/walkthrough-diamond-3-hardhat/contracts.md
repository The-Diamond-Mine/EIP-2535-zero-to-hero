---
description: >-
  Here a brief explanation of what each contract contained in this folder does
  would be done.
---

# Contracts

### Diamond.sol

This is the main contract of the diamond and is what I would call the control point. This contract handles storing data, storing ether/native tokens, and delegating the function to the facet that has that logic implemented.

#### Facets

Just as similar to a regular diamond, a diamond has many faces called a facet. The diamond standard also employs this, having facets also like a regular diamond but this time the facet contains related functions

Here is the list of the facet that comes with the diamond 3 hardhat starter template.&#x20;

* DiamondCutFacet: This is the facet that handles upgrades. Basically, this facet holds logic to add, remove or replace functions in a diamond.
* DiamondLoupeFacet: The diamond standard supports transparency, this is achieved using the DiamondLoupeFacet. Using this facet, regular users and developers can very all facets and functions that are implemented in a Diamond.
* OwnershipFacet: This is the facet handling the ownership of the diamond. This is a very important facet because the owner set by this facet would be the only address that can make upgrades.

#### Interfaces

Same as interfaces used in solidity, it also applies here. The interfaces defined in this folder are used as a strict layout for which the facet must be implemented with. All functions, events, custom errors, and so on defined in the interface must be imported by the inheriting facet.

#### Libraries

The diamond 3 hardhat starter template libraries folder houses just one library, LibDiamond. The LibDiamond using the diamond storage pattern holds the logic for storing data related to the diamond. Also in this library, the logic (internal functions/utils functions) used in the diamond cut facet and the ownership facet.

#### DiamondInit&#x20;

It is no new story that contract construction is done differently when it gets to proxies . The diamond uses DiamondInit as a constructor. Logic and state variables needed in the diamond immediately after deployment would be done here in the init function.

####


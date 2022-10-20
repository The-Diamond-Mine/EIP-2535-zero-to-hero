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

Here are the list of the facet that comes with the diamond 3 hardhat starter temeplate.&#x20;

* DiamondCutFacet: This is facet that handles upgrades. Basically these are logic to add, remove or replace functions in a diamond.
*

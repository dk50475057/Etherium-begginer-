# Create a Token in Solidity
# MyToken Smart Contract - README

## Overview

This Solidity contract defines a simple ERC-20-like token named "MyToken" with basic functionalities like minting and burning tokens. It allows users to create and destroy tokens, keeping track of the total supply and balances of individual addresses.

## License
This project is licensed under the MIT License. The full license can be found at the top of the Solidity contract:
```
// SPDX-License-Identifier: MIT
```

## Requirements

1. **Public Variables for Token Details**:
    - The contract includes three public variables that store essential details about the token:
      - `name`: Token Name (set to `"MyToken"`).
      - `symbol`: Token Abbreviation (set to `"MTK"`).
      - `totalSupply`: The total supply of tokens currently in circulation.
  
2. **Mapping of Address to Balances**:
    - A mapping (`balances`) is used to keep track of the balance of each address:
      - `balances[address]`: Stores the token balance for each address.
  
3. **Mint Function**:
    - The `mint()` function takes two parameters:
      - `_to`: The address to which new tokens will be minted.
      - `_value`: The amount of tokens to mint.
    - This function:
      - Increases the `totalSupply` by the `_value`.
      - Increases the balance of the `_to` address by the same amount.

4. **Burn Function**:
    - The `burn()` function takes two parameters:
      - `_from`: The address from which tokens will be burned.
      - `_value`: The amount of tokens to burn.
    - This function:
      - Decreases the `totalSupply` by the `_value`.
      - Reduces the balance of the `_from` address by the same amount.
      - Includes a `require` statement to ensure the balance of `_from` is greater than or equal to `_value` before burning, preventing underflow.

## Functions

### 1. `mint(address _to, uint256 _value)`
- **Description**: Mints new tokens to a specified address.
- **Parameters**:
  - `_to`: The address receiving the minted tokens.
  - `_value`: The number of tokens to be minted.
- **Effects**: Increases the `totalSupply` and the balance of `_to`.

### 2. `burn(address _from, uint256 _value)`
- **Description**: Burns tokens from a specified address.
- **Parameters**:
  - `_from`: The address from which tokens are being burned.
  - `_value`: The number of tokens to burn.
- **Effects**: Decreases the `totalSupply` and the balance of `_from`. Ensures the `_from` address has enough tokens before burning.
- **Revert Condition**: Throws an error if the balance of `_from` is less than `_value`.

## Example Usage

1. **Minting Tokens**:
   - Call the `mint()` function to mint tokens to an address. For example:
     ```solidity
     mint(0x123..., 100);  // Mints 100 tokens to the address 0x123...
     ```

2. **Burning Tokens**:
   - Call the `burn()` function to burn tokens from an address. For example:
     ```solidity
     burn(0x123..., 50);  // Burns 50 tokens from the address 0x123...
     ```

## Security Considerations
- **Access Control**: This contract allows anyone to mint or burn tokens. In a production environment, this should be restricted to authorized users by introducing access control mechanisms like `onlyOwner` or `modifier` statements.
- **Token Supply**: There is no upper limit to the token supply in this contract. Depending on your use case, you may want to introduce a maximum supply.
- **Overflow/Underflow Protection**: The contract uses Solidity 0.8.18, which has built-in protections against overflow and underflow.
## Author
Dilkhush Kumar

## Video Explanation
https://www.loom.com/share/0383939b46db403baffc21c52ccb7b99?sid=162b6504-8584-4ce5-95bd-cb1c82462b7f


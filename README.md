# ERC20

# Pittu ERC20 Token Contract

## Simple Overview

The Pittu ERC20 Token Contract is a simple smart contract that creates an ERC20 token named "PittuPrasanth" with the symbol "PI". It allows the contract owner to mint new tokens and users to burn and transfer tokens.

## Description

This project implements a basic ERC20 token using Solidity and the OpenZeppelin library. The contract, named Pittu, includes functionalities for minting, burning, and transferring tokens. The contract owner (the deployer) has the exclusive right to mint new tokens, while any user can burn their tokens or transfer tokens to other addresses. This contract can be deployed and interacted with using the Remix IDE, making it an excellent educational tool for understanding ERC20 tokens on the Ethereum blockchain.



## Getting Started

Installing

#### Download the Program:

- Open Remix IDE.
- Create a new Solidity file and copy the contract code into it.
- No Modifications Needed:

The contract is ready to be compiled and deployed as is.
Executing Program

### Compile the Contract:

- Open the Solidity file containing the contract code in Remix.
- Select the appropriate compiler version (Solidity 0.8.18 or above).
- Click on the "Compile" button to compile the contract.

### Deploy the Contract:

- Go to the "Deploy & Run Transactions" tab in Remix.
- Select the desired environment (e.g., JavaScript VM, Injected Web3, etc.).
- Click on the "Deploy" button to deploy the contract.
- Interact with the Contract:

- After deployment, use the deployed contract instance to call the mintToken, burnToken, and transferToken functions.
- For mintToken, specify the recipient address and the amount to mint.
- For burnToken, specify your address and the amount to burn.
- For transferToken, specify the recipient address and the amount to transfer.

### Code Explanation

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
```
Explanation: The SPDX-License-Identifier specifies the licensing information. The pragma directive indicates that the code is written for Solidity version 0.8.18. We import the ERC20 implementation from the OpenZeppelin library to leverage its well-tested and secure functionalities.


```solidity
contract Pittu is ERC20
{
    address public PITTU;

```
Explanation: We define a new contract Pittu that inherits from OpenZeppelin's ERC20 contract. We declare a state variable PITTU to store the address of the contract deployer.

```solidity
    modifier onlyPITTU() 
    {
        require(msg.sender == PITTU, "Only the contract PITTU can perform this action");
        _;
    }
```
Explanation: The onlyPITTU modifier restricts certain functions so that only the contract owner (PITTU) can call them. It checks if the sender (msg.sender) is the contract owner, and if not, it reverts the transaction with an error message.

```solidity
       constructor() ERC20("PittuPrasanth", "PI")
    {
        PITTU = msg.sender;
    }

```
Explanation: The constructor function initializes the contract. It sets the token name to "PittuPrasanth" and the symbol to "PI". It also sets the PITTU variable to the address that deploys the contract (msg.sender), which will have special permissions.

```solidity
         function mintToken(address account, uint256 amount) external onlyPITTU
    {
        _mint(account, amount);
    }
    function burnToken(address account, uint256 amount) external 
    {
        require(msg.sender == account, "You can only burn your own tokens");
        _burn(account, amount);
    }
    function transferToken(address recipient, uint256 amount) external returns (bool) 
    {
        return transfer(recipient, amount);
    }
}



```
Explanation: The mintToken function allows the contract owner to create new tokens and assign them to a specified account. The onlyPITTU modifier ensures that only the owner can call this function. The _mint function, inherited from the ERC20 contract, handles the creation and assignment of tokens. The burnToken function allows users to destroy a specified amount of their own tokens, reducing the total supply. It checks that the caller of the function (msg.sender) is the same as the account from which tokens are being burned. If the check passes, it calls the _burn function to destroy the tokens.The transferToken function allows users to transfer their tokens to another address. It calls the transfer function inherited from the ERC20 contract. This function moves the specified amount of tokens to the recipient and returns a boolean indicating whether the transfer was successful.

## Help
#### Common Issues:

#### Compilation Errors:

- Ensure you are using Solidity version 0.8.18 or above.
- Check for any typos or syntax errors in the code.
#### Deployment Issues:

- Make sure you have selected the correct environment in Remix.
- Ensure you have sufficient funds in your account if using a test network.
#### Helper Command:

- Remix IDE does not have a built-in help command, but you can refer to the Remix Documentation for guidance.
Authors
PITTU PRASANTH - @pittu777


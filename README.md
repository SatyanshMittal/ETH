Project Title:

A simple smart contract for creating and managing a token named "MyToken".

Description
The MyToken contract allows users to mint new tokens, burn existing tokens, and keep track of token balances associated with different addresses. The contract demonstrates basic token management on the Ethereum blockchain.

Getting Started
Executing program
Follow these steps to set up and deploy the contract using Remix IDE:

Open Remix IDE: Go to Remix IDE.

Create a New File:

In the left sidebar, click on the "+" icon to create a new file.
Name your file MyToken.sol.
Paste the Solidity Code:


// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    // Public variables to store the details about the token
    string public name = "MyToken";
    string public symbol = "MTK";
    uint256 public totalSupply;

    // Mapping to store balances of addresses
    mapping(address => uint256) public balances;

    // Mint function to create new tokens
    function mint(address to, uint256 value) public {
        totalSupply += value;
        balances[to] += value;
    }

    // Burn function to destroy tokens
    function burn(address from, uint256 value) public {
        require(balances[from] >= value, "Balance is less than the amount to burn");
        totalSupply -= value;
        balances[from] -= value;
    }
}


Public Variables:

name: The name of the token (MyToken).
symbol: The abbreviation of the token (MTK).
totalSupply: The total supply of the token, initialized to 0.
Mapping:

balances: This mapping keeps track of each address's balance.
Mint Function:

Takes two parameters: to (the address to receive the tokens) and value (the number of tokens to mint).
Increases the totalSupply by value.
Increases the balance of the to address by value.
Burn Function:

Takes two parameters: from (the address from which tokens will be burned) and value (the number of tokens to burn).
Checks if the balance of the from address is greater than or equal to value.
Decreases the totalSupply by value.
Decreases the balance of the from address by value.
This smart contract allows minting and burning of tokens, which affects the total supply and the balances of the respective addresses. Make sure to test this contract thoroughly before deploying it on a live blockchain.




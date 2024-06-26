# Project Title

A simple smart contract for an ERC-20 like token implementation on the Ethereum blockchain, allowing for minting and burning of tokens while tracking total supply and balances.


## Description

The `MyToken` smart contract facilitates the creation, management, and destruction of a custom cryptocurrency token. This project demonstrates basic blockchain programming concepts including the use of Solidity, smart contract development, and token management.


## Getting Started

### Installing

* Clone the repository from github:
  ```bash
  https://github.com/Espada203/ethereum-assesment.git
* Navigate to the project directory:
  ```bash
  cd mytoken
  
### Executing program

* Compile and deploy the contract using a development environment like Remix, Truffle, or Hardhat.
* Contract code
```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public tokenName = "META";
    string public tokenAbbrv = "MTA";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}

```

## Contract details

1. **Public Variables**:
   - **Token Name**: The name of the token (e.g., "META").
   - **Token Abbreviation**: The abbreviated symbol of the token (e.g., "MTA").
   - **Total Supply**: The total supply of the tokens in existence.

2. **Mapping**:
   - A mapping that associates addresses with their corresponding token balances.

3. **Mint Function**:
   - A function that takes an address and a value as parameters. It increases the total supply by the given value and also increases the balance of the specified address by that amount.

4. **Burn Function**:
   - A function that takes an address and a value as parameters. It decreases the total supply by the given value and also decreases the balance of the specified address by that amount. It includes a check to ensure the address has a sufficient balance to burn.


## Authors

Contributors names and contact info

ex. Parichay Sharma  
ex. (203parichaysharma@gmail.com)


## License

This project is licensed under the [MIT] License - see the LICENSE.md file for details

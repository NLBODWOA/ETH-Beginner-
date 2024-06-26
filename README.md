# ETH_Begineer

This Solidity program is a simple "ETH_Begineer" program that demonstrates the basic syntax and functionality of the Solidity programming language. The purpose of this program is to serve as a starting point for those who are new to Solidity and want to get a feel for how it works.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has a single function that returns the string "ETH_Begineer!". This program serves as a simple introduction to Solidity programming and can be used as a stepping stone for more complex projects in the future.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Token.sol). Copy and paste the following code into the file:

```javascript
pragma solidity ^0.8.18;

contract Token {

  // Public variables for token details (using generic names)
  string public name = "MyCoin";
  string public symbol = "MYC"; // Using 'symbol' instead of 'tokenAbbrv' for standard convention
  uint256 public totalSupply; // Using uint256 for larger supply sizes

  // Mapping to store balances
  mapping(address => uint256) public balances;

  // Mint function to create tokens
  function mint(address recipient, uint256 amount) public {
    require(msg.sender != address(0), "Cannot mint to zero address"); // Ensure non-zero recipient

    totalSupply += amount;
    balances[recipient] += amount;
  }

  // Burn function to destroy tokens (with safety check)
  function burn(address account, uint256 amount) public {
    require(balances[account] >= amount, "Insufficient balance for burning"); // Check balance before burning

    totalSupply -= amount;
    balances[account] -= amount;
  }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.4" (or another compatible version), and then click on the "Compile HelloWorld.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "HelloWorld" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "HelloWorld" contract in the left-hand sidebar, and then click on the "sayHello" function. Finally, click on the "transact" button to execute the function and retrieve the "Hello World!" message.

## Authors

Metacrafter Chris  
[@metacraftersio](https://twitter.com/metacraftersio)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details

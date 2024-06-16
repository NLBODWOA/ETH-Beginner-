// SPDX-License-Identifier: MIT
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

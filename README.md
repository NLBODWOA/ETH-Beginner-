// SPDX-License-Identifier: MIT
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

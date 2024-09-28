# OCOS-UK

```markdown
# OCOS-UK Smart Contract

OCOS-UK is a blockchain project that introduces a decentralized token based on the ERC-20 standard. The OCOS token is designed for use within the metaverse, providing integration with decentralized finance (DeFi) protocols, tokenized assets, and smart contract-enabled services. The smart contract is implemented using Solidity and includes essential functions such as token minting, burning, and transfer.

## Features
- **ERC-20 Standard**: OCOS token adheres to the widely-used ERC-20 standard, ensuring compatibility with Ethereum-based DeFi platforms.
- **18 Decimal Precision**: The OCOS token uses 18 decimals to maintain compatibility with the Ethereum network's token precision.
- **Initial Supply**: 1 billion OCOS tokens are minted upon contract creation.
- **Minting and Burning**: The contract allows the owner to mint new tokens and users to burn their tokens.
- **OpenZeppelin Libraries**: The contract uses OpenZeppelin's well-audited libraries for security and reliability.

## Contract Details
- **Contract Name**: OCOS UK
- **Symbol**: OCOS
- **Total Supply**: 1,000,000,000 OCOS
- **Decimals**: 18
- **Contract Owner**: The contract creator has special permissions to mint new tokens.

### Smart Contract Code
The smart contract is written in Solidity, a popular language for Ethereum-based smart contracts. Below is a basic outline of the contract code:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract OCOSToken is ERC20, Ownable {
    uint8 private _decimals = 18;  // 18 decimal precision
    uint256 public constant INITIAL_SUPPLY = 1_000_000_000 * (10 ** 18); // 1 billion tokens with 18 decimals

    constructor() ERC20("OCOS UK Token", "OCOS") {
        _mint(msg.sender, INITIAL_SUPPLY); // Mint all tokens to the contract creator
    }

    // Override decimals to 18
    function decimals() public view virtual override returns (uint8) {
        return _decimals;
    }

    // Mint new tokens
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Burn tokens
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
```

## How to Deploy
1. **Install Dependencies**: Install the necessary dependencies using npm or yarn.
    ```bash
    npm install @openzeppelin/contracts
    ```
2. **Compile the Smart Contract**: Use a Solidity compiler such as Remix IDE to compile the smart contract.
3. **Deploy the Contract**: Deploy the contract on a blockchain such as Ethereum or Binance Smart Chain (BSC).
4. **Minting and Burning**: The contract owner can use the `mint` and `burn` functions as needed.

## Interacting with the Contract
You can interact with the contract using the following functions:
- **balanceOf(address account)**: Check the token balance of an account.
- **transfer(address to, uint256 amount)**: Transfer tokens to another account.
- **approve(address spender, uint256 amount)**: Approve another account to spend tokens on your behalf.
- **transferFrom(address from, address to, uint256 amount)**: Transfer tokens from one account to another using an approved spender.
- **mint(address to, uint256 amount)**: The contract owner can mint new tokens.
- **burn(uint256 amount)**: Users can burn their tokens to reduce the supply.

## License
This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for more details.

## Contact
For further information, please contact us at: **support@ocos.io**

Visit our website: [OCOS UK](https://www.ocos.io)

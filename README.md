# MyToken (MTK) - ERC-20 Implementation

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Solidity](https://img.shields.io/badge/Solidity-0.8.20-363636.svg)
![Remix](https://img.shields.io/badge/Built%20With-Remix%20IDE-blueviolet)

## Overview

**MyToken** is a custom implementation of the ERC-20 token standard built on the Ethereum blockchain. This project demonstrates the core functionality of fungible tokens, including minting, transferring, approval mechanisms, and error handling. It was developed and tested using the Remix IDE.

## Token Details

| Property | Value |
| :--- | :--- |
| **Token Name** | MyToken |
| **Symbol** | MTK |
| **Decimals** | 18 |
| **Total Supply** | 1,000,000 MTK |
| **Supply (in Wei)** | `1000000000000000000000000` |

## What is an ERC-20 Token?

The **ERC-20** (Ethereum Request for Comment 20) is the technical standard for fungible tokens created using the Ethereum blockchain. "Fungible" means that each token is exactly the same (in type and value) as another token. It defines a common list of rules that an Ethereum token has to implement, allowing developers to predict how interactions between tokens and DApps (Decentralized Apps) will work.

## Features Implemented

This contract includes the following functionality:

1.  **Core ERC-20 Functions:**
    * `totalSupply()`: Returns the total token supply.
    * `balanceOf(address)`: Checks the balance of a specific wallet.
    * `transfer(to, value)`: Sends tokens from the caller to another address.
    * `approve(spender, value)`: Authorizes a third party to spend tokens on your behalf.
    * `transferFrom(from, to, value)`: Used by a third party to move tokens (requires approval).
    * `allowance(owner, spender)`: Checks the remaining amount a spender is allowed to use.

2.  **Helper Functions:**
    * `getTokenInfo()`: A custom function to retrieve name, symbol, decimals, and supply in a single call.

3.  **Safety & Events:**
    * `Transfer` and `Approval` events emitted for frontend tracking.
    * Error handling with `require` statements (e.g., checking for sufficient balance).

## Deployment Instructions

This contract was deployed using the **Remix IDE**.

1.  Open [Remix IDE](https://remix.ethereum.org/).
2.  Create a new file named `MyToken.sol`.
3.  Paste the Solidity contract code.
4.  Navigate to the **Solidity Compiler** tab:
    * Compiler version: `0.8.20` (or higher).
    * Click **Compile MyToken.sol**.
5.  Navigate to the **Deploy & Run Transactions** tab:
    * Environment: `Remix VM (Cancun)`.
    * Account: Select one of the pre-funded test accounts.
    * Contract: Select `MyToken`.
    * Click **Deploy**.

## Usage Examples

### 1. Checking Balance
Input your address into the `balanceOf` field to see your holding.

// Returns the balance in Wei (1 token = 1 * 10^18)
balanceOf("0x5B3...")

### 2. Transferring Tokens
To send 100 MTK to another user:

// Input: Receiver Address, Amount (in Wei)
// 100 MTK = 100 * 10^18 Wei
transfer("0xAb8...", 100000000000000000000)

### 3. Approving a Spender (Delegate)

To allow a DEX or another external address to spend 50 MTK from your wallet:

// Input: Spender Address, Amount
approve("0xAb8...", 50000000000000000000);

## Testing Scenarios & Results

Comprehensive testing was performed to validate contract security and functionality.

| Scenario | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :---: |
| **Valid Transfer** | Token balance updates correctly. | Transfer event emitted, balances updated. | ✅ Passed |
| **Insufficient Balance** | Transaction reverts. | Error: "Insufficient balance" | ✅ Passed |
| **Zero Address Transfer** | Transaction reverts. | Error: "Cannot transfer to zero address" | ✅ Passed |
| **Approve Spender** | Allowance mapping updates. | Approval event emitted. | ✅ Passed |
| **TransferFrom (Valid)** | Tokens move from Owner → Receiver. | Transfer event emitted. | ✅ Passed |
| **TransferFrom (Over Limit)** | Transaction reverts. | Error: "Insufficient allowance" | ✅ Passed |

## What I Learned

Building this project helped solidify my understanding of:

- **State Variables vs. Local Variables:** Understanding how data is stored on the blockchain vs. in memory during function execution.
- **Events:** The importance of emitting events (`emit Transfer`) so that off-chain applications (frontends) can listen to changes.
- **The Approval Mechanism:** How `approve` and `transferFrom` work together to enable DeFi patterns (like swapping tokens on a DEX).
- **Gas Optimization:** Observing gas costs for different transactions in Remix.
- **Error Handling:** Using `require` to prevent invalid transactions and save gas for the user.

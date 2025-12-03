# MyToken (MTK)

## Overview
MyToken is a simple ERC-20 compatible token built on Ethereum for learning purposes. It demonstrates the core principles of smart contract development, including state management, event logging, and the standard token interface used by major cryptocurrencies.

## Token Details
- **Name**: MyToken
- **Symbol**: MTK
- **Decimals**: 18
- **Total Supply**: 1,000,000 MTK

## Features
- ✅ **Standard ERC-20 implementation** (Compatible with wallets/exchanges)
- ✅ **Transfer tokens** between addresses
- ✅ **Approve and transferFrom** functionality (Delegate spending)
- ✅ **Event emission** for transparency (Transfer & Approval logs)
- ✅ **Balance tracking** for all holders

## How to Deploy
1. Open [RemixIDE](https://remix.ethereum.org/).
2. Create a new file named `MyToken.sol`.
3. Paste the contract code into the editor.
4. Navigate to the **Solidity Compiler** tab and compile with version 0.8.x.
5. Navigate to the **Deploy & Run Transactions** tab.
6. In the Deploy input box, enter the initial supply (with 18 zeros).
   * Example for 1 Million tokens: `1000000000000000000000000`
7. Click **Deploy**.

## How to Use

### Check Balance
Returns the token balance of a specific address.
```solidity
balanceOf(address account) → returns uint256

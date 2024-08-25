# Ethavax4
---
# DegenToken Smart Contract

## Overview

The `DegenToken` smart contract is an ERC20 token with added functionality for minting, burning, and redeeming tokens for exclusive NFTs. It is designed for the Ethereum blockchain using Solidity and is built on top of the OpenZeppelin library for security and standardization.

## Features

- **ERC20 Token**: Standard ERC20 functionality for minting, burning, and transferring tokens.
- **NFT Redemption**: Users can redeem their tokens for specific NFT items representing exclusive digital collectibles.
- **Ownable Contract**: Only the contract owner can mint new tokens.
- **Store Interface**: View the available NFTs for redemption and the items owned by players.

## Contract Details

- **Token Name**: Degen
- **Token Symbol**: DGN
- **Solidity Version**: 0.8.20

## Functions

### 1. `mint(address to, uint256 amount)`

Mints new tokens and assigns them to the specified address. This function can only be called by the contract owner.

### 2. `burn(uint256 amount)`

Burns the specified amount of tokens from the sender's balance, reducing the total supply.

### 3. `transferToken(address receiver, uint256 amount)`

Transfers tokens from the sender's balance to the specified receiver.

### 4. `redeem(uint256 item)`

Allows users to redeem their tokens for one of the available NFT items. The cost is deducted from the user's balance, and the item is added to their list of owned items.

### 5. `showStore()`

Returns a list of the available NFT items along with their token cost.

### 6. `getPlayerItems(address player)`

Returns a list of items owned by a specified player.

## Example Usage

1. **Deploy the contract** with the address of the initial owner.
2. **Mint tokens** to an address (only the owner can do this).
3. **Transfer tokens** between addresses.
4. **Redeem items** from the store by burning tokens.
5. **View available items** in the store.
6. **Check redeemed items** for a specific player.

## Deployment on Fuji Network

### Requirements

1. **Remix IDE**: A web-based IDE for Solidity development.
2. **MetaMask**: A browser extension for managing Ethereum-compatible wallets.
3. **AVAX Test Tokens**: Required for deploying the contract on the Fuji test network.

### Steps

1. **Set Up MetaMask**:
   - Install the MetaMask extension for your browser.
   - Create a new wallet or import an existing one.
   - Switch to the Fuji test network. To add the Fuji test network to MetaMask, use the following settings:
     - Network Name: Avalanche Fuji C-Chain
     - New RPC URL: `https://api.avax-test.network/ext/bc/C/rpc`
     - Chain ID: `43113`
     - Symbol: `AVAX`
     - Explorer URL: `https://cchain.explorer.avax-test.network/`
   
2. **Obtain AVAX Test Tokens**:
   - Visit the [Avalanche Fuji Faucet](https://faucet.avax-test.network/).
   - Enter your wallet address to receive test AVAX tokens.

3. **Deploy Contract Using Remix**:
   - Open [Remix IDE](https://remix.ethereum.org/).
   - Create a new file and paste the `DegenToken` contract code.
   - Compile the contract by selecting the appropriate Solidity version.
   - In the "Deploy & Run Transactions" panel, select "Injected Web3" as the environment to connect Remix to MetaMask.
   - Ensure that MetaMask is connected to the Fuji network and has sufficient AVAX test tokens.
   - Deploy the contract by specifying the initial owner's address.
   - Confirm the transaction in MetaMask.

4. **Verify Contract on Snowtrace**:
   - After deploying the contract, you can verify it on [Snowtrace](https://testnet.snowtrace.io/).
   - Navigate to the contract address on Snowtrace.
   - Click on the "Verify and Publish" button.
   - Select the compiler version and optimization settings used during deployment.
   - Paste the contract code and complete the verification process.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Notes

- The `redeem` function burns the required amount of tokens and adds the redeemed item to the player's list. It also removes the redeemed item from the store.
- The `showStore` function returns a static list of items. To reflect dynamic updates, further logic could be added to generate this string dynamically based on the `items` mapping.

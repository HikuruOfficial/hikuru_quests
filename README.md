[![Follow us on Twitter](https://img.shields.io/twitter/follow/HikuruOfficial?style=social&logo=twitter)](https://twitter.com/HikuruOfficial)
[![Join our Discord](https://img.shields.io/discord/989643607898206208?color=%237289DA&label=Join%20our%20Discord&logo=discord&logoColor=white)](https://discord.gg/mevde2mRSw)
![Aleo Badge](https://img.shields.io/badge/Aleo-Developer-1572B6?style=flat-square&logo=aleo&logoColor=white)
[![License](https://img.shields.io/badge/license-MIT-orange.svg)](https://opensource.org/licenses/MIT)


# Hikuru Quests NFT Smart Contract

[hikuru_quests_nft.aleo](https://explorer.hamp.app/program?id=hikuru_quests_nft.aleo)


Welcome to the Hikuru Quests NFT Smart Contract, an upgraded version of Private Pride specially designed for Hikuru.com. This README provides an overview of the contract's functionality and usage.

## Table of Contents
- [Introduction](#introduction)
- [Contract Structure](#contract-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Functions](#functions)
- [License](#license)

## Introduction

The Hikuru Quests NFT Smart Contract is designed to manage a collection of unique and mintable NFTs on the Aleo blockchain. It allows users to mint NFTs, add minters, claim NFTs, transfer ownership, and more, all while maintaining privacy and security.

## Contract Structure

The contract consists of various data structures and functions to achieve its objectives:

- `NFT`: Represents an NFT with private ownership, token data, and edition.
- `NFT_mint`: Records a minter's address and the number of NFTs they can mint.
- `NFT_claim`: Contains the owner's address and a private claim for NFT minting.
- `NFT_ownership`: Provides a way to prove ownership of an NFT privately.

Key mappings and settings within the contract include:
- `nft_owners`: Maps fields to owner addresses.
- `general_settings`: Stores general settings for the contract.
- `nfts_to_mint`: Maps indices to token edition hashes.
- `claims_to_nfts`: Maps claims to token edition hashes.
- `toggle_settings`: Manages contract settings, including initialization, minting, whitelist requirements, and freezing.

## Getting Started

To interact with this contract, you'll need to use the Aleo blockchain. Ensure you have an Aleo-compatible wallet and the Aleo CLI set up.

1. Clone this repository.
2. Deploy the contract to the Aleo blockchain using the Aleo CLI or a compatible development environment.
3. Use the contract's functions to mint NFTs, add minters, claim NFTs, and more.

## Usage

This contract provides various functions to manage the NFT collection. Below are some common actions:

### Initialize the Collection

```rust
transition initialize_collection(
    public total: u128,
    public symbol: u128,
    public base_uri: BaseURI
)
```

This function initializes the NFT collection with the specified total supply, symbol, and base URI.

### Mint NFTs

```rust
transition add_nft(public tokenId: TokenId, public edition: scalar)
```

Mint NFTs by providing the `tokenId` and `edition`.

### Add Minter

```rust
transition add_minter(private minter: address, public amount: u8) -> NFT_mint
```

Add a minter to the contract, specifying the minter's address and the number of NFTs they can mint.

### Update Contract Settings

```rust
transition update_toggle_settings(public toggle_settings_bitstring: u32)
```

Update contract settings, including toggling minting, whitelist requirements, or freezing the contract.

### Claim NFT

```rust
transition claim_nft(nft_claim: NFT_claim, private tokenId: TokenId, private edition: scalar) -> NFT
```

Claim an NFT by providing a claim and the NFT's `tokenId` and `edition`.

### Transfer NFT Ownership

```rust
transition transfer_private(nft: NFT, private receiver: address) -> NFT
```

Transfer ownership of an NFT to another address privately.

### Convert Ownership Privacy

```rust
transition convert_private_to_public(nft: NFT)
```

Convert private ownership of an NFT to public ownership.

```rust
transition convert_public_to_private(private owner: address, private data: TokenId, private edition: scalar) -> NFT
```

Convert public ownership of an NFT to private ownership.

## License

This contract is provided under a specific license agreement. Please refer to the license file for more details.

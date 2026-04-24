# kangeki_sbt

## Overview

A personal project that lets users mint NFTs from a web browser. Minted tokens can be switched by the owner into a **non-transferable** state — known as an **SBT (SoulBound Token)**.

| Attribute | Value |
|-----------|-------|
| Chain     | Polygon (Ethereum-compatible, low-fee blockchain) |
| Contract  | [`0xC49dB55Aea26f82e7c42b6A8c51a756E3a78A550`](https://polygonscan.com/token/0xc49db55aea26f82e7c42b6a8c51a756e3a78a550) |
| Supply    | 40 max, 0.05 MATIC per mint |
| Minting   | Web dApp (MetaMask + allowlist) |

| Directory | Role |
|-----------|------|
| `hashlips_nft_contract-main/`     | NFT smart contract (Solidity) |
| `hashlips_nft_minting_dapp-main/` | Minting web frontend (React + Firebase Hosting) |

> Use cases: event attendance badges, community memberships, commemorative tokens — anywhere non-transferability is the point.

## Steps

### Prerequisites

| Tool         | Purpose |
|--------------|---------|
| Node.js 14+  | Run the dApp locally and build for production |
| MetaMask     | Connect a wallet to the Polygon network |
| Firebase CLI | Deploy the dApp to Firebase Hosting |

### 1. Deploy the contract

The project assumes deployment via Remix IDE (no Hardhat / Truffle config is included).

1. Open [Remix IDE](https://remix.ethereum.org)
2. Copy the contents of `hashlips_nft_contract-main/info/kangeki.sol` into a new file
3. Compile with Solidity `>=0.7.0 <0.9.0`
4. In "Deploy & Run Transactions", set Environment to `Injected Provider - MetaMask` and select the Polygon network
5. Click Deploy

After deploying, update `CONTRACT_ADDRESS` in `hashlips_nft_minting_dapp-main/public/config/config.json` with the new address.

### 2. Run the dApp locally

```bash
cd hashlips_nft_minting_dapp-main
npm install
npm start
```

Open http://localhost:3000.

### 3. Deploy to production (Firebase)

```bash
cd hashlips_nft_minting_dapp-main
npm run build
firebase deploy
```

Firebase project ID: `kangeki-dapps`

## Based on

- [hashlips_nft_contract](https://github.com/HashLips/hashlips_nft_contract)
- [hashlips_nft_minting_dapp](https://github.com/HashLips/hashlips_nft_minting_dapp)

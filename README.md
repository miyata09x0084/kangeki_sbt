# kangeki_sbt

## 概要

Web ブラウザから NFT を発行できる個人プロジェクト。発行された NFT は、Owner の操作で「譲渡不可」状態（= **SBT / SoulBound Token**）に切り替えることができる。

- **チェーン**: Polygon（Ethereum 互換の低手数料チェーン）
- **発行方式**: Web dApp からミント（MetaMask 必須）、Allowlist（事前登録制）対応
- **供給量**: 最大 40 個、価格 0.05 MATIC

### ファイル構成

- `hashlips_nft_contract-main/` — NFT のスマートコントラクト（Solidity）
- `hashlips_nft_minting_dapp-main/` — ミント用の Web フロントエンド（React + Firebase Hosting）

コントラクトは Polygon 上にデプロイ済み: [`0xC49dB55Aea26f82e7c42b6A8c51a756E3a78A550`](https://polygonscan.com/token/0xc49db55aea26f82e7c42b6a8c51a756e3a78a550)

> ユースケース: イベント参加証、会員バッジ、記念品など、譲渡不可であることに意味があるユースケースを想定。

## 手順

### 前提

- Node.js 14+
- MetaMask（Polygon ネットワーク接続済み）
- Firebase CLI（本番デプロイする場合）

### 1. コントラクトのデプロイ

Remix IDE 経由でのデプロイを想定（Hardhat/Truffle 設定はなし）。

1. [Remix IDE](https://remix.ethereum.org) を開く
2. `hashlips_nft_contract-main/info/kangeki.sol` の内容をコピーして新規ファイルに貼り付け
3. Solidity `>=0.7.0 <0.9.0` でコンパイル
4. Environment を `Injected Provider - MetaMask` にして Polygon を選択
5. Deploy を実行

デプロイ後、`hashlips_nft_minting_dapp-main/public/config/config.json` の `CONTRACT_ADDRESS` を新しいアドレスに差し替える。

### 2. dApp ローカル起動

```bash
cd hashlips_nft_minting_dapp-main
npm install
npm start
```

http://localhost:3000 で動作確認。

### 3. 本番デプロイ（Firebase）

```bash
cd hashlips_nft_minting_dapp-main
npm run build
firebase deploy
```

Firebase プロジェクト ID: `kangeki-dapps`

## Based on

- [hashlips_nft_contract](https://github.com/HashLips/hashlips_nft_contract)
- [hashlips_nft_minting_dapp](https://github.com/HashLips/hashlips_nft_minting_dapp)

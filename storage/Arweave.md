---
topic: Decentralized Storage
type: concept
tags: [storage, arweave, permanent, blockweave, nft, solana, depin]
confidence: high
last_updated: 2026-03-19
sources:
  - https://docs.ipfs.tech/concepts/comparisons/
  - https://nftbirdies.com/article/arweave-filecoin-and-sia-where-to-store-nft-metadata-and-files-in-web3/
  - https://academy.swissborg.com/en/learn/arweave
  - https://blog.upay.best/crypto-terminology/arweave-ar/
---

## Summary
Arweave is a decentralised permanent storage network using a novel "blockweave" data structure and Proof of Access (PoA) consensus. Users pay a one-time fee to store data permanently — the fee goes into an endowment designed to fund miner rewards indefinitely. Once stored, data is immutable and cannot be deleted, making Arweave the dominant choice for NFT metadata and on-chain archival.

## Key Facts

- **Blockweave**: Arweave's data structure links each new block to a random historical block (a "recall block"), not just the previous block. Miners must prove access to this randomly selected old block to mine new blocks.
- **Proof of Access (PoA) / SPoRA**: Miners are incentivised to store the entire blockweave history — the more history they store, the more likely they can satisfy random recall requirements.
- **One-time fee model**: No recurring costs. Fee is placed into a storage endowment. Returns from the endowment fund miner rewards theoretically for 200+ years.
- **Permanent and immutable**: Once uploaded, data cannot be altered or deleted. This is by design.
- **Permaweb**: A permanent, censorship-resistant web layer built on Arweave — dApps, front-ends, and data accessible forever via Arweave gateways (arweave.net).
- **AR token**: Used for storage payments and miner compensation.
- **NFT dominance**: De-facto standard for NFT metadata storage. Adopted by major marketplaces (Magic Eden, Tensor, OpenSea cross-chain). Metaplex defaults to Arweave for Solana NFTs.
- **Solana integration**: 
  - Solana's validator ledger archiving is officially recommended to use Arweave.
  - Solana's transaction history is archived via the Geyser framework to Arweave.
  - [[Irys Bundlr]] abstracts Arweave uploads, accepting SOL and other tokens.
- **Research paper (2025)**: Published in Engineering Reports — blockweave-based architecture reduces on-chain metadata to 48 bytes, enabling 7,200 TPS throughput for storage-intensive apps.
- **Upfront cost variability**: AR token price volatility makes cost unpredictable. Higher initial cost than time-bound contracts on [[Filecoin]] for small datasets.
- **Static data orientation**: Designed for immutable, final content. Poor fit for mutable data (databases, live state).
- **Retrieval speed**: Slower than [[IPFS]] gateways for hot/frequently-accessed content; optimised for archival not CDN.

> [!fact] Confirmed from official/primary sources
> Arweave is recommended by the Solana Foundation for validator ledger archiving. Bundlr/Irys handles ~70% of Arweave's network traffic.

> [!analysis] Analyst inference — not verified
> Arweave's endowment model assumes AR token value appreciates or at minimum holds — a market-dependent assumption. If AR price collapses long-term, the endowment math breaks down.

## How it relates to Logos

- Arweave demonstrates that permanent storage is a marketable primitive — developers pay a premium for the "never worry about renewals" guarantee. Logos could offer a similar permanence tier.
- The Logos Ideas #19 use case (decentralised Supabase) needs a data layer — immutable blobs on Arweave are unsuitable for mutable app state, but archival of schema versions/migrations could use an Arweave-like model.
- Arweave's Permaweb (censorship-resistant front-end hosting) is a Logos-aligned use case: hosting dApp front-ends on Logos storage to make them unstoppable.
- Cross-chain payment abstraction via [[Irys Bundlr]] (pay with SOL, store on Arweave) is an architectural pattern applicable to Logos: accept payment in any token, abstract the underlying storage protocol.

## Open Questions

- Is Arweave's endowment model financially sustainable if AR price stays flat or declines?
- Could Logos Storage offer a "permanent storage" mode analogous to Arweave, without the token price risk?
- How does Arweave's retrieval performance compare to Logos Storage for live app use cases?

## Sources

- https://docs.ipfs.tech/concepts/comparisons/
- https://nftbirdies.com/article/arweave-filecoin-and-sia-where-to-store-nft-metadata-and-files-in-web3/
- https://academy.swissborg.com/en/learn/arweave
- https://blog.upay.best/crypto-terminology/arweave-ar/
- https://midlandsinbusiness.com/nft-storage-choices-on-chain-ipfs-and-arweave-for-long-term-asset-survival
- https://onlinelibrary.wiley.com/doi/full/10.1002/eng2.70259

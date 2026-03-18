---
topic: DAS API Standard
type: concept
tags: [solana, das, nft, digital-assets, api-standard, helius, metaplex]
confidence: high
last_updated: 2026-03-18
sources:
  - https://www.helius.dev/blog/all-you-need-to-know-about-solanas-new-das-api
  - https://www.helius.dev/docs/das-api
  - https://helius.mintlify.app/das-api
  - https://www.quicknode.com/docs/solana/solana-das-api
---

## Summary
The Digital Asset Standard (DAS) API is an open-source specification (pioneered by Helius, adopted by Metaplex) that provides a unified JSON-RPC interface for querying all types of Solana digital assets: standard NFTs, compressed NFTs (cNFTs), fungible tokens, and programmable NFTs (pNFTs). It abstracts the complexity of Solana's multiple token standards and on-chain data layouts into a single consistent API.

## Key Facts
- **Origin**: Introduced by Helius Labs in 2023; later formalized by Metaplex as part of the token standard spec.
- **Scope**: Standard NFTs, cNFTs (Bubblegum/Merkle tree), Fungible tokens, Fungible Assets, Programmable NFTs (pNFTs).
- **Interface**: JSON-RPC (same transport as standard Solana RPC), not REST.
- **Core methods**:
  - `getAsset` — fetch single asset by ID
  - `getAssetProof` — Merkle proof for compressed NFTs
  - `getAssetsByOwner` — all assets for a wallet
  - `getAssetsByGroup` — assets in a collection
  - `getAssetsByCreator` — assets by creator address
  - `getAssetsByAuthority` — assets by update authority
  - `searchAssets` — flexible multi-parameter search
- **Compressed NFT support**: Critical feature — cNFTs are stored in Merkle trees on-chain; DAS API handles proof retrieval and decompression transparently.
- **Off-chain metadata**: DAS indexes the off-chain JSON metadata (images, attributes) in addition to on-chain state. Note: off-chain data is re-indexed only when the NFT is seen again by the system (no real-time refresh on off-chain changes).
- **Multi-provider**: Helius, QuickNode, and other RPC providers implement the same DAS spec — portability across providers.
- **Fungible Token Extension**: Helius extended DAS to cover fungible tokens, including price data for top 10k tokens by 24h volume.

> [!fact] Confirmed from official docs
> DAS is described as "open-source specification" by both Helius and Metaplex documentation. Multiple providers implement the same interface.

> [!analysis] De-facto standard
> DAS has become the dominant standard for Solana NFT/digital asset data. The fragmented pre-DAS landscape (separate Metaplex SDK calls, manual on-chain decoding) was replaced by this unified interface. Adoption by QuickNode confirms cross-provider standardization.

## How it relates to Logos
- DAS is the closest analog to what Logos Ideas #19 envisions: a standardized query API layer over complex on-chain data.
- Key insight: DAS works because it solved a specific pain point (fragmented NFT standards) with a narrow, well-defined interface. Logos's query layer would need a similarly focused scope.
- The off-chain metadata indexing (JSON at URI) is analogous to how Logos Storage objects would need a query layer — the DAS approach of caching + indexing off-chain data alongside on-chain pointers is a proven pattern.
- See also: [[Helius Platform]], [[Solana Account Model vs EVM Events]]

## Open Questions
- Is DAS being expanded beyond NFTs/tokens to cover general program state (DeFi positions, etc.)?
- Does DAS have a governance process for adding new methods, or is it Helius/Metaplex-controlled?
- Could a DAS-equivalent spec work for Logos Storage objects?

## Sources
- https://www.helius.dev/blog/all-you-need-to-know-about-solanas-new-das-api
- https://www.helius.dev/docs/das-api
- https://helius.mintlify.app/das-api
- https://www.quicknode.com/docs/solana/solana-das-api

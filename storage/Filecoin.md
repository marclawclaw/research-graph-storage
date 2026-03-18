---
topic: Decentralized Storage
type: concept
tags: [storage, filecoin, incentive-layer, enterprise, ipfs, depin]
confidence: high
last_updated: 2026-03-19
sources:
  - https://docs.ipfs.tech/concepts/comparisons/
  - https://thetechtrends.tech/decentralized-storage-solutions/
  - https://messari.io/report/state-of-filecoin-q3-2024
  - https://depinscan.io/news/2025-03-14/filecoin-s-strategic-shift-drives-99m-inflows-and-client-growth
---

## Summary
Filecoin is a decentralised storage marketplace built on top of [[IPFS]]. Storage providers (miners) compete for deals, post cryptographic proofs that they are continuously storing client data, and earn FIL tokens. Unlike IPFS alone, Filecoin creates economic incentives for long-term persistence through time-bound storage contracts.

## Key Facts

- **Built on IPFS**: Uses CIDs for content addressing; clients store data via IPFS then anchor persistence through Filecoin deals.
- **Storage deals**: Client negotiates with a provider — duration, replication factor, geography, price. Deals are on-chain, cryptographically enforced.
- **Proof of Replication (PoRep)**: Proves the provider stored a unique copy at sealing time.
- **Proof of Spacetime (PoSt)**: Ongoing proof that data is still stored; missed proofs incur slashing.
- **Sectors**: Data packed into 32 or 64 GiB sectors before sealing. Storage granularity is coarse.
- **Retrieval market**: A separate market pays providers to serve data quickly (distinct from the storage deal economics).
- **FIL token**: Used for storage payments, provider collateral/slashing, and network governance.
- **Enterprise adoption (Q3 2025)**: 2,491 onboarded datasets; 925 of them exceed 1,000 TiB (research and enterprise scale). Q4 2024: 2,263 clients (+10% QoQ). 804 clients storing >1,000 TiB (Aug 2025 figure).
- **$99M inflows** reported in early 2025 as enterprise strategy shift drove client growth.
- **Network utilisation Q2 2025**: 32% of capacity utilised despite 13% decline in total capacity — demand growing faster than raw supply.
- **FIL ProPGF**: $15M allocated to public goods tooling and research.
- **CAR files**: Client data packaged as Content Addressable aRchive files for efficient deal preparation.
- **Filecoin Virtual Machine (FVM)**: Launched 2023, adds programmable smart contracts on top of storage — enabling perpetual storage deals, data DAOs, storage bounties.

> [!fact] Confirmed from Messari Q3 2024
> Over 1,600 PiB stored through active deals in Q3 2024, down 8% QoQ but network pivoting towards higher-quality enterprise datasets rather than bulk low-value storage.

> [!analysis] Analyst inference — not verified
> Filecoin's retrieval speeds have historically been slow (cold storage orientation). The retrieval market (Saturn CDN) attempts to address this but hot-data use cases remain weak compared to [[Arweave]] + [[Irys Bundlr]] or centralised CDNs.

## How it relates to Logos

- Filecoin demonstrates the viability of an incentive layer bolted onto a content-addressed P2P layer ([[IPFS]]). Logos Storage could follow a similar layered architecture.
- The FVM model — smart contracts that can programmatically interact with storage commitments — is directly relevant to Logos Ideas #19 (decentralised Supabase): storage commitments could be made conditional on schema versions or indexing outputs.
- Filecoin's deal complexity (CAR files, sealing, sector sizes) creates significant developer friction. Logos could differentiate by abstracting this into an S3-like UX.
- Enterprise adoption numbers show decentralised storage is viable at scale for archival — but hot/low-latency access remains an unsolved problem in this model.

## Open Questions

- Does Filecoin's retrieval market (Saturn) reach latency competitive with S3 for web apps?
- Would FVM smart contracts provide a useful template for Logos Storage's data commitment primitives?
- Is Filecoin being used beyond archival / large-dataset clients for live application state?

## Sources

- https://docs.ipfs.tech/concepts/comparisons/
- https://thetechtrends.tech/decentralized-storage-solutions/
- https://messari.io/report/state-of-filecoin-q3-2024
- https://messari.io/report/state-of-filecoin-q3-2025
- https://depinscan.io/news/2025-03-14/filecoin-s-strategic-shift-drives-99m-inflows-and-client-growth
- https://www.ainvest.com/news/filecoin-long-term-play-decentralized-storage-quiet-revolution-crypto-volatility-2508/

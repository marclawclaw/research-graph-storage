---
topic: Decentralized Storage
type: concept
tags: [storage, irys, bundlr, arweave, solana, cross-chain, upload-layer, depin]
confidence: high
last_updated: 2026-03-19
sources:
  - https://irys.xyz/
  - https://medium.com/irys/bundlr-network-101-how-does-bundlr-work-a8759d7e338e
  - https://www.rootdata.com/Projects/detail/Irys
  - https://coinmarketcap.com/currencies/irys/
---

## Summary
Irys (formerly Bundlr Network) is a data layer blockchain that evolved from an [[Arweave]] upload service into a standalone programmable chain. Originally, Bundlr solved the "I want to store on Arweave but pay with SOL/ETH" problem and handled ~70% of Arweave's network traffic. In 2024, it rebranded to Irys and pivoted to building its own blockchain where smart contracts can directly access onchain data during execution.

## Key Facts

- **Bundlr origin**: Bundlr Network was an Arweave scaling and payment abstraction layer. Users uploaded to Arweave paying with ETH, SOL, MATIC, DOT, or other tokens; Bundlr converted to AR tokens behind the scenes.
- **Multi-chain signing**: Users signed transactions with their native keys (Ethereum, Solana, etc.) — no AR wallet required.
- **Traffic share**: Bundlr handled approximately 70% of Arweave network traffic at its peak — Arweave's de-facto upload gateway.
- **Rebrand to Irys (June 2024)**: Bundlr rebranded as Irys, signalling a shift from upload layer to independent chain.
- **Irys chain**: A blockchain designed to store large volumes of data onchain for **flexible durations** (not just permanent like Arweave). Smart contracts can use stored data directly during execution. Storage fees and execution fees are separate.
- **Data availability verification**: The protocol verifies data availability continuously.
- **Funding**:
  - $3.5M strategic round (Jan 2025)
  - $10M seed extension (2024)
  - $10M Series A (Nov 2025)
  - Total: ~$23.5M raised
- **Testnet**: Live on testnet as of Aug 2025.
- **Airdrop**: IRYS token airdrop registration opened late 2025.
- **IRYS token**: Native token for the Irys chain.

> [!fact] Confirmed from CoinMarketCap / RootData
> Irys raised $10M seed (2024) + $10M Series A (Nov 2025). Testnet launched Aug 2025. Total funding ~$23.5M.

> [!analysis] Analyst inference — not verified
> The pivot from "Arweave upload service" to "standalone programmable data chain" is significant and ambitious. Irys is no longer purely an [[Arweave]] complement — it's positioning as an alternative with smart-contract-accessible onchain storage. If the Irys chain succeeds, it could displace both Arweave (for flexible-duration storage) and Filecoin (for verified storage). The flexible duration model fills the gap between Arweave's permanent storage and Filecoin's complex deal system.

## How it relates to Logos

- Irys's cross-chain payment abstraction (pay with SOL, store on Arweave/Irys) is a UX pattern Logos should study: don't require users to hold a specific storage token — accept the token they already have.
- The programmable data chain concept (smart contracts reading stored data during execution) maps directly to the Logos Ideas #19 (decentralised Supabase) vision — query-layer smart contracts could read and index stored data.
- Irys's evolution shows there's a market for a "middle tier" between permanent archival ([[Arweave]]) and complex deal negotiation ([[Filecoin]]) — flexible durations, simple UX, programmable.
- Logos could learn from Bundlr's initial traction: solve the upload UX problem first (cross-chain payments, batch uploads) before building full chain infrastructure.

## Open Questions

- Does Irys mainnet ship in 2026? Is it production-ready by the time Logos Storage is live?
- How does Irys's "flexible duration" storage cost compare to Filecoin's deal-based model and Arweave's one-time fee?
- Can smart contracts on other chains (e.g., Logos chain) access data stored on Irys during execution?

## Sources

- https://irys.xyz/
- https://medium.com/irys/bundlr-network-101-how-does-bundlr-work-a8759d7e338e
- https://www.rootdata.com/Projects/detail/Irys?k=MjI4OQ%3D%3D
- https://coinmarketcap.com/currencies/irys/
- https://www.cypherhunter.com/en/p/bundlr-network/

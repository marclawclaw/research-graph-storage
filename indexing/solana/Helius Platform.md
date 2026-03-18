---
topic: Helius Platform
type: competitor
tags: [solana, helius, rpc, api, webhooks, grpc, laserstream, das, platform]
confidence: high
last_updated: 2026-03-18
sources:
  - https://www.helius.dev/
  - https://www.helius.dev/blog/solana-data-tools
  - https://www.helius.dev/docs/getting-data
  - https://www.helius.dev/docs/laserstream
  - https://www.helius.dev/blog/introducing-next-generation-enhanced-websockets
---

## Summary
Helius is the dominant Solana-focused developer infrastructure platform, combining RPC access, the DAS API, enhanced transaction APIs, webhooks, and the LaserStream gRPC streaming service into a single developer experience. It serves as the de-facto "Alchemy of Solana" and is the primary implementation of the DAS standard.

## Key Facts
- **Core offerings**:
  1. **RPC nodes** — standard Solana JSON-RPC with archival access; SOC 2-compliant
  2. **DAS API** — unified NFT/token query interface (see [[DAS API Standard]])
  3. **Enhanced Transactions API** — decoded, human-readable transaction data (enriched above raw RPC)
  4. **Webhooks** — push-based notifications for wallet activity, token transfers, program interactions; no polling needed
  5. **WebSockets** — real-time account/transaction subscriptions
  6. **LaserStream** — next-generation gRPC streaming service
  7. **Dedicated Nodes** — private nodes with Geyser access for enterprise
- **LaserStream** specifics:
  - Taps directly into Solana leaders to receive **shreds** (raw block fragments) as produced
  - Ultra-low latency — purpose-built for trading, MEV, real-time monitoring
  - Aggregates multiple Solana nodes for redundancy (no single-node failure risk)
  - Supports **24-hour historical replay** — catch up on missed data after reconnection
  - Powered by same infrastructure as Enhanced WebSockets
- **Enhanced WebSockets**: Geyser-enhanced subscriptions supporting up to 50,000 address filters via `accountInclude`, `accountExclude`, `accountRequired` — far beyond standard Solana WebSocket limits.
- **Historical data**: `getTransactionsForAddress` — billed as "fastest, most developer-friendly" way to backfill Solana data.
- **Orb**: Helius's own block explorer at `orb.helius.dev`.
- **Pricing**: Tiered (free to enterprise); traders recommended to use LaserStream + Sender (tx landing) + Shred Delivery (raw shreds).

> [!fact] Confirmed from Helius docs and pricing page
> Helius offers SOC 2 compliance, indicating enterprise-grade security standards. LaserStream uses shred-level data delivery — the lowest latency available on Solana.

> [!analysis] Market position
> Helius is the single most comprehensive Solana developer platform. The combination of DAS (NFT/token indexing), enhanced RPC (decoded data), and LaserStream (real-time streaming) makes it a full-stack indexing solution. Competitors (QuickNode, Triton) match some features but not the full breadth.

## How it relates to Logos
- Helius illustrates what a "full-stack indexing provider" looks like for a high-throughput chain. Logos would need something comparable — or could integrate with such providers at the cost of centralization.
- LaserStream's historical replay feature is a key UX insight: indexers need catch-up mechanisms for reconnection events. Logos's indexing design should account for this.
- The Enhanced WebSockets (50k address filters) shows developer demand for flexible, server-side filtering — a feature any Logos query layer should consider.
- See also: [[DAS API Standard]], [[Geyser Plugin Interface]], [[Yellowstone gRPC (Triton)]]

## Open Questions
- Is Helius profitable / sustainable as a business, or is it VC-funded with uncertain longevity?
- Does Helius have plans to expand beyond Solana (multi-chain)?
- How does Helius handle the tension between centralized convenience and the decentralization ethos of web3?

## Sources
- https://www.helius.dev/
- https://www.helius.dev/blog/solana-data-tools
- https://www.helius.dev/docs/getting-data
- https://www.helius.dev/docs/laserstream
- https://www.helius.dev/blog/introducing-next-generation-enhanced-websockets

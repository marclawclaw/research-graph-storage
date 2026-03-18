---
topic: Envio (HyperSync + HyperIndex)
type: competitor
tags: [indexing, competitor, envio, hypersync, hyperindex, evm, performance]
confidence: high
last_updated: 2026-03-18
sources:
  - https://docs.envio.dev/docs/HyperSync/overview
  - https://docs.envio.dev/docs/HyperIndex/overview
---

## Summary
Envio provides two tightly coupled products: HyperSync (a Rust-built, ultra-fast blockchain data retrieval layer replacing JSON-RPC) and HyperIndex (a full-featured indexing framework built on top of HyperSync). HyperSync claims up to 2000x faster data access than traditional RPC, supporting 70+ EVM chains. The developer experience is TypeScript/JS-native, making it a direct competitor to both The Graph and SQD for EVM-focused teams.

## Key Facts

### HyperSync
- Built in **Rust** from scratch; designed as a direct replacement for JSON-RPC
- Performance: up to **2000x faster** than JSON-RPC for historical data
  - Scan Arbitrum for sparse log data: Hours/Days (RPC) → 2 seconds (HyperSync) — ~2000x
  - Fetch all Uniswap v3 PoolCreated events on Ethereum: Hours → Seconds — ~500x
- Supports **70+ EVM chains** (and Fuel); constantly expanding
- Client libraries: Python, Rust, Node.js, Go
- Use cases: custom data pipelines, analytics, block explorers, ETL, monitoring

### HyperIndex
- Full-featured indexing framework built on HyperSync
- Provides: schema management, event handling, GraphQL API generation
- Powers 100+ production applications (e.g., v4.xyz analytics)
- Same GraphQL query pattern as The Graph — familiar to existing Graph users
- TypeScript/JavaScript native (no AssemblyScript)
- Comparison to The Graph: 100x faster indexing + multi-chain support

### Products Built on HyperSync
- **ChainDensity.xyz** — fast tx/event density analysis for any address
- **Scope.sh** — AA-focused block explorer using HyperSync for ultra-fast retrieval
- **LogTUI** — terminal UI for historical blockchain event search (20+ protocol presets)

### Hosted Service
- **HyperIndex Hosted Service** available — deploy without managing infrastructure
- API tokens required for HyperSync access

### Key Differentiators vs The Graph
| Feature | Envio HyperIndex | The Graph |
|---------|-----------------|-----------|
| Indexing speed | 100–2000x faster | Baseline |
| Language | TypeScript | AssemblyScript |
| Data source | HyperSync (Rust engine) | Graph Node (Firehose) |
| Chains | 70+ EVM + Fuel | 80+ (EVM + Solana) |
| Decentralisation | Hosted/centralised | Decentralised network |
| Payment | Not GRT-based | GRT |

> [!analysis] Envio's 2000x speed claim is compelling for analytics and indexing-heavy use cases. The trade-off is centralisation — there is no decentralised indexer network. For applications that need throughput over decentralisation, Envio is arguably the strongest EVM indexer as of 2025.

## How it relates to Logos
HyperSync's architecture — a purpose-built data retrieval engine separate from the indexing framework — mirrors what a Logos storage indexing layer might need. The key insight: don't rely on JSON-RPC / standard node APIs for data access; build a dedicated extraction layer. This is directly applicable to designing an indexing layer for [[Logos Ideas 19]] that reads from Logos Storage efficiently.

## Open Questions
- Is Envio's hosted service sufficiently reliable for production dApps that can't self-host?
- Does HyperSync support non-EVM chains (Solana, Cosmos)? Current docs suggest EVM + Fuel only.
- Is there a roadmap for decentralised query serving, or is Envio deliberately centralised-first?
- How does HyperSync's Rust engine compare to The Graph's Firehose in architecture?

## Sources
- https://docs.envio.dev/docs/HyperSync/overview
- https://docs.envio.dev/docs/HyperIndex/overview
- https://docs.envio.dev/

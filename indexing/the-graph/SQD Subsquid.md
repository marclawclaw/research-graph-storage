---
topic: SQD (Subsquid)
type: competitor
tags: [indexing, competitor, sqd, subsquid, evm, typescript, decentralized]
confidence: high
last_updated: 2026-03-18
sources:
  - https://docs.sqd.ai/sdk/subsquid-vs-thegraph/
  - https://www.gate.com/tr/crypto-wiki/article/what-is-subsquid-and-how-does-its-sqd-token-work-in-2025
---

## Summary
SQD (formerly Subsquid) is a decentralised data lake and indexing framework that competes directly with The Graph. It uses a modular architecture separating data extraction (SQD Network) from transformation (Squid SDK). The key developer differentiator is TypeScript-native indexing vs. The Graph's AssemblyScript, along with dramatically faster historical indexing speeds.

## Key Facts

### Architecture
- **SQD Network** — decentralised data lake; stores pre-extracted raw blockchain data; permissionless access
- **Squid SDK** — TypeScript-based transformation + presentation layer; consumes data from SQD Network
- Modular: data sourcing is separated from transformation (vs. The Graph's tightly coupled Graph Node)
- Also supports: Python DipDup SDK, Subgraph adapter (SQD Firehose), ApeWorx plugin

### Performance vs The Graph
| Metric | SQD | The Graph |
|--------|-----|-----------|
| Language | TypeScript | AssemblyScript (WASM) |
| Indexing speed | ~1k–50k blocks/sec | ~100–150 blocks/sec |
| Real-time (unfinalized blocks) | Yes | No |
| Off-chain data | Yes | No |
| Data targets | Customisable | Postgres only |
| Analytic targets | BigQuery, Parquet, CSV | No |
| Custom DB migrations | Yes | No |
| Multi-contract indexing | Yes | Limited |
| Payment | Fiat subscription | GRT pay-per-query |

### Token: SQD
- Work utility token for network operations
- AI agents (autonomous) access data via SQD tokens — no human in the loop
- Decentralised data sourcing via SQD Network; opt-in decentralised targets (Kwil DB, Ceramic)
- Decentralised processing: via Lava (in development as of 2025)
- ZK proofs for modular architecture security (as per CoinMarketCap description)

### Scale (2024 data)
- 1.2B+ cloud queries Q1 2024
- Full-stack blockchain indexing solution as of 2025

### DevEx Highlights
- No archival node needed for local setup (uses SQD Network data)
- Secret env variables (vs. The Graph: no)
- Custom GraphQL resolvers and mutations (vs. The Graph: no)
- Subscriptions built-in (The Graph: via middleware only)

> [!analysis] SQD's TypeScript-native approach and faster indexing speed are strong developer selling points, especially post-Sunrise when The Graph moved to paid GRT queries. SQD's fiat subscription model removes crypto-native friction for new developers.

## How it relates to Logos
SQD's modular architecture (network = data layer, SDK = transform layer) is a design pattern worth considering for a Logos indexing solution. The separation of concerns allows Logos Storage to serve as the data lake layer, with a separate transformation and query layer on top — very close to the [[Logos Ideas 19]] vision. SQD also shows that TypeScript-native tooling wins developer mindshare over WASM/AssemblyScript.

## Open Questions
- Is SQD Network sufficiently decentralised to be trust-minimised for production use?
- How does SQD's fiat pricing compare to GRT cost for high-volume production use?
- Is the Lava-based decentralised processing (in development) production-ready?
- Does SQD's Subgraph compatibility adapter (Firehose) enable seamless migration from The Graph?

## Sources
- https://docs.sqd.ai/sdk/subsquid-vs-thegraph/
- https://www.gate.com/tr/crypto-wiki/article/what-is-subsquid-and-how-does-its-sqd-token-work-in-2025
- https://reports.tiger-research.com/p/subsquid-eng

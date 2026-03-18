---
topic: The Graph Protocol
type: concept
tags: [indexing, blockchain, graphql, the-graph, evm, decentralized]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/docs/en/
  - https://en.wikipedia.org/wiki/The_Graph
  - https://thegraph.com/blog/the-graph-2024-recap/
---

## Summary
The Graph is an open-source, decentralized indexing protocol launched in 2018 that enables developers to build and query APIs (called subgraphs) for blockchain data. It supports 80+ chains and serves as the foundational data layer for web3 applications, analytics, and AI agents — commonly described as the "Google of blockchains."

## Key Facts
- Founded 2018 by Yaniv Tal, Brandon Ramirez, and Jannis Pohlmann (Edge & Node)
- Supports 80+ blockchain networks including Ethereum, Solana, Arbitrum, Base, Polygon, Optimism, Celo, Soneium, Avalanche
- Core products: **Subgraphs** (open APIs), **Substreams** (real-time streaming), **Token API** (no-index token data), **Graph Node** (indexing engine), **Firehose** (data extraction layer)
- Token: GRT (Graph Token) — work utility token for network operations and staking
- Migrated 100% of indexing rewards to **Arbitrum One** (L2) in 2024 to cut gas costs
- Hosted service **sunset June 12, 2024** — all queries now through decentralized Graph Network
- 10,000+ subgraphs live on the decentralised network post-Sunrise (AAVE, Balancer, ENS, SushiSwap, Uniswap)
- Oct 2025: Edge & Node launched **ampersend** — AI agent payment platform on Coinbase's x402 + Google's A2A
- 2025: CCIP integration for cross-chain GRT transfers (Solana, Arbitrum, Base)
- Jan 2025: **Geo Genesis** app launched — knowledge curation for web3 environments
- Mar 2025: **Token API beta** — real-time token balances, transfers, pricing data

## Architecture

### Components
1. **Firehose** — extraction layer; streams raw blockchain data as flat files; replaces RPC polling with push model; eliminates need for archive nodes
2. **Graph Node** — ingestion and indexing engine; executes subgraph WASM mappings; stores indexed data in Postgres; exposes GraphQL API
3. **Subgraph Studio** — developer interface; deploy, test, stage subgraphs; free with rate limiting; free tier: 100K queries/month
4. **Decentralized Network** — Indexers serve queries; consumers pay GRT; curation signals prioritize subgraphs
5. **Token API** — pre-indexed token data; no subgraph authorship needed

### Data Flow
Raw chain → Firehose (extract) → Graph Node (transform via WASM mappings) → Postgres (load) → GraphQL (query)

### Network Roles
- **Indexers** — operate nodes, stake GRT (min 100K GRT), earn query fees + indexing rewards (3% annual inflation)
- **Curators** — signal on subgraphs by staking GRT; earn 10% of query fees from curated subgraphs; indicate quality
- **Delegators** — stake GRT with Indexers without running infrastructure; earn proportional share of rewards
- **Fishermen** — open disputes; require 10K GRT deposit; earn 50% of slashed GRT if dispute accepted

### GRC-20 Knowledge Standard
Introduced 2024 — structures data into Spaces, Entities, Relations; analogous to ERC-20 for value transfer but for knowledge graphs; enables interoperable, dynamic data applications.

## How it relates to Logos
The Graph is the dominant EVM indexing pattern and reference architecture for any Logos-based indexing layer. [[Logos Ideas 19]] explores building a Supabase-equivalent on Logos Storage — The Graph's architecture (subgraph manifests, event watchers, GraphQL APIs) is the template to match or surpass. Key lessons:
- Event-based indexing (listen to contract events → transform → serve) is the proven pattern
- Decentralised query serving (Indexer/Curator/Delegator roles) shows how to incentivize honest data
- The GRC-20 knowledge standard is relevant for Logos's knowledge layer ambitions

## Open Questions
- Is the decentralised network genuinely used at scale, or do most teams use Subgraph Studio's free tier?
- How does query latency compare between Graph Network and a centralised Subgraph Studio endpoint?
- What is developer sentiment post-Sunrise migration? Did any teams defect to competitors?
- Does the 100K free query limit per month drive teams to self-host or switch to [[SQD]] / [[Envio HyperIndex]]?

## Sources
- https://thegraph.com/docs/en/
- https://en.wikipedia.org/wiki/The_Graph
- https://thegraph.com/blog/the-graph-2024-recap/
- https://thegraph.com/blog/sunsetting-hosted-service/
- https://thegraph.com/blog/transitioning-to-decentralized-graph-network/

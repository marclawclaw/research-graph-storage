---
topic: EVM Indexing Landscape
type: analysis
tags: [indexing, evm, landscape, comparison, the-graph, sqd, envio, covalent, alchemy]
confidence: medium
last_updated: 2026-03-18
sources:
  - https://docs.sqd.ai/sdk/subsquid-vs-thegraph/
  - https://docs.envio.dev/docs/HyperSync/overview
  - https://goldrush.dev/
  - https://www.spaceandtime.io/
---

## Summary
The EVM blockchain indexing landscape has fragmented significantly since The Graph's hosted service sunset in 2024. The Graph remains the most recognised brand and has the largest network of indexed subgraphs, but developer-facing competitors (SQD, Envio) have captured significant mindshare with faster, TypeScript-native tooling. Managed API providers (GoldRush, Alchemy, QuickNode) compete for the no-setup segment. Space and Time is carving out a ZK-verified analytics niche.

## Key Facts

### Competitor Positioning Map

| Product | Model | Language | Speed | Decentralised | Best For |
|---------|-------|----------|-------|---------------|----------|
| **The Graph** | Protocol + Studio | AssemblyScript | Medium | Yes (network) | Large-scale EVM + multi-chain |
| **SQD** | Modular data lake | TypeScript | High (50k bps) | Partial (data layer) | TypeScript devs, analytics, AI agents |
| **Envio HyperIndex** | Hosted indexer | TypeScript | Very High (2000x RPC) | No | EVM analytics + speed-critical apps |
| **GoldRush/Covalent** | Managed REST API | N/A (pre-built) | Medium | No | Wallets, explorers, no-setup apps |
| **Alchemy/QuickNode** | Managed RPC + APIs | N/A | Medium | No | RPC-first, dev tools, managed infra |
| **Space and Time** | ZK data blockchain | SQL | Varies | Partial | Finance, compliance, ZK-verified queries |
| **Dune Analytics** | SQL dashboards | SQL | Slow (batch) | No | Analytics/dashboards, not API |

### Consolidation Trends (2024–2025)
- The Graph's Sunrise forced migration → some developer churn to SQD and Envio
- SQD and Envio both offer TypeScript-native tooling — capturing developers frustrated with AssemblyScript
- GoldRush/Covalent rebranded — differentiating managed API from custom indexing
- Space and Time gaining traction in institutional DeFi
- Alchemy, QuickNode, Moralis compete primarily on RPC + enhanced APIs (not custom indexing)

### EVM-Specific Patterns
- Event log indexing: watch contract events → transform → persist → serve GraphQL/REST
- Factory contract patterns: index dynamically created contracts (pool creation, etc.)
- Trace-level data: available via Substreams (EVM) and Envio HyperSync; not standard in subgraphs
- Off-chain data integration: only SQD and Envio support this natively

### Multi-Chain Considerations
- The Graph: 80+ chains including Solana (via Substreams)
- Envio HyperSync: 70+ EVM chains + Fuel; no Solana
- SQD: EVM + expanding; strong on EVM-L2s
- GoldRush: 100+ chains

> [!analysis] The market is bifurcating: (1) developer-friendly, TypeScript-native indexers (SQD, Envio) gaining dev mindshare; (2) The Graph maintaining protocol-level decentralisation as differentiator. Neither has clearly won. The Sunrise migration was a strategic risk — if it accelerated competitor adoption, it may have permanently ceded some market share.

## How it relates to Logos
For [[Logos Ideas 19]], this landscape analysis reveals:
1. **TypeScript-native wins developer adoption** — any Logos indexing tool should be TypeScript-first
2. **Decentralisation is a differentiator, not a requirement** — start centralised, add decentralisation progressively
3. **GraphQL is table stakes** — users expect it; don't force SQL or custom query languages initially
4. **Speed matters** — HyperSync's 2000x claim resonates; a slow indexer loses to hosted alternatives
5. **Multi-chain by design** — Logos Storage could serve as a chain-agnostic data layer

## Open Questions
- Is there a genuine market for a trust-minimised (ZK or cryptographically verifiable) indexing layer?
- Does developer adoption of TypeScript tooling suggest AssemblyScript/Rust approaches have lost?
- What happens when Ethereum moves fully to statelessness? Does indexing architecture need to change?

## Sources
- https://docs.sqd.ai/sdk/subsquid-vs-thegraph/
- https://docs.envio.dev/docs/HyperSync/overview
- https://goldrush.dev/
- https://www.spaceandtime.io/

# Index — The Graph & EVM Indexing

**Phase 2 crawl completed:** 2026-03-18  
**Notes:** 8 atomic notes  
**Sources crawled:** 15+ (official docs, blog, Wikipedia, competitor docs, web searches)

---

## Notes

| File | Type | Summary |
|------|------|---------|
| [The Graph Protocol Architecture](./The%20Graph%20Protocol%20Architecture.md) | concept | Core architecture: Firehose → Graph Node → GraphQL. 80+ chains, Arbitrum L2 migration, GRC-20 knowledge standard. |
| [Subgraphs](./Subgraphs.md) | concept | Subgraph manifest + AssemblyScript mappings → WASM → GraphQL API. Developer lifecycle from Studio to decentralised network. |
| [Substreams](./Substreams.md) | concept | Rust-based parallelised streaming layer. 100x+ faster than subgraphs. Multi-sink (Postgres, ClickHouse, Mongo). Powers Solana support. |
| [GRT Tokenomics](./GRT%20Tokenomics.md) | concept | Indexers (min 100K GRT stake), Curators (10% query fee share), Delegators. 3% annual inflation for indexing rewards. TAP payment protocol. |
| [Decentralised Network vs Hosted Service](./Decentralised%20Network%20vs%20Hosted%20Service.md) | concept | Hosted service sunset June 12, 2024. Subgraph Studio = staging (free, 100K queries/month). Graph Network = production (GRT-paid). |
| [SQD Subsquid](./SQD%20Subsquid.md) | competitor | TypeScript-native, modular data lake. 1k–50k blocks/sec vs The Graph's 100–150. Fiat subscription model. Strong developer alternative. |
| [Envio HyperSync HyperIndex](./Envio%20HyperSync%20HyperIndex.md) | competitor | Rust-built HyperSync claims 2000x faster than RPC. HyperIndex is full indexing framework on top. 70+ EVM chains. TypeScript developer experience. |
| [GoldRush Covalent](./GoldRush%20Covalent.md) | competitor | REST-first managed API for 100+ chains. No custom indexing required. Pre-built endpoints for balances, transfers, NFTs. |
| [Space and Time](./Space%20and%20Time.md) | competitor | SQL + ZK coprocessor for verifiable query results. Targets institutional DeFi, compliance, and smart contracts that need provable data. |
| [EVM Indexing Landscape](./EVM%20Indexing%20Landscape.md) | analysis | Comparative analysis of all major EVM indexing solutions. Positioning map, trends, and implications for Logos. |

---

## Key Takeaways for Logos

1. **TypeScript wins devs** — SQD and Envio are taking mindshare from The Graph with TS-native tooling
2. **Speed is table stakes** — Envio's 2000x + SQD's 50k bps show what developers now expect
3. **Decentralisation ≠ adoption** — The Graph's decentralised network is aspirational; most usage is via Studio free tier
4. **GraphQL is expected** — any query layer should expose GraphQL as default
5. **ZK has a niche** — Space and Time shows there's a market for verifiable queries in institutional contexts

## Wikilinks
- [[The Graph Protocol Architecture]]
- [[Subgraphs]]
- [[Substreams]]
- [[GRT Tokenomics]]
- [[Decentralised Network vs Hosted Service]]
- [[SQD Subsquid]]
- [[Envio HyperSync HyperIndex]]
- [[GoldRush Covalent]]
- [[Space and Time]]
- [[EVM Indexing Landscape]]
- [[Logos Ideas 19]]

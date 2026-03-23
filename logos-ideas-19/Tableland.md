---
topic: Logos Ideas #19 — Supabase on Logos Storage
type: competitor
tags: [decentralized-database, sql, sqlite, evm, prior-art]
confidence: high
last_updated: 2026-03-19
sources:
  - https://tableland.xyz/
  - https://docs.tableland.xyz/fundamentals/why-sqlite
  - https://docs.tableland.xyz/fundamentals/architecture/protocol-design
---

## Summary
Tableland is a decentralised, ACID-compliant SQLite database that anchors write mutations to EVM blockchains. Smart contracts or frontends submit SQL writes as blockchain transactions (paying gas); the Tableland validator network processes them and updates a SQLite database. Reads are free and can be done from anywhere. It is live on Ethereum, Optimism, Arbitrum, Polygon. Most mature decentralised SQL layer for EVM apps.

## Key Facts
- **Architecture**: Two-layer design:
  1. **Write layer**: SQL write statements submitted as EVM transactions (gas = write cost). On-chain access control logic. Write ordering = blockchain ordering.
  2. **Read layer**: Tableland validator network maintains SQLite replicas. Any validator can answer read queries — reads are free and gasless.
- **Database engine**: SQLite. ACID-compliant. Full relational schema support.
- **Access control**: Wallet-based. Smart contract-controlled row/column write policies. Familiar EVM patterns.
- **Chain support**: Live on Ethereum, Optimism, Arbitrum, Arbitrum Nova, Polygon. Filecoin and zkEVMs announced.
- **Query interface**: Standard SQL. Read from any validator; write to chain.
- **Use cases shown**: Game state (hangman, chess), voting mechanisms, NFT metadata tables, key-value stores.
- **Limitations**: Writes require gas (blockchain tx). Write throughput limited by block rate. Cannot do low-latency writes (sub-second).

> [!fact] Confirmed from tableland.xyz
> "Tableland is an open source, permissionless cloud database built on SQLite. Read and write tamperproof data from apps, data pipelines, or EVM smart contracts."

> [!analysis] Analyst inference — not verified
> Tableland's architecture pattern maps cleanly to Logos: replace EVM blockchain with Logos Blockchain module for write anchoring, replace EVM validators with Logos validator nodes running SQLite replicas, use Logos Storage for persistent backup of SQLite snapshots. This is the cleanest architectural analogy for Ideas #19.

> [!analysis] Analyst inference — not verified
> The key insight from Tableland: you do NOT need fully decentralised query execution. You need decentralised write ordering (blockchain anchoring) + replication (validator network) + free reads. This separates concerns appropriately and is achievable with existing Logos primitives.

## How it relates to Logos
- **Pattern to adopt**: Logos blockchain module = write anchor. Logos storage module = WAL/snapshot backup. Logos messaging = replication gossip between validators.
- **Adaptation needed**: Tableland is EVM-native. Its smart contract ACL model doesn't transfer directly — Logos would need its own access control primitives.
- **Query layer is solved**: SQLite is battle-tested, fast, and portable. No need to invent a query engine.
- **Read from [[Logos Storage Primitives]]** — SQLite WAL files are blobs that could be stored on Codex.

## Open Questions
- What happens if all Tableland validators disappear? Is data recoverable from on-chain data alone?
- Has Tableland achieved meaningful developer adoption or is it still niche?
- Could a Logos fork of Tableland replace the EVM write layer with the Logos blockchain module?

## Sources
- https://tableland.xyz/
- https://docs.tableland.xyz/
- https://github.com/tablelandnetwork

---
topic: Logos Ideas #19 — Supabase on Logos Storage
type: competitor
tags: [decentralized-database, sql, postgresql, tendermint, prior-art]
confidence: high
last_updated: 2026-03-19
sources:
  - https://www.kwil.com/
  - https://github.com/trufnetwork/kwil-db
  - https://medium.com/kwildb/kwil-joins-chainlink-build-to-accelerate-adoption-of-decentralized-database-be2861dace1d
---

## Summary
Kwil is a decentralised SQL database built on PostgreSQL with Tendermint BFT consensus and a custom SQL smart contract language (Kuneiform). It is the most mature decentralised relational database project actively maintained, now under the TrufNetwork umbrella. Kwil supports typed schemas, SQL queries, wallet-based auth, and custom extensions. It does NOT use a decentralised blob storage layer — it uses PostgreSQL at each node.

## Key Facts
- **Architecture**: Each Kwil node runs PostgreSQL locally. Consensus via Tendermint BFT. Writes are replicated across nodes via consensus before committing to local Postgres.
- **Query language**: Standard SQL + "Kuneiform" smart contract language for defining tables, access control, and business logic on-chain.
- **Access control**: Wallet-based auth (Ethereum-style). Extensions support custom signature schemes.
- **Consensus**: Tendermint = Byzantine Fault Tolerant. Survives up to f < n/3 malicious nodes.
- **Current version**: v0.10.0 (trufnetwork/kwil-db on GitHub). Apache 2.0 licensed.
- **Extension system**: Oracles, custom auth, deterministic compute — pluggable.
- **Chainlink BUILD**: Kwil joined Chainlink BUILD programme — signals real ecosystem intent. Used by Truflation for multi-source economic data.
- **Go-based**: Node software written in Go. Requires PostgreSQL as a dependency.
- **Limitations**: Does NOT use decentralised storage. Each node stores its own full copy in Postgres. No content addressing or durability proofs. Centralisation risk = node set operators.

> [!fact] Confirmed from GitHub README (trufnetwork/kwil-db)
> "Built with PostgreSQL, Kwil enables scalable and high-integrity networks for web3 to be built on top of relational databases."

> [!analysis] Analyst inference — not verified
> Kwil is the strongest integration candidate for Logos Ideas #19. Its architecture could be adapted to use Logos Storage for persistence (replacing local Postgres files with Codex-stored snapshots) while keeping Tendermint consensus for write ordering. This is a "Kwil + Logos Storage backend" approach rather than building from scratch.

## How it relates to Logos
- **Integration path**: Replace Kwil's local PostgreSQL data files with Logos Storage-backed snapshots. Kwil handles SQL, consensus, and access control. Logos handles durable blob storage. This is feasible today with engineering effort.
- **Forking opportunity**: Fork kwil-db, add a Codex storage adapter for PostgreSQL data/WAL, expose the REST/GraphQL API. Would inherit Kwil's maturity instantly.
- **Risk**: Kwil's node model (PostgreSQL dependency) is heavyweight. A lighter document model (like ComposeDB) might be more appropriate for the Logos ecosystem's developer profile.
- **Read from [[Logos Storage Primitives]]** for what Codex can provide as a persistence layer.

## Open Questions
- Has any project attempted to use Kwil with an external storage backend (non-local Postgres)?
- What's Kwil's mainnet status and network size?
- Is there a way to run Kwil with SQLite instead of Postgres for a lighter-weight deployment?

## Sources
- https://www.kwil.com/
- https://github.com/trufnetwork/kwil-db
- https://docs.kwil.com/docs/concepts
- https://medium.com/kwildb/kwil-joins-chainlink-build-to-accelerate-adoption-of-decentralized-database-be2861dace1d

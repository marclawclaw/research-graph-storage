---
topic: Logos Ideas #19 — Supabase on Logos Storage
type: competitor
tags: [decentralized-database, ipfs, crdt, p2p, prior-art]
confidence: high
last_updated: 2026-03-19
sources:
  - https://github.com/orbitdb/orbitdb
  - https://arxiv.org/abs/2004.00107
---

## Summary
OrbitDB is a serverless, distributed, peer-to-peer database built on IPFS and libp2p. It uses Merkle-CRDTs (operation-based CRDTs backed by a Merkle DAG) for conflict-free replication. It provides four database types (events, documents, keyvalue, keyvalue-indexed) and supports custom types. OrbitDB is the closest existing implementation to what Logos Ideas #19 could look like at the persistence layer — if Logos Storage were substituted for IPFS.

## Key Facts
- **Architecture**: OpLog (immutable, CRDT-based operation log) backed by IPFS for storage. Libp2p Gossipsub for peer sync (pubsub-based replication).
- **Consistency model**: Eventually consistent. Merkle-CRDT guarantees convergence — all replicas eventually agree on the same state even with concurrent writes. No total ordering.
- **Database types**:
  - `events`: immutable append-only log. Useful for message queues, audit trails.
  - `documents`: JSON document store, indexed by a configurable key field.
  - `keyvalue`: simple KV store.
  - `keyvalue-indexed`: KV with LevelDB local index for efficient lookups.
- **Query capabilities**: Limited. Documents support `query()` with predicate functions (JavaScript), not SQL or GraphQL. No server-side query engine.
- **Language**: JavaScript only (Node.js + browser). Go implementation via berty/go-orbit-db.
- **Storage**: IPFS Helia (v2 API). Content-addressed. Persistence requires pinning.
- **Access control**: Built-in ACL framework. Custom access controllers supported.
- **Maintenance**: Actively maintained. Sponsored by Protocol Labs historically.
- **Production readiness**: Used in local-first and P2P apps. Not suitable for high-throughput production APIs due to eventual consistency and lack of structured queries.

> [!fact] Confirmed from GitHub README
> "OrbitDB is a serverless, distributed, peer-to-peer database. OrbitDB uses IPFS as its data storage and Libp2p Pubsub to automatically sync databases with peers."

> [!analysis] Analyst inference — not verified
> OrbitDB's architecture is directly portable to Logos Storage: replace IPFS with Codex (both are content-addressed P2P storage), keep libp2p Gossipsub (Logos Messaging module already uses libp2p). This would give an immediately working P2P document database. The gap is the query layer — OrbitDB's JavaScript predicates are not production-ready for a Supabase-equivalent.

> [!analysis] Analyst inference — not verified
> OrbitDB's Merkle-CRDT approach solves the conflict-free merge problem that any decentralised mutable database must solve. Logos Ideas #19 will need to adopt CRDTs or a different consistency mechanism. Total ordering via the Logos blockchain module is the alternative — write confirmation anchored to blocks.

## How it relates to Logos
- **Most relevant architectural reference** for the persistence and replication layer.
- **Replace IPFS with Codex**: Both are content-addressed. Codex adds economic durability guarantees IPFS lacks.
- **Keep libp2p**: Logos Messaging module is built on libp2p. Same transport layer. Zero friction.
- **Gap to fill**: Query layer (GraphQL/SQL), auth (wallet-based), admin dashboard, migrations — none of these exist in OrbitDB.
- **Pattern**: OrbitDB = lower 30% of what Ideas #19 needs. Build the upper 70% on top.

## Open Questions
- Can OrbitDB's storage adapters be swapped to use Codex instead of Helia/IPFS?
- What's the performance ceiling for OrbitDB document queries at scale (1M+ docs)?
- Is the Go port (berty/go-orbit-db) maintained enough for production use?

## Sources
- https://github.com/orbitdb/orbitdb
- https://github.com/berty/go-orbit-db
- https://arxiv.org/abs/2004.00107 (Merkle-CRDTs paper)

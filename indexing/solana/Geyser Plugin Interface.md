---
topic: Geyser Plugin Interface
type: concept
tags: [solana, geyser, streaming, validator, plugin, real-time]
confidence: high
last_updated: 2026-03-18
sources:
  - https://www.helius.dev/blog/solana-geyser-plugins-streaming-data-at-the-speed-of-light
  - https://docs.solanalabs.com/validator/geyser
  - https://docs.anza.xyz/validator/geyser
---

## Summary
The Solana Geyser Plugin Interface is a Rust trait built into the validator that allows external plugins to receive real-time streaming data (accounts, transactions, slots, block metadata, entries) as they are processed. It was introduced as a simpler alternative to the abandoned AccountsDB replica proposal and is the foundational low-level streaming primitive for the entire Solana indexing ecosystem.

## Key Facts
- **Defined by**: `GeyserPlugin` trait in the `solana-geyser-plugin-interface` crate.
- **Plugin format**: Dynamic shared library (`.so` file) loaded by the validator at startup via a JSON config file specifying `libpath`.
- **Streams**: accounts, transactions, slots, block metadata, entries.
- **Trigger callbacks**:
  - `update_account()` — fires whenever an account is updated at processed commitment level
  - `notify_transaction()` — fires on each transaction
  - `update_slot_status()` — fires on slot status changes (Processed → Confirmed → Rooted)
  - `notify_block_metadata()` — fires on block completion
  - `notify_entry()` — fires on each block entry
- **Commitment levels**: `processed` (highest slot worked on) → `confirmed` (supermajority vote) → `rooted` (permanent, canonical).
- **Performance**: As of Solana 1.16, callbacks use `&self` instead of `&mut self`, eliminating the need for a RW lock — significant throughput improvement.
- Replaced the `AccountsDB Replica` proposal which required a separate synchronization service.
- Geyser plugins redirect data to external stores: relational DBs (Postgres), NoSQL, Kafka, or custom gRPC servers.
- Running a Geyser plugin requires operating your own validator or a dedicated node — cannot be used against public RPC endpoints.

> [!fact] Confirmed from official docs
> The Geyser plugin interface is declared in `solana-geyser-plugin-interface` crate; the trait is the canonical extension point.

> [!analysis] Operational constraint
> Geyser requires running a full validator node. This creates a significant barrier — most teams rely on providers like Helius (LaserStream), Triton (Yellowstone gRPC), or QuickNode instead of running their own.

## How it relates to Logos
- Geyser is the lowest-level streaming primitive in Solana. A comparable design for Logos would be a protocol-level hook that emits state change events as nodes process transactions — enabling external indexers without full node replication.
- The Geyser pattern shows the trade-off: flexibility (any plugin) vs. operational burden (must run a validator). Logos's design should consider whether a Geyser-like plugin interface is needed or if a higher-level abstraction (like DAS) suffices.

## Open Questions
- Is the Geyser interface stable enough for production use, or does it break between Solana releases?
- Can Geyser plugins be used with RPC-only nodes (not full validators)?
- Is there an equivalent streaming interface in Agave (the new Solana validator client)?

## Sources
- https://www.helius.dev/blog/solana-geyser-plugins-streaming-data-at-the-speed-of-light
- https://docs.solanalabs.com/validator/geyser
- https://docs.anza.xyz/validator/geyser

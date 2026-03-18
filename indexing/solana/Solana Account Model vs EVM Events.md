---
topic: Solana Account Model vs EVM Events
type: concept
tags: [solana, evm, account-model, indexing, architecture]
confidence: high
last_updated: 2026-03-18
sources:
  - https://solana.com/developers/evm-to-svm/accounts
  - https://www.helius.dev/blog/solana-data-tools
  - https://rareskills.io/post/solana-logs-transaction-history
---

## Summary
Solana uses a universal account-based model where all state (programs, data, tokens) is stored in accounts with explicit ownership. Unlike EVM chains which emit discrete indexed event logs from contract execution, Solana programs write to accounts and use log messages — meaning event-based indexing patterns common on Ethereum do not map directly to Solana.

## Key Facts
- **EVM model**: Smart contracts emit `event` logs with indexed/non-indexed fields; indexers (The Graph, etc.) filter events by signature and index them into queryable stores.
- **Solana model**: Everything is an account. Programs (smart contracts) are stateless executables stored in executable accounts; state lives in separate data accounts (PDAs — Program Derived Addresses).
- Solana accounts have fields: `lamports`, `owner` (program), `executable` (bool), `data` (raw bytes), `rent_epoch`.
- There is no native concept of "indexed" vs "non-indexed" fields in Solana logs (unlike EVM's `indexed` keyword).
- Solana uses `msg!()` for log output and the `emit!` macro (via Anchor framework) to serialize structured events into logs — but these are opaque byte strings without a standardized ABI encoding.
- Transaction logs are accessible via `getTransaction` RPC but are ephemeral; long-term history requires archival solutions.
- Anchor framework (most popular Solana dev framework) provides IDL (Interface Definition Language) for decoding instructions and events — analogous to Ethereum ABI.
- Solana's parallel execution (Sealevel) means multiple transactions can touch different accounts simultaneously — complicating global state reconstruction for indexers.

> [!fact] Confirmed from official docs
> Solana docs explicitly state all data is stored in accounts; programs are stateless. There is no equivalent of Ethereum's event log bloom filter.

> [!analysis] Indexing implication
> Indexers must track account state diffs, not event emissions. This requires either Geyser plugins (real-time) or RPC polling (slow, expensive). The Graph's subgraph model can't be applied directly without modification.

## How it relates to Logos
- Logos is building a decentralized storage and compute stack. If Logos wants a query layer (Ideas #19), it faces the same fundamental problem: there's no standardized event model, so indexers must watch state changes.
- The Solana approach (Geyser + DAS) illustrates how a high-throughput chain solves this without native event indexing — relevant for designing Logos's own data layer.
- Wikilink to [[Geyser Plugin Interface]] for the streaming solution Solana chose.

## Open Questions
- Will Solana ever standardize event emissions with a first-class ABI like Ethereum?
- Does the Anchor IDL become a de-facto standard for event decoding across all Solana dApps?
- How do non-Anchor programs (raw BPF) get indexed — is there a solution beyond custom parsers?

## Sources
- https://solana.com/developers/evm-to-svm/accounts
- https://www.helius.dev/blog/solana-data-tools
- https://rareskills.io/post/solana-logs-transaction-history

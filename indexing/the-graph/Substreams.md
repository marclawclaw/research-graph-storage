---
topic: Substreams
type: concept
tags: [indexing, the-graph, streaming, rust, parallel, solana, evm]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/docs/en/substreams/introduction/
  - https://thegraph.com/blog/indexing-solana-substreams/
---

## Summary
Substreams is a high-performance, parallelised blockchain data streaming technology developed by StreamingFast (a core Graph ecosystem developer). Unlike subgraphs (which process events sequentially in WASM), Substreams modules are written in Rust, compiled to WASM, and executed in parallel — enabling 100x+ faster historical sync. Substreams can feed into subgraphs, Postgres, ClickHouse, or MongoDB.

## Key Facts
- Developed by **StreamingFast** (core dev team funded by The Graph Foundation)
- Language: **Rust** (compiled to WASM)
- Execution: **Parallelised** — horizontally scalable; not constrained to sequential block processing
- Built on top of **Firehose** (data extraction layer); Firehose = pull raw data from nodes, Substreams = transform layer
- Analogy: Firehose = Extract, Substreams = Transform, Subgraphs = Load + Query (full ETL+Q)
- Supported chains: EVM + Solana, Injective, Starknet, Vara (multi-chain, not EVM-only)
- Indexing speed benchmark: 100x+ faster historical processing vs. standard subgraphs
- **Multi-sink support**: Subgraphs, Postgres, ClickHouse, MongoDB
- Fully open-source; composable — modules reuse each other's output streams
- Free hosted service until deployed on The Graph Network

## How it works (4 steps)
1. Write Rust transformation function (e.g., extract block number/hash from raw block struct)
2. Compile to WASM with single CLI command
3. WASM container sent to Substreams endpoint → provider feeds blockchain data → transformations applied in parallel
4. Route output to a sink (subgraph, SQL DB, etc.)

## Substreams vs Subgraphs

| Dimension | Substreams | Subgraphs |
|-----------|-----------|-----------|
| Language | Rust | AssemblyScript |
| Processing | Parallel | Sequential |
| Speed | 100x+ faster historical | ~100–150 bps |
| Sinks | Multi (Postgres, ClickHouse, Mongo, Subgraph) | Postgres only |
| Off-chain data | Yes | No |
| Chains | Multi (EVM + Solana, etc.) | EVM-first |
| DevEx | More complex (Rust) | Simpler (AssemblyScript) |

> [!analysis] Substreams is the high-performance tier — best for analytics, cross-chain apps, or any indexing that needs speed at scale. Subgraphs remain the simpler path for straightforward EVM event indexing.

## Solana Support
- The Graph launched Solana support via Substreams in 2024
- Substreams can access Solana account changes, transaction data, program logs
- Enables "fast, no-code indexing for Solana" — hours instead of weeks vs custom Rust solutions
- First step toward full subgraph support on Solana

## How it relates to Logos
If Logos wants to build a high-performance indexing layer for its storage/compute stack, Substreams' architecture (parallelised Rust modules, multi-sink, composable streams) is the strongest existing template. The key innovation is the **composability** — developers reuse each other's stream transformations, creating a data lego ecosystem. This pattern is worth considering for [[Logos Ideas 19]].

## Open Questions
- Is Substreams mature enough for production use outside The Graph ecosystem?
- How does it compare to SQD Network's decentralised data lake approach for the same workloads?
- Does the Rust requirement for Substreams modules create a developer bottleneck?

## Sources
- https://thegraph.com/docs/en/substreams/introduction/
- https://thegraph.com/blog/indexing-solana-substreams/
- https://docs.substreams.dev (maintained separately by StreamingFast)

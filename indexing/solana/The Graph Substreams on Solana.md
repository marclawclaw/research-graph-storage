---
topic: The Graph Substreams on Solana
type: concept
tags: [solana, the-graph, substreams, indexing, grpc, rust, cross-chain]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/blog/indexing-solana-substreams/
  - https://solanacompass.com/projects/the-graph
---

## Summary
The Graph extended to Solana in 2023 via the Substreams technology (developed by StreamingFast), rather than the traditional subgraph approach. Substreams use Rust modules compiled to WebAssembly for parallel, stateful historical indexing at up to 100x faster sync speeds than RPC-based indexing — addressing Solana's lack of native event logs.

## Key Facts
- **Why Substreams, not Subgraphs**: Solana's account model does not emit discrete event logs like EVM; subgraphs (AssemblyScript, event-driven) don't map cleanly. Substreams are more flexible and can handle account state diffs.
- **Technology**:
  - Modules written in **Rust** (compiled to WebAssembly/BPF)
  - Backed by **Firehose** — a push-based data extraction layer replacing RPC polling
  - Stateful modules: can aggregate across chain history in parallel
  - Output feeds into **sinks**: Postgres, MongoDB, graph-node (subgraph), custom gRPC consumers
- **Performance**: Historical indexing 100x+ faster than RPC-based approaches due to horizontal parallelization.
- **Composability**: Modules are composable — one team's price module can be combined with another's sales module at transformation time, not query time.
- **Determinism + caching**: Substreams are fully deterministic; previously executed modules are cached. Jump to any point in history without reprocessing.
- **Cursor-based reliability**: Every streamed payload includes a cursor. On reconnection, send cursor to resume exactly — prevents missing reorgs even during disconnection.
- **Solana program code reuse**: Since programs are written in Rust, the same code used for on-chain validation can be reused in a substream module for decoding.
- **Free hosted service**: Available until deployed on The Graph's decentralized network.
- **Adoption on Solana**: Via Solana Compass — GRT token staking, ~$700M TVL in protocol; "hundreds of applications across DeFi, NFTs."

> [!fact] Confirmed from The Graph official blog
> Substreams on Solana launched in 2023; Firehose provides the extraction layer.

> [!analysis] Adoption uncertainty
> The Graph's Solana integration is technically mature but The Graph's decentralized network is EVM-focused (migrated to Arbitrum). Solana substreams currently run on hosted/centralized infrastructure. Real decentralized Solana indexing via The Graph remains a future goal.

> [!outdated] Check status
> This announcement dates to 2023. Verify current state of The Graph's Solana decentralized network support in 2026.

## How it relates to Logos
- Substreams' ETL model (Firehose = extract, Substreams = transform, Sinks = load + query) is the most principled architecture for indexing non-EVM chains. A Logos query layer would benefit from a similar separation.
- The cursor-based resume mechanism is a key reliability pattern for any decentralized indexer — essential for production systems.
- Composable modules (build on others' work) directly parallels the Logos composability goal.
- See also: [[Solana Account Model vs EVM Events]], [[Cross-Chain Indexing Patterns]]

## Open Questions
- Has The Graph's Solana support matured to full decentralized network participation, or still hosted-only?
- What is real developer adoption on Solana vs EVM chains for The Graph?
- Is StreamingFast (Firehose/Substreams) still independent or fully merged into The Graph ecosystem?

## Sources
- https://thegraph.com/blog/indexing-solana-substreams/
- https://solanacompass.com/projects/the-graph

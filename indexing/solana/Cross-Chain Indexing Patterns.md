---
topic: Cross-Chain Indexing Patterns
type: analysis
tags: [cross-chain, multichain, indexing, solana, evm, sqd, goldsky, substreams, patterns]
confidence: medium
last_updated: 2026-03-18
sources:
  - https://blog.sqd.dev/how-gmx-accelerated-cross-chain-indexing-with-sqd/
  - https://blog.sqd.dev/the-top-five-solana-infrastructure-projects/
  - https://goldsky.com/chains/solana
  - https://www.alchemy.com/dapps/best/indexing-tools
---

## Summary
Cross-chain indexing is the challenge of building a unified data layer that spans multiple blockchains with fundamentally different data models (EVM event logs, Solana account diffs, Substrate extrinsics, etc.). The dominant pattern in 2024-2025 is a unified SDK/processor that abstracts over chain-specific extraction layers, feeding into a common transformation and storage pipeline.

## Key Facts

### Approaches
1. **Chain-specific specialists** (Helius for Solana, The Graph for EVM) — highest performance for one chain, no cross-chain story.
2. **Unified multi-chain indexers**:
   - **SQD (Subsquid)**: Data lake supporting EVM, Substrate, Solana. TypeScript-based processors. 140k blocks/sec sync. Used by GMX across Arbitrum, Avalanche, Solana, Base, BNB Chain.
   - **Goldsky**: Supports 150+ chains including Solana. "Turbo Pipelines" with WebAssembly transforms. "Mirror" for direct DB streaming. TypeScript-based.
   - **The Graph Substreams**: Rust/WASM modules + Firehose. Designed for cross-chain composability. Used for EVM and Solana.
3. **Managed analytics** (Dune, Flipside): SQL-based, ~1-60 min delay, good for analytics not production APIs.

### Key cross-chain challenges
- **Different data models**: EVM events vs Solana account diffs vs Substrate extrinsics. Each requires a different extraction layer.
- **Synchronization across chains**: Multi-chain apps need to correlate events from different chains (e.g., bridge deposits + withdrawals). Requires ordering across different block times and finality models.
- **Reorg handling**: EVM has short reorgs (usually <1 block), Solana rarely reorgs but has different commitment levels (processed/confirmed/rooted). Indexers must handle all cases.
- **Historical sync speed**: EVM archive nodes are slow via RPC; Solana's history is massive. Dedicated extraction layers (Firehose, SQD data lake) are essential.

### GMX case study (SQD)
- GMX expanded across Arbitrum, Avalanche, Botanix, Solana, Base, BNB Chain.
- Previous subgraph-based approach: one handler per event, complex synchronization, slow debugging.
- SQD: batch processing via EVM processor, custom resolvers, TypeScript debugging locally.
- Key fix: switching to `wss://` (WebSocket) reduced latency significantly.
- Result: faster data delivery, smoother UI, lower infra costs.

> [!fact] Confirmed from SQD blog (Nov 2025)
> GMX moved from The Graph subgraphs to SQD for multi-chain indexing. SQD supports Solana as of 2024.

> [!analysis] Pattern emerging
> The trend is toward unified SDK-based indexers (SQD, Goldsky) that hide chain differences behind a common TypeScript/WASM processing layer. Chain-specific high-performance needs (MEV, trading) still use specialized providers (Helius, Triton).

## How it relates to Logos
- A Logos query layer (Ideas #19) targeting a multi-chain future must choose: build chain-specific or adopt a unified approach.
- SQD and Goldsky demonstrate that TypeScript + batch processing is viable for production cross-chain workloads — this is the builder-friendly approach.
- Solana's approach (Geyser → gRPC → custom processor) shows the full performance-oriented stack — appropriate for latency-sensitive use cases.
- The key insight: **extraction and transformation should be separate layers** (Firehose/Geyser = extract; substreams/processors = transform; sinks/DBs = load). Logos should design similarly.
- See also: [[The Graph Substreams on Solana]], [[Geyser Plugin Interface]]

## Open Questions
- Is SQD's Solana support mature enough for production NFT/DeFi use cases?
- Does Goldsky support Solana's compressed NFTs (DAS-equivalent)?
- Can cross-chain indexers handle Solana's ~400ms slot time without adding significant latency?

## Sources
- https://blog.sqd.dev/how-gmx-accelerated-cross-chain-indexing-with-sqd/
- https://blog.sqd.dev/the-top-five-solana-infrastructure-projects/
- https://goldsky.com/chains/solana
- https://www.alchemy.com/dapps/best/indexing-tools

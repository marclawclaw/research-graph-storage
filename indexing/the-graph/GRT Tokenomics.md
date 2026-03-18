---
topic: GRT Tokenomics
type: concept
tags: [tokenomics, the-graph, grt, staking, economics, indexers, curators, delegators]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/docs/en/indexing/overview/
  - https://messari.io/report/state-of-the-graph-q2-2025
  - https://www.okx.com/en-us/learn/what-is-grt-the-graph-crypto
---

## Summary
GRT is The Graph's native work utility token. It aligns network participants (Indexers, Curators, Delegators) through staking and economic incentives. Indexers stake GRT to run nodes and earn query fees plus inflation-based indexing rewards. Curators signal quality subgraphs with GRT and earn a cut of query fees. Delegators outsource staking to Indexers and share in rewards without running infrastructure.

## Key Facts

### Supply & Inflation
- Protocol-wide inflation: **3% annual issuance** — allocated as indexing rewards
- Rewards distributed across subgraphs proportionally to their curation signal
- Within each subgraph, distributed proportionally to Indexers by allocated stake
- Rewards require valid **Proof of Indexing (POI)** to be eligible
- POI: digest of all entity store transactions for a subgraph deployment up to a given block

### Indexers
- Minimum stake: **100,000 GRT**
- Revenue streams:
  1. **Query fee rebates** — paid by consumers; mediated via GraphTally (Timeline Aggregation Protocol)
  2. **Indexing rewards** — from 3% annual protocol inflation
- Allocation lifetime: max **28 epochs** (~28 days); must close with valid POI to earn rewards
- Slashing: GRT staked can be slashed for malicious indexing or incorrect data
- Select subgraphs to index based on curation signal

### Curators
- Stake GRT to signal on valuable subgraphs
- Earn **10% of query fees** from curated subgraphs
- Signal directs Indexers toward high-quality, high-demand subgraphs

### Delegators
- Delegate GRT to Indexers without running infrastructure
- Earn proportional share of Indexer query fees + indexing rewards
- No minimum (can delegate any amount)

### Timeline Aggregation Protocol (TAP)
- Launched 2024; replaces Scalar payment system
- Consolidates micropayments into **Receipt Aggregate Vouchers (RAVs)** — batch on-chain payments
- Reduces on-chain transaction costs; Indexers have greater receipt control
- Improves performance and trustlessness of query payment flow

### Disputes (Fishermen)
- Any participant can dispute Indexer queries/allocations
- Requires 10,000 GRT deposit from disputing party
- Query/attestation disputes: 7 epoch window
- Allocation disputes: 56 epoch window
- If dispute accepted: disputing party earns 50% of slashed GRT; Indexer slashed

### L2 Migration
- All indexing rewards now issued on **Arbitrum One** (completed 2024)
- 99%+ of subgraphs on L2
- Eliminates Ethereum mainnet gas costs; significantly faster transactions

## How it relates to Logos
Logos Ideas 19 envisions a queryable data layer — The Graph's economic model (stake-to-index, curate-to-signal, delegate-to-participate) provides a reference for how to incentivize honest, performant indexing in a decentralised system. However, for a PoC or developer-tool context, a simpler fee model (subscription or flat API key) may be preferable. The GRT tokenomics are complex and not necessary for initial feasibility research on [[Logos Ideas 19]].

## Open Questions
- What proportion of GRT queries are actually paid on the decentralised network vs. free Studio tier?
- Are indexing rewards sufficient to attract enough Indexers for long-tail subgraphs?
- How does TAP (RAV batching) affect query latency vs. the old pay-per-query Scalar model?
- Is the 100K free query limit on Studio a strategic moat or a barrier to adoption?

## Sources
- https://thegraph.com/docs/en/indexing/overview/
- https://messari.io/report/state-of-the-graph-q2-2025
- https://www.okx.com/en-us/learn/what-is-grt-the-graph-crypto
- https://forum.thegraph.com/t/mainnet-release-of-tap-and-indexer-service-rs/6038

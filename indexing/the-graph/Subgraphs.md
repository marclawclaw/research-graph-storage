---
topic: Subgraphs
type: concept
tags: [indexing, the-graph, graphql, subgraph, assemblyscript, evm]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/docs/en/subgraphs/quick-start/
  - https://docs.chainstack.com/docs/subgraphs-tutorial-a-beginners-guide-to-getting-started-with-the-graph
---

## Summary
Subgraphs are open APIs that define how blockchain data is extracted, processed, and served via GraphQL. Developers write a manifest (subgraph.yaml), a schema (schema.graphql), and AssemblyScript mappings to transform on-chain events into queryable entities. Subgraphs are the primary developer-facing product of The Graph.

## Key Facts
- Three core files per subgraph:
  1. **subgraph.yaml** — manifest; defines data sources, networks, event handlers, start block
  2. **schema.graphql** — entity types and fields; defines what data is queryable
  3. **mapping.ts** (AssemblyScript) — event handler logic; translates raw events to schema entities
- Compiled to **WebAssembly (WASM)** for execution inside Graph Node — sandboxed, deterministic
- Deployed via **Subgraph Studio** for testing; published on-chain to become available on The Graph Network
- On publication: subgraph becomes indexable by decentralised Indexers; rate limits removed; publicly queryable
- **Upgrade Indexer** (Edge & Node operated): single centralised indexer for Studio-only deployments; free, rate-limited
- Published subgraphs require GRT curation signal to attract decentralised Indexers
- Subgraph slug format: `SubgraphName ChainName` (Title Case recommended)
- Free tier: 100,000 queries/month via Studio
- Supports EVM chains + (via Substreams) Solana, NEAR, Starknet, Injective, Vara
- Toolchain: `graph-cli` npm package (`graph init`, `graph codegen`, `graph build`, `graph deploy`)
- ABI-based code generation: auto-generates TypeScript types from contract ABI

## Lifecycle
1. `graph init` — scaffold from existing contract + ABI
2. `graph codegen` — generate AssemblyScript types
3. `graph build` — compile WASM
4. `graph deploy` — push to Subgraph Studio (free, dev/staging)
5. Publish on-chain → live on decentralised network

## Limitations vs Substreams
- Sequential (non-parallelised) processing — ~100–150 blocks/sec
- AssemblyScript only — no TypeScript, no npm libraries
- Postgres-only data target
- No off-chain data sources
- No real-time indexing of unfinalized blocks
- No custom DB migrations

> [!analysis] Subgraphs are the established developer pattern but trade flexibility for simplicity. For high-throughput or multi-target use cases, [[Substreams]] or [[SQD]] are stronger options.

## How it relates to Logos
[[Logos Ideas 19]] proposes a structured data + query API on top of Logos Storage. Subgraphs show the proven DevEx pattern: manifest → schema → handlers → GraphQL. A Logos indexer would benefit from a similar developer experience. Key takeaway: the complexity of AssemblyScript/WASM is a pain point — TypeScript-native alternatives (SQD, Envio) are gaining ground.

## Open Questions
- Why AssemblyScript instead of Rust or TypeScript? (Legacy decision from early WASM support)
- Can subgraphs be extended to support non-EVM chains without Substreams?
- Is the WASM execution environment a security concern or just a performance trade-off?

## Sources
- https://thegraph.com/docs/en/subgraphs/quick-start/
- https://docs.sqd.ai/sdk/subsquid-vs-thegraph/

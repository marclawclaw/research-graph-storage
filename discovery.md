# Discovery Report — Blockchain Indexing & Decentralized Storage

**Date:** 2026-03-18  
**Status:** Phase 1 complete — cron jobs scheduled for deep crawl  
**Repo:** https://github.com/marclawclaw/research-graph-storage

---

## Research Scope

Four topics identified, scheduled across 18 hours:

| # | Topic | Folder | Cron fire |
|---|-------|--------|-----------|
| 1 | The Graph & EVM Indexing | `indexing/the-graph/` | T+0h (immediate) |
| 2 | Solana Indexing Ecosystem | `indexing/solana/` | T+6h |
| 3 | Decentralized Storage | `storage/` | T+12h |
| 4 | Logos Ideas #19 Feasibility | `logos-ideas-19/` | T+18h |

---

## Topic 1 — The Graph & EVM Indexing

### What it is
The Graph is a decentralized indexing protocol. Developers write **subgraphs** — JSON manifests that describe which smart contract events/calls to watch. A Graph Node ingests blockchain data, processes it through user-defined mappings (AssemblyScript), and exposes a **GraphQL API**.

### Key concepts to research
- Subgraph manifest structure and lifecycle
- Graph Node architecture (block ingestor, indexer, query node)
- Substreams — higher-throughput streaming alternative to subgraphs
- Decentralized Network vs. hosted/Subgraph Studio
- GRT token economics (Indexers, Curators, Delegators)
- Migration to Arbitrum One (completed 2024)
- 195B+ queries/month as of 2024

### Sources identified

| Source | URL | Type |
|--------|-----|------|
| Official docs | https://thegraph.com/docs/ | Docs |
| Official blog | https://thegraph.com/blog/ | Blog |
| 2024 year-in-review | https://thegraph.com/blog/the-graph-2024-recap/ | Blog |
| GitHub org | https://github.com/graphprotocol | GitHub |
| Solana substreams blog | https://thegraph.com/blog/indexing-solana-substreams/ | Blog |
| Messari profile | https://messari.io/project/the-graph/profile | Analysis |
| Wikipedia (overview) | https://en.wikipedia.org/wiki/The_Graph | Overview |
| AWS + The Graph | https://aws.amazon.com/blogs/web3/gain-insights-from-web3-data-with-the-graph-and-amazon-managed-blockchain/ | Blog |
| Chainstack tutorial | https://docs.chainstack.com/docs/subgraphs-tutorial-a-beginners-guide-to-getting-started-with-the-graph | Docs |

### Competing / alternative indexers (EVM-focused)
- **SQD (Subsquid)** — modular, Node.js-native, 1.2B cloud queries Q1 2024. Comparison: https://docs.sqd.ai/sdk/subsquid-vs-thegraph/
- **Envio + HyperSync** — EVM-only, multi-chain GraphQL, accelerated sync vs JSON-RPC. Docs: https://docs.envio.dev/
- **Covalent / GoldRush** — unified multi-chain API, no subgraph required, REST-first
- **Alchemy, QuickNode, Moralis** — managed APIs, less decentralized
- **Space and Time** — SQL interface, ZK proofs on query results
- **Dune Analytics** — SQL-based, community dashboards, not developer-facing API
- **SubQuery** — strong in Polkadot/Cosmos ecosystem

### Open questions
- Is The Graph's decentralized network meaningfully used vs. Subgraph Studio (centralized)?
- How does Substreams compare to subgraphs for throughput-sensitive apps?
- Developer sentiment on subgraph migration (hosted → Studio → network)?

---

## Topic 2 — Solana Indexing Ecosystem

### What it is
Solana's account-based model (vs. EVM's event logs) requires different indexing approaches. No native equivalent of The Graph dominated initially — the ecosystem fragmented into RPC providers, custom indexers, and Geyser plugin systems.

### Key concepts to research
- Solana account model vs. EVM event model (why standard subgraphs don't map cleanly)
- Geyser plugin interface — low-level streaming hook for validators
- Yellowstone gRPC (Triton) — production-grade Geyser consumer
- DAS (Digital Asset Standard) API — NFT/token indexing, Helius implementation
- Helius — RPC + enhanced APIs + webhooks + DAS; dominant Solana dev platform
- Triton One — lowest latency RPC, Yellowstone gRPC for real-time feeds
- The Graph on Solana — Substreams-based integration (2024 expansion)

### Sources identified

| Source | URL | Type |
|--------|-----|------|
| Helius data tools guide | https://www.helius.dev/blog/solana-data-tools | Blog |
| Helius docs (Getting Data) | https://www.helius.dev/docs/getting-data | Docs |
| Helius homepage | https://www.helius.dev/ | Product |
| Triton / Yellowstone gRPC | https://github.com/rpcpool/yellowstone-grpc | GitHub |
| The Graph on Solana | https://thegraph.com/blog/indexing-solana-substreams/ | Blog |
| Solana Stack Exchange thread | https://solana.stackexchange.com/questions/22043/data-indexer-for-solana-similar-to-the-graph | Community |
| Solana Compass - The Graph | https://solanacompass.com/projects/the-graph | Analysis |
| RPC comparison (slerf.tools) | https://blog.slerf.tools/en-us/solana-rpc-evaluation-a-comprehensive-review/ | Analysis |
| Top RPC providers | https://dysnix.com/blog/solana-node-providers | Analysis |

### Open questions
- Is Helius's DAS API becoming the de-facto indexing standard for Solana NFT/token data?
- Does The Graph's Substreams approach on Solana have real adoption or is it fringe?
- What do high-frequency apps (MEV bots, perps) use vs. analytics teams?

---

## Topic 3 — Decentralized Storage

### What it is
A landscape of protocols for storing data outside centralized cloud providers — content-addressed, incentivized, or permanent.

### Key concepts to research
- **IPFS** — content-addressed P2P network; no native incentive layer; needs pinning services (Pinata, web3.storage, Infura)
- **Filecoin** — incentive layer on top of IPFS; time-bound storage contracts; enterprise-grade; 804+ large clients (2024)
- **Arweave** — "blockweave"; one-time endowment fee = permanent storage; no renewal required; strong Solana NFT adoption
- **Shadow Drive (GenesysGo)** — Solana-native object storage; alternative to Arweave/IPFS for Solana builders
- **Storj** — S3-compatible, erasure coding, usage-based pricing
- **DePIN growth** — storage sector grew $5.2B → $19B market cap (2024→Sep 2025)
- **Use cases**: NFT metadata, dApp frontends, archival, validator history (Solana recommends Arweave)

### Solana storage patterns
- Solana NFT metadata: on-chain PDA with URI pointing to Arweave/IPFS/Shadow Drive
- Arweave is recommended by Solana Foundation for validator ledger archiving
- Bundlr (now Irys) — Arweave upload service with Solana payment support

### Sources identified

| Source | URL | Type |
|--------|-----|------|
| IPFS docs comparisons | https://docs.ipfs.tech/concepts/comparisons/ | Docs |
| Dev.to: IPFS vs Arweave vs Filecoin | https://dev.to/raji_moshood_ee3a4c2638f6/decentralized-storage-wars-ipfs-vs-arweave-vs-filecoin-52c3 | Blog |
| NFT storage patterns (QuickNode) | https://www.quicknode.com/guides/solana-development/nfts/solana-nft-metadata-deep-dive | Docs |
| Shadow Drive explainer | https://solanacompass.com/learn/Solfate/decentralized-cloud-storage-on-the-solana-network-introducing-shadow-drive-v2-64 | Blog |
| DePIN boom 2026 | https://adipek.com/articles/the-web3-storage-war-is-here-why-decentralized-files-systems-are-suddenly-everywhere-in-2026 | Analysis |
| Arweave vs Filecoin vs Sia (NFT) | https://nftbirdies.com/article/arweave-filecoin-and-sia-where-to-store-nft-metadata-and-files-in-web3/ | Analysis |
| 9 decentralized storage solutions | https://thetechtrends.tech/decentralized-storage-solutions/ | Overview |
| Top 5 solutions (gate.com) | https://www.gate.com/learn/articles/top-5-decentralized-storage-solutions/6183 | Overview |

### Open questions
- Is Filecoin being used beyond archival / large-dataset clients?
- How does Shadow Drive V2 compare to Arweave for typical Solana dApp needs?
- Is there a convergence happening (IPFS + Filecoin + hot layer) for production apps?

---

## Topic 4 — Logos Ideas #19: Supabase on Logos Storage (Feasibility)

### What it is
GitHub issue: https://github.com/logos-co/ideas/issues/19  
**Title:** Logos Storage → Postgres-equivalent → Supabase-equivalent  
**TLDR:** Build a structured data + query + API layer on top of Logos Storage — a decentralized Supabase.

### Core feature set requested
- Typed schemas / collections
- CRUD + indexes + query language
- REST and/or GraphQL API generation
- Auth (wallet, email/password, OAuth)
- Realtime subscriptions
- Admin dashboard + SDKs + migrations
- Local dev emulator

### Prior art mentioned in issue
- **Supabase / Firebase** — centralized baseline; defines developer expectations
- **Polybase DB** — decentralized Firebase-like; limited adoption; uses zk-proofs for integrity
- **Ceramic + ComposeDB** — append-only streams + GraphQL DB layer; composable but complex

### Research tasks for Topic 4
1. **Assess prior art depth**: Ceramic/ComposeDB maturity, Polybase status, Kwil DB
2. **Map Logos Storage capabilities**: what primitives exist, what's missing for a DB layer
3. **Identify the indexing gap**: how would a query layer index Logos storage objects?
4. **Cross-reference Topics 1–3**: lessons from The Graph / Substreams / Helius / Filecoin
5. **Feasibility verdict**: what's buildable now, what needs protocol work, what's speculative

### Sources to crawl for Topic 4

| Source | URL | Type |
|--------|-----|------|
| Logos Ideas #19 | https://github.com/logos-co/ideas/issues/19 | Issue |
| Logos Storage docs | https://logos.co (find storage docs) | Docs |
| Ceramic Network | https://ceramic.network/ | Product |
| ComposeDB docs | https://composedb.js.org/ | Docs |
| Polybase DB | https://polybase.xyz/ | Product |
| Kwil DB | https://kwil.com/ | Product |
| OrbitDB | https://github.com/orbitdb/orbitdb | GitHub |
| Tableland | https://tableland.xyz/ | Product |
| SpaceAndTime | https://www.spaceandtime.io/ | Product |

### Open questions
- Does Logos Storage expose enough primitives (consistency guarantees, addressing) for a DB layer?
- Is the indexing problem solvable without a centralized query node?
- What's the minimal viable implementation vs. full Supabase parity?
- Would this be a new project, an integration with existing tools (Ceramic, Tableland), or a fork?

---

## Cron Schedule

All jobs are one-shot (`--delete-after-run`), staggered by 6h:

| Job | Topic | Fire time |
|-----|-------|-----------|
| `research-graph-evm` | The Graph & EVM Indexing | T+0h (immediate) |
| `research-solana-indexing` | Solana Indexing Ecosystem | T+6h |
| `research-storage` | Decentralized Storage | T+12h |
| `research-logos-19` | Logos Ideas #19 Feasibility | T+18h |

Each job: read this file → crawl sources for its topic → write atomic notes → update index.md → commit/push → notify Franck.

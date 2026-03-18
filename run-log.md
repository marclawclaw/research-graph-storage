# Run Log

---

## [2026-03-18 18:27 AEDT] TOPIC 2: Solana Indexing Ecosystem — ok

- Phase: 2 (Deep Crawl)
- Notes written: 7 atomic notes
- Sources crawled:
  - helius.dev/blog/solana-data-tools (full data tools guide)
  - helius.dev/docs/getting-data (DAS API, Enhanced Transactions, LaserStream)
  - helius.dev/blog/solana-geyser-plugins-streaming-data-at-the-speed-of-light
  - helius.dev/blog/all-you-need-to-know-about-solanas-new-das-api
  - helius.dev/blog/introducing-next-generation-enhanced-websockets
  - github.com/rpcpool/yellowstone-grpc (Triton's gRPC server)
  - docs.triton.one/project-yellowstone/introduction
  - thegraph.com/blog/indexing-solana-substreams/
  - solanacompass.com/projects/the-graph
  - solana.com/developers/evm-to-svm/accounts
  - blog.sqd.dev/how-gmx-accelerated-cross-chain-indexing-with-sqd/
  - goldsky.com/chains/solana
  - Web searches: DAS API standard, Geyser plugin, cross-chain indexing patterns, Triton One
- Folder: indexing/solana/
- Key findings:
  - No EVM-style events on Solana — indexers must watch account diffs via Geyser
  - Yellowstone gRPC (Triton) is de-facto streaming standard; open source proto
  - DAS API (Helius/Metaplex) is the established multi-provider NFT/token query spec
  - Helius is the dominant full-stack Solana platform; LaserStream = shred-level latency
  - The Graph uses Substreams (Rust/WASM, parallel) for Solana — not standard subgraphs
  - SQD and Goldsky lead multi-chain unified indexing; GMX case study shows real adoption

## [2026-03-18 12:27 AEDT] TOPIC 1: The Graph & EVM Indexing — ok

- Phase: 2 (Deep Crawl)
- Notes written: 9 (7 concept/analysis + 3 competitor)
- Sources crawled:
  - thegraph.com/docs (architecture, subgraphs, substreams, indexing/GRT)
  - thegraph.com/blog/the-graph-2024-recap/
  - thegraph.com/blog/sunsetting-hosted-service/ (+ transition blog)
  - thegraph.com/blog/indexing-solana-substreams/
  - en.wikipedia.org/wiki/The_Graph
  - docs.sqd.ai/sdk/subsquid-vs-thegraph/
  - docs.envio.dev (HyperSync + HyperIndex overviews)
  - goldrush.dev + github.com/covalenthq
  - spaceandtime.io
  - Web searches: GRT tokenomics, SQD 2025, Sunrise migration, GoldRush
- Folder: indexing/the-graph/
- Key findings: TypeScript tooling (SQD, Envio) is taking mindshare post-Sunrise. Envio claims 2000x speed vs RPC. Space and Time's ZK SQL is architecturally interesting for Logos. Decentralised network adoption still unclear vs Studio free tier.

## [2026-03-18 12:24 AEDT] DISCOVERY — ok

- Phase: 1 (Discovery)
- Topics identified: 4
- Sources catalogued: 30+
- Cron jobs scheduled: 4 (T+0h, T+6h, T+12h, T+18h)
- Notes written: 0 (Phase 2 pending)
- Notes: Added Logos Ideas #19 feasibility assessment as Topic 4 per Franck's instruction

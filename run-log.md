# Run Log

---

## [2026-03-19 00:27 AEDT] TOPIC 3: Decentralized Storage — ok

- Phase: 2 (Deep Crawl)
- Notes written: 7 atomic notes
- Sources crawled:
  - docs.ipfs.tech/concepts/comparisons/ (official IPFS comparison table)
  - dev.to IPFS vs Arweave vs Filecoin comparison article
  - thetechtrends.tech 9 decentralized storage solutions overview
  - nftbirdies.com Arweave/Filecoin/Sia NFT storage deep-dive
  - solanacompass.com Shadow Drive V2 explainer (Solfate podcast)
  - irys.xyz homepage + Medium Bundlr 101 explainer
  - messari.io State of Filecoin Q3 2024 / Q3 2025 (via search snippets)
  - depinscan.io Filecoin Q1/Q2 2025 reports
  - ainvest.com Filecoin enterprise adoption stats
  - academy.swissborg.com Arweave deep-dive
  - blog.upay.best Arweave/SPoRA explainer
  - rootdata.com Irys project timeline and funding
  - coinmarketcap.com Irys/IRYS token + DePIN stats
  - socialcapitalmarkets.net DePIN statistics 2025
  - bingx.com top decentralised storage projects 2026
  - Web searches: DePIN market growth, Filecoin enterprise, Arweave Solana, Irys funding, Storj features, Shadow Drive 2024 status
- Folder: storage/
- Key findings:
  - IPFS is the universal transport layer but needs incentive — Filecoin or pinning services mandatory for persistence
  - Arweave dominates NFT metadata and Solana validator archiving; one-time fee model is DX winner but static-only
  - Filecoin pivoting hard to enterprise (2,491 datasets, $99M inflows 2025); FVM adds programmability
  - Irys (ex-Bundlr) evolution is most interesting: cross-chain payments + programmable data chain; $23.5M raised; testnet live Aug 2025
  - Storj is most dev-friendly: S3-compatible, erasure coding, privacy-first; Valdi acquisition targets AI storage
  - Shadow Drive V2 long-delayed, community concern; use with caution
  - DePIN storage $5.2B → $19B+ in ~18 months; AI data demand is new growth vector
  - Pattern for Logos: S3-compatible API + client-side encryption + cross-chain payments + flexible durations = winning stack

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

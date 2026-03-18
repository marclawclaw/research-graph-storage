---
topic: Decentralised Network vs Hosted Service
type: concept
tags: [the-graph, decentralization, subgraph-studio, hosted-service, sunrise, migration]
confidence: high
last_updated: 2026-03-18
sources:
  - https://thegraph.com/blog/sunsetting-hosted-service/
  - https://thegraph.com/blog/transitioning-to-decentralized-graph-network/
  - https://thegraph.com/blog/the-graph-2024-recap/
---

## Summary
The Graph completed its transition from a centrally-run hosted service to a fully decentralised network in 2024. The "Sunrise" migration sunset the hosted service on June 12, 2024, forcing all subgraphs onto The Graph Network. Subgraph Studio now acts as the developer staging environment; production queries flow through decentralised Indexers.

## Key Facts

### Timeline of Decentralisation ("Sunrise" phases)
| Phase | Action |
|-------|--------|
| **Phase 1 (Sunray)** | Disabled new hosted service subgraph creation for chains with sufficient network coverage |
| **Phase 2 (Sunbeam)** | Disabled hosted service subgraph upgrades |
| **Phase 3 (Sunrise)** | Disabled hosted service querying — all endpoints expired June 12, 2024 |

- **Hosted Service sunset: June 12, 2024** — no longer active
- 10,000+ subgraphs migrated to The Graph Network
- Major protocols now live on network: AAVE, Balancer, ENS, SushiSwap, Uniswap

### Subgraph Studio (post-Sunrise)
- Staging/testing environment for developers; not the production query endpoint
- Deployment backed by **Upgrade Indexer** — single centralised indexer operated by Edge & Node
- Free to use; rate-limited; not visible to public
- Free tier: **100,000 queries/month**
- Does NOT require GRT — intended for development/testing only

### The Graph Network (production)
- Queries served by decentralised Indexers staking GRT
- Consumers pay query fees in GRT
- Curation signal (GRT staked by Curators) determines which subgraphs Indexers prioritise
- No rate limits; publicly queryable
- Subgraphs require on-chain publication transaction + GRT signal to attract Indexers

### Developer Journey
1. Build + test in Subgraph Studio (free, centralised)
2. Publish on-chain (pays gas on Arbitrum One; Upgrade Indexer handles initial serving)
3. Add GRT curation signal to attract additional Indexers
4. Consumers query via The Graph Network gateway (pays GRT per query)

> [!analysis] The "decentralised" network still has meaningful centralisation points: the Upgrade Indexer, the Studio interface, and the gateway layer (operated by Edge & Node). True decentralisation of query serving is aspirational; in practice most small subgraphs rely on the Upgrade Indexer.

## How it relates to Logos
The Sunrise migration illustrates the practical difficulty of transitioning from centralised to decentralised infrastructure. Logos would face similar challenges if building an indexing layer on top of Logos Storage. Key lesson: provide a centralised "studio" tier first for developer adoption, then progressively decentralise. Don't force decentralisation before developer demand exists.

## Open Questions
- What % of queries on The Graph Network are served by the Upgrade Indexer vs. other Indexers?
- Has the Sunrise migration caused meaningful developer churn to competitors like [[SQD]] or [[Envio HyperIndex]]?
- Is there developer frustration with having to pay GRT for production queries after the free hosted service era?

## Sources
- https://thegraph.com/blog/sunsetting-hosted-service/
- https://thegraph.com/blog/transitioning-to-decentralized-graph-network/
- https://thegraph.com/blog/the-graph-2024-recap/
- https://thegraph.academy/developers/upgrading-your-subgraph/

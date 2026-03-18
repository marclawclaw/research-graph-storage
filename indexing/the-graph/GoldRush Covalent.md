---
topic: GoldRush (Covalent)
type: competitor
tags: [indexing, competitor, covalent, goldrush, multichain, api, rest]
confidence: high
last_updated: 2026-03-18
sources:
  - https://goldrush.dev/
  - https://github.com/covalenthq
---

## Summary
GoldRush (formerly Covalent) is a managed, multi-chain blockchain data API platform supporting 100+ blockchains. Unlike The Graph (subgraph authorship required), GoldRush offers pre-built, REST-first APIs for common data types (token balances, transfers, NFT data, gas prices, contract events) — no indexing setup needed. It is developer-friendly for quick integration but less customisable than subgraph-based approaches.

## Key Facts
- Product: **GoldRush** — branded product; SDK: `@covalenthq/client-sdk`
- Supports **100+ blockchains** including Ethereum, Polygon, BNB Chain, Base, Optimism, and more
- API style: **REST-first** (vs. GraphQL for The Graph/SQD); structured JSON responses
- Key endpoints: token balances, ERC-20/native transfers, contract event logs, NFT data, gas prices, block data
- No subgraph authorship — pre-indexed data for all supported chains out of the box
- Available on QuickNode marketplace as add-on
- GitHub org: `covalenthq` — open-source SDKs and toolkits

### Sample usage (TypeScript)
```typescript
import { GoldRushClient } from "@covalenthq/client-sdk";
const client = new GoldRushClient("YOUR_API_KEY");
const balances = await client.BalanceService
  .getTokenBalancesForWalletAddress("eth-mainnet", "0x...");
```

### Position in ecosystem
- **Fastest time-to-first-query** — no indexing setup, just API key + call
- **Pre-built data** for common use cases (wallets, explorers, portfolio trackers)
- Limited to what Covalent has pre-indexed — custom events require support
- Not decentralised — centrally operated infrastructure

> [!analysis] GoldRush is ideal for applications consuming standard blockchain data (balances, transfers, NFT metadata) across many chains without custom indexing logic. For custom contract event indexing, it falls short compared to The Graph or SQD. It competes most directly with Alchemy/QuickNode managed APIs.

## How it relates to Logos
If Logos builds a query API layer on top of Logos Storage, GoldRush's REST-first, no-setup approach represents the minimum viable DX target for a managed tier. The lesson: offer a set of pre-built, opinionated endpoints for common data patterns before requiring users to write custom indexing logic. See [[Logos Ideas 19]].

## Open Questions
- Does GoldRush have a decentralisation roadmap (Covalent had a CQT token)?
- How does pricing scale for high-volume production applications?
- Is GoldRush actively maintained post-rebrand, or is it in maintenance mode?
- What's the data freshness (latency) for GoldRush's pre-indexed chains?

## Sources
- https://goldrush.dev/
- https://github.com/covalenthq
- https://marketplace.quicknode.com/add-on/covalent-blockchain-api

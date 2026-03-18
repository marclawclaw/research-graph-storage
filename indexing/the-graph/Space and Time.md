---
topic: Space and Time
type: competitor
tags: [indexing, competitor, sql, zk-proofs, space-and-time, onchain-finance, verifiable]
confidence: high
last_updated: 2026-03-18
sources:
  - https://www.spaceandtime.io/
---

## Summary
Space and Time is a decentralised data platform that combines blockchain indexing, off-chain data storage, and a ZK coprocessor for SQL queries. Developers write SQL to query indexed on-chain data, secure off-chain data with ZK proofs, and use those proofs in smart contracts. Primary focus is on DeFi, stablecoins, tokenized assets, and institutional finance — not general-purpose dApp development.

## Key Facts
- Self-described: "the data blockchain" — decentralised replacement for database + indexing + API servers
- **Core differentiator**: ZK-proven SQL queries — SQL results come with zero-knowledge proofs that can be verified on-chain
- Query language: **SQL** (vs. GraphQL for The Graph)
- Use cases: onchain finance, DeFi protocols, stablecoins, tokenized assets, reserves proofs, NAV proofs, compliance, audits
- Supports: Ethereum, Base, and other popular EVM chains
- Self-service indexing of smart contract events (custom tables for contract events)
- **Verifiable offchain data**: ingest external data → secure with ZK proofs → join with on-chain data → prove to smart contracts
- Smart contracts can execute ZK-proven SQL to access historical chain data and offchain inputs
- Applications: data-driven smart contracts for minting/redemption, settlements, collateral checks, fee distribution, compliance
- Security: audited (auditor not named in source)

### Product surfaces
1. **Indexed blockchain data** — query EVM history via SQL
2. **Verifiable onchain database** — secure offchain data with ZK proofs
3. **Smart contract data access** — prove SQL queries on-chain; execute financial logic
4. **Data APIs** — deliver query results to apps/dashboards/backends without custom pipelines

### How ZK SQL works
- Run SQL query against indexed data
- Generate ZK proof of query correctness
- Proof submitted on-chain → smart contract verifies → executes based on result
- Enables data-driven contract execution without trusting an oracle

> [!analysis] Space and Time occupies a unique niche: verifiable data for financial applications. The ZK SQL approach is technically impressive but complex. It's not competing for general web3 developer mindshare — it targets institutional/DeFi protocols that need auditable, provable data pipelines. Not a direct threat to The Graph for typical dApp development.

## How it relates to Logos
Logos's privacy and ZK focus makes Space and Time worth watching. The idea of ZK-proven query results feeding into smart contract logic is directly applicable to trustless data layers on top of Logos Storage. For [[Logos Ideas 19]], a ZK query verification layer could differentiate a Logos-native indexer from all existing solutions. This is speculative/future-looking but architecturally aligned with Logos's ZK research.

## Open Questions
- Is Space and Time's ZK SQL commercially deployed and production-proven, or still research-stage?
- What chains beyond EVM does it support?
- How does query latency for ZK-proven SQL compare to standard GraphQL or REST APIs?
- Is there a token (SXT)? If so, what are the tokenomics?
- Does it support custom smart contract indexing, or only pre-indexed chains?

## Sources
- https://www.spaceandtime.io/

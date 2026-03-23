---
topic: Logos Ideas #19 — Supabase on Logos Storage
type: competitor
tags: [decentralized-database, zk-proofs, prior-art, dead-project]
confidence: high
last_updated: 2026-03-19
sources:
  - https://polybase.xyz/
  - https://polybaselabs.com/
---

## Summary
Polybase was a Firebase-like decentralised database using ZK-proofs for integrity guarantees. It is now effectively a dead project — the team (Polybase Labs) has pivoted to building "Payy", an onchain consumer bank for stablecoins. The Polybase database is listed as a "past project" on their website.

## Key Facts
- **Original pitch**: Firebase-style collections and queries with ZK-proof-backed integrity. Target: replace Firebase with a verifiable decentralised alternative.
- **Current status**: **DEAD / PIVOTED**. polybase.xyz now redirects to polybaselabs.com which focuses on "Payy" — an on-chain consumer bank.
- **Past projects listed**: Polybase DB ("ZK-rollup with private transactions"), Polylang ("ZK STARK compiler with TypeScript-like syntax"), zkbench.dev.
- **Why it failed** (inferred): ZK proof complexity + bootstrapping a new network + developer adoption challenge proved too hard simultaneously. The team appears to have found an easier market (payments).
- **Adoption**: Never achieved mainstream adoption. No published user metrics.
- **Technical approach**: ZK-rollup-based storage with a client-facing API resembling Firebase. Ambitious but not completed.

> [!fact] Confirmed from official website (polybaselabs.com, 2026-03-19)
> Polybase DB is listed under "Past projects" on Polybase Labs homepage. The flagship product is now Payy, an onchain consumer bank.

> [!analysis] Analyst inference — not verified
> The failure pattern: ZK overhead at the database layer is premature optimisation when you can't even get developers to switch from Firebase. Ceramic took a simpler approach (append-only streams + Ethereum anchoring) and got further. For Logos Ideas #19, ZK integrity proofs should be a later-stage feature, not a Day 1 requirement.

## How it relates to Logos
- **Key lesson**: Developer-facing database products are very hard to bootstrap. Even a funded team with a novel ZK approach couldn't achieve adoption.
- **Avoid**: Building ZK proof verification into the core MVP. That's a complexity multiplier.
- **Signal**: The Supabase-equivalent space remains wide open for a well-funded, technically credible team. Polybase's exit creates opportunity.

## Open Questions
- Does any Polybase codebase remain open source for reference architecture?
- Was the ZK approach technically flawed or just poorly timed (pre-ZK boom)?

## Sources
- https://polybase.xyz/docs (docs still partially accessible)
- https://polybaselabs.com/

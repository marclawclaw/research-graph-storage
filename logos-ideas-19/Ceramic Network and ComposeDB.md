---
topic: Logos Ideas #19 — Supabase on Logos Storage
type: competitor
tags: [decentralized-database, graphql, ceramic, composedb, prior-art]
confidence: high
last_updated: 2026-03-19
sources:
  - https://ceramic.network/
  - https://developers.ceramic.network/learn/welcome/
  - https://blog.ceramic.network/faq-ceramic-network/
---

## Summary
Ceramic is a decentralised event-streaming protocol that anchors data to Ethereum for global ordering. ComposeDB is the primary database built on Ceramic, offering a GraphQL interface over schemas defined by developers. It is the closest existing analogue to Logos Ideas #19 — a decentralised structured-data layer — but requires running indexing nodes and has no tokenised incentive for doing so.

## Key Facts
- **Architecture**: Append-only stream of signed events. Each event is a JSON patch. Streams are identified by a StreamID (DID-anchored).
- **Global ordering**: Events rolled up and anchored to Ethereum blockchain for immutable timestamps. This is the consistency mechanism — not a native consensus.
- **ComposeDB**: GraphQL database on top of Ceramic. Developers define schema (SDL), deploy a "composite", and get a GraphQL API. Internally uses SQLite for the local index.
- **Scale claims**: 400+ apps, 10M+ streams of content (as of ceramic.network homepage).
- **Decentralisation caveat**: No tokenised incentives for running Ceramic nodes. Nodes can defect; data availability depends on someone caring.
- **Developer complexity**: Requires: running a Ceramic node, deploying composites to it, understanding the stream model, managing anchoring latency (Ethereum anchoring is async).
- **Indexing**: Each node maintains a local SQLite index of streams it watches. Query capability is scoped to what that node indexes — not a global index.
- **Mutability model**: Streams are mutable via append. The latest state is the aggregate of all patches applied in order.
- **Launch timeline**: Developer Preview September 2022. Still in developer preview / beta posture as of 2025.
- **Ethereum dependency**: Global ordering depends on Ethereum anchoring. This is a centralisation vector — also introduces latency (anchoring can take minutes to hours).

> [!fact] Confirmed from official docs
> "Today there are no tokenized incentives for running a Ceramic node, but by running a node you can ensure the data for your app remains available while helping contribute to the network's decentralization." — developers.ceramic.network

> [!analysis] Analyst inference — not verified
> The lack of economic incentives for node operation is the #1 risk for data durability. Apps that stop running their own node lose availability. This is structurally similar to self-hosted Postgres — not decentralised in practice for most apps.

> [!analysis] Analyst inference — not verified
> ComposeDB's local SQLite indexing per node means queries only cover data that node has subscribed to. Global query across all Ceramic data is not possible by design. This is a fundamental architectural limitation vs. Supabase's centralised query engine.

## How it relates to Logos
Ceramic/ComposeDB is the **closest direct prior art** for Logos Ideas #19. Key lessons:
1. **Append-only streams on blob storage work** — proves the model is feasible.
2. **Per-node SQLite indexing is the practical pattern** — not globally distributed indexing.
3. **Lack of incentives = lack of durability** — Logos Storage's incentivised marketplace is an improvement over Ceramic's volunteer model.
4. **Ethereum dependency is a trap** — Logos should anchor ordering in its own blockchain module, not Ethereum.
5. **GraphQL is the right API surface** — ComposeDB proves developers accept GraphQL for structured decentralised data.

## Open Questions
- Is Ceramic's adoption (400 apps, 10M streams) genuine or concentrated in a few projects?
- Has ComposeDB released a production-stable version or is it still beta?
- Could ComposeDB's indexing layer be adapted to store its data on Logos Storage instead of local SQLite?

## Sources
- https://ceramic.network/
- https://developers.ceramic.network/learn/welcome/
- https://blog.ceramic.network/faq-ceramic-network/

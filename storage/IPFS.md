---
topic: Decentralized Storage
type: concept
tags: [storage, ipfs, content-addressing, p2p, pinning]
confidence: high
last_updated: 2026-03-19
sources:
  - https://docs.ipfs.tech/concepts/comparisons/
  - https://thetechtrends.tech/decentralized-storage-solutions/
---

## Summary
IPFS (InterPlanetary File System) is a peer-to-peer content-addressed file system where data is identified by a CID (Content Identifier) — a cryptographic hash of the content itself, not its location. It has no built-in incentive or persistence layer; data survives only as long as at least one node pins it.

## Key Facts

- **Content addressing**: Data is retrieved by what it is (CID), not where it is (URL). Identical content always has the same CID; any bit change produces a new CID.
- **No native persistence**: Unpinned data is subject to garbage collection and can vanish. Persistence requires explicit pinning — locally or via a third-party pinning service (Pinata, web3.storage, Infura, nft.storage).
- **Distributed hash table (DHT)**: Nodes advertise which CIDs they hold; routing finds the nearest holder of a CID.
- **Merkle DAG data model**: Files chunked into blocks, linked into a DAG (similar to git). Deduplication is automatic — shared blocks count once.
- **Libp2p networking**: Uses the same networking stack as [[Filecoin]] and [[Ethereum Swarm]].
- **IPNS**: Mutable pointer system that lets a key resolve to different CIDs over time — adds mutability layer on top of the immutable CID namespace.
- **Pinning services API**: W3C-standardised API for delegating pin requests to remote services.
- **Use in NFTs**: NFT metadata on OpenSea, Rarible, and many Solana collections points to IPFS CIDs. Metaplex standards support IPFS URIs natively.
- **Gateway access**: Public gateways (gateway.ipfs.io, cloudflare-ipfs.com) let browsers fetch IPFS content over HTTP without running a node.

> [!fact] Confirmed from official docs
> CIDs are self-describing — they encode the hashing algorithm, codec, and hash. This makes them forward-compatible as hash algorithms evolve.

> [!analysis] Analyst inference — not verified
> IPFS is best understood as a content-addressed transport layer, not a storage guarantee. Real persistence requires the incentive layer provided by [[Filecoin]] or a pinning service.

## How it relates to Logos

- Logos Storage is exploring content-addressed primitives; IPFS's CID scheme and IPLD data model are a direct precedent for how Logos could address stored objects.
- IPFS shows the failure mode of decentralised storage without incentives — data rot without pinning. Logos needs to design persistence guarantees from day one.
- A Logos-based app that wants to interop with the broader Web3 ecosystem (e.g., NFT metadata) may need to produce IPFS-compatible CIDs or gateways.
- [[Filecoin]] wraps IPFS and adds the economic layer — a pattern Logos could replicate with its own token economics.

## Open Questions

- Can Logos Storage be made IPFS-compatible (CID namespace) for cross-ecosystem access?
- Is IPNS-style mutability (key → CID) something Logos Storage will support natively?
- How do pinning service economics compare to Logos's storage incentive model?

## Sources

- https://docs.ipfs.tech/concepts/comparisons/
- https://thetechtrends.tech/decentralized-storage-solutions/
- https://dev.to/raji_moshood_ee3a4c2638f6/decentralized-storage-wars-ipfs-vs-arweave-vs-filecoin-52c3

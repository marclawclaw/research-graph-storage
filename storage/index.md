# Storage — Index

**Topic**: Decentralized Storage  
**Phase**: 2 complete — deep crawl done  
**Last updated**: 2026-03-19  
**Notes**: 7 atomic notes

---

## Notes

| File | Type | Summary |
|------|------|---------|
| [IPFS.md](IPFS.md) | concept | Content-addressed P2P file system. No built-in incentive or persistence — requires pinning. Foundation for Filecoin and much of the Web3 storage stack. |
| [Filecoin.md](Filecoin.md) | concept | Incentive layer on top of IPFS. Time-bound storage deals with cryptographic proofs. 2,491 enterprise datasets onboarded (Q3 2025); FVM enables programmable storage. |
| [Arweave.md](Arweave.md) | concept | Permanent storage via one-time endowment fee. Blockweave + Proof of Access consensus. De-facto standard for NFT metadata and Solana validator ledger archiving. |
| [Shadow Drive.md](Shadow%20Drive.md) | competitor | Solana-native object storage by GenesysGo. "Solana's hard drive" — targets mutable hot-access storage with custom consensus. V2 development long-running; status uncertain. |
| [Storj.md](Storj.md) | competitor | S3-compatible decentralised storage with erasure coding and client-side encryption. Most developer-friendly option. Acquired Valdi (GPU compute) in 2024. |
| [Irys Bundlr.md](Irys%20Bundlr.md) | concept | Evolved from Arweave upload service (Bundlr) to standalone programmable data chain (Irys). Cross-chain payments, flexible storage durations, smart contracts that access stored data. $23.5M raised. |
| [DePIN Storage Sector.md](DePIN%20Storage%20Sector.md) | analysis | Sector overview and growth trends. DePIN storage grew $5.2B → $19B+ (2024 → Sep 2025). AI data demand + Web3 adoption driving. FIL, AR, STORJ all surged Nov 2025. |

---

## Key Themes

1. **No-incentive layer problem**: IPFS alone doesn't guarantee persistence — all production apps need an incentive layer (Filecoin) or pinning service (Pinata, web3.storage).
2. **Permanence vs. time-bound**: Arweave (pay once, permanent) vs. Filecoin (renewed deals) vs. Storj/Shadow Drive (subscription-like). Different use cases.
3. **Developer UX gap**: Filecoin's deal complexity and token volatility create friction. Storj's S3 compatibility and Irys's cross-chain payments show the winning UX pattern.
4. **Solana patterns**: Arweave + Irys/Bundlr for NFT metadata and ledger archiving. Shadow Drive as Solana-native alternative. NFT metadata points to IPFS or Arweave CIDs.
5. **DePIN growth**: 270% market cap growth in ~18 months. Enterprise adoption real (Filecoin 2,491 datasets). AI data demand creating new demand vectors.
6. **Convergence**: Compute + storage (Storj+Valdi, Render, Irys programmable chain). The future is not just storage — it's storage + execution.

---

## Cross-references

- [[The Graph]] — query layer on top of data; relevant for indexing Logos Storage
- [[Logos Ideas 19]] — decentralised Supabase built on Logos Storage
- [[Solana Indexing Ecosystem]] — how Solana apps index Arweave/IPFS stored data

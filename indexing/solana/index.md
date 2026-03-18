# Solana Indexing Ecosystem — Index

**Topic**: Solana Indexing Ecosystem  
**Phase 2 completed**: 2026-03-18  
**Notes**: 7 atomic notes

---

## Notes

| File | Type | Summary |
|------|------|---------|
| [[Solana Account Model vs EVM Events]] | concept | Why EVM event-log indexing doesn't apply to Solana; account-based state model and its indexing implications |
| [[Geyser Plugin Interface]] | concept | The Solana validator's low-level streaming hook (Rust trait) that powers all real-time indexing |
| [[Yellowstone gRPC (Triton)]] | concept | Triton One's production gRPC server built on Geyser; Project Yellowstone suite including Dragon's Mouth and Old Faithful |
| [[DAS API Standard]] | concept | Helius/Metaplex open-source spec for unified NFT/token querying on Solana; multi-provider standard |
| [[Helius Platform]] | competitor | Full-stack Solana dev platform: RPC + DAS + webhooks + LaserStream gRPC streaming |
| [[The Graph Substreams on Solana]] | concept | The Graph's Rust/WASM parallel indexing approach for Solana via Firehose + Substreams |
| [[Cross-Chain Indexing Patterns]] | analysis | Patterns and tools for unified multi-chain indexing (SQD, Goldsky, Firehose); GMX case study |

---

## Key Takeaways

1. **No native events**: Solana has no equivalent to EVM event logs. Indexers must watch account state diffs, not event emissions.
2. **Geyser is the foundation**: All high-performance Solana indexing flows through the Geyser plugin interface. Requires running your own validator or using a provider.
3. **Yellowstone = industry standard gRPC**: The open-source `rpcpool/yellowstone-grpc` proto is the de-facto streaming wire format for Solana.
4. **DAS = NFT/token query standard**: The DAS API (Helius/Metaplex) is the established interface for digital asset data. Multi-provider, JSON-RPC, handles cNFTs.
5. **Helius dominates developer mindshare**: Full-stack platform combining all of the above. LaserStream achieves shred-level ultra-low latency.
6. **The Graph on Solana = Substreams**: The Graph took a different approach for Solana (Rust/WASM parallel processing) vs EVM (AssemblyScript event handlers).
7. **Cross-chain trend**: SQD and Goldsky are the leaders for unified multi-chain indexing; TypeScript-based, batch processing, ~100k+ blocks/sec.

---

## Relation to Logos Ideas #19

For a Supabase-on-Logos layer, the Solana indexing ecosystem suggests:
- Build separate **extraction** (protocol hooks) and **transformation** (user-defined logic) layers
- Design a **standardized query API** (DAS-style) for Logos storage objects
- Plan for **historical replay** from the start — not an afterthought
- Consider whether to build chain-specific or adopt a unified indexer SDK

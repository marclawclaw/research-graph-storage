---
topic: Yellowstone gRPC (Triton)
type: concept
tags: [solana, triton, yellowstone, grpc, streaming, rpc-provider]
confidence: high
last_updated: 2026-03-18
sources:
  - https://github.com/rpcpool/yellowstone-grpc
  - https://docs.triton.one/project-yellowstone/introduction
  - https://docs.triton.one/project-yellowstone/dragons-mouth-grpc-subscriptions
  - https://solanacompass.com/projects/triton-one
---

## Summary
Yellowstone gRPC (maintained by Triton One as part of Project Yellowstone) is an open-source, production-grade gRPC server built on top of the Solana Geyser plugin interface. It is branded "Dragon's Mouth" and provides a standardized, filterable streaming API for slots, blocks, transactions, and account updates — the de-facto industry standard for high-performance Solana data streaming.

## Key Facts
- **Repo**: `github.com/rpcpool/yellowstone-grpc` (open source, maintained by Triton One).
- **Branding**: Project Yellowstone (suite) → Dragon's Mouth (gRPC) + Steamboat (custom indexes) + Whirligig (WebSockets) + Old Faithful (historical archive).
- **Protocol**: gRPC using protobuf schema defined in `yellowstone-grpc-proto/proto/geyser.proto`.
- **Subscription types**: slots, blocks, transactions, accounts, block_meta, entries.
- **Filtering capabilities**:
  - Accounts: by `account` (pubkey), `owner` (program pubkey), `filters` (dataSize / Memcmp)
  - Transactions: by `signature`, `account_include`, `account_exclude`, `account_required`
  - Slots: by `commitment` level
- **Ping/keepalive**: Server sends pings every 15s; clients should reply to keep connections alive through cloud load balancers (Cloudflare, Fly.io).
- **Kafka bridge**: `yellowstone-grpc-kafka` project forwards gRPC stream to Kafka with deduplication.
- **Client libraries**: Go, Rust, TypeScript example clients included in repo.
- **Performance**: Dragon's Mouth improves streaming capability by ~75% vs standard implementations (per Solana Compass).
- **Old Faithful**: Built with Solana Foundation — decentralized historical archive of all Solana transaction and block data, low cost.
- **Block reconstruction limitation**: Block entries count is always zero on validators (known Solana issue #33823).

> [!fact] Confirmed from GitHub repo and Triton docs
> Yellowstone is the most widely deployed production Geyser gRPC implementation. Used by Helius (LaserStream), QuickNode, and many independent operators.

> [!analysis] Industry standard status
> While not an official Solana Labs standard, Yellowstone gRPC proto has become the de-facto wire format for high-performance Solana streaming. Helius's LaserStream is built on the same infrastructure.

## How it relates to Logos
- Yellowstone demonstrates how a community-developed standard (not official protocol) can become the dominant interface for a chain's data layer — relevant to Logos where community standards may emerge around indexing.
- Old Faithful (decentralized historical archive) is a direct parallel to what Logos might need: a decentralized way to store and serve historical chain data without centralizing it at an RPC provider.
- See also: [[Geyser Plugin Interface]], [[Helius Platform]]

## Open Questions
- Is the Yellowstone proto format being formalized into the Solana protocol spec?
- How does Old Faithful's decentralized model actually work — what storage layer does it use?
- Will Agave (new Solana validator) maintain full Yellowstone compatibility?

## Sources
- https://github.com/rpcpool/yellowstone-grpc
- https://docs.triton.one/project-yellowstone/introduction
- https://docs.triton.one/project-yellowstone/dragons-mouth-grpc-subscriptions
- https://solanacompass.com/projects/triton-one

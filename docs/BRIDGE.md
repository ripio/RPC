# RPC bridge: Ethereum ↔ HyperEVM (LayerZero)

## Decision (2026-10-21)

RPC bridges between Ethereum and HyperEVM through LayerZero v2: an OFT Adapter on Ethereum (wrapping the existing RipioCoin ERC-20) and an OFT on HyperEVM.

**Security stack (DVNs): 2-of-3, none individually required**

| DVN | Notes |
|-----|-------|
| LayerZero Labs | |
| Nethermind | |
| Canary | TEE-based verification |

- All three have DVN contracts deployed on both Ethereum and HyperEVM ([addresses](https://docs.layerzero.network/v2/deployments/dvn-addresses)).
- Why 2-of-3: operator independence, and the bridge tolerates one DVN going down. Minimum 2 verifiers so no single DVN can approve a message. This is the failure mode behind the KelpDAO bridge exploit (Apr 2026).
- Proposed by Nicolás Menendez, approved by Sebastián Serrano (Slack group DM with Antonio Ceraso, 2026-10-21).

## Phase 2 (not started)

Run our own DVN on Ripio infra (DVN contracts on both chains + the off-chain worker), ideally as a **required** DVN on top of the 2-of-3 optional set, so that no message gets through without Ripio's verification.

---
token: OFC
ticker: OFC
network: base
risk_score: 46
status: medium
date: 2026-09-20
---

# OFC (OFC) — Smart Contract Security Analysis | Base

> **Risk Score: 46/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ofc-base)

---

## Audit Summary

The ERC20FixedSupply token contract implements a standard fixed-supply ERC-20 token with features like batch transfers, permit, meta-transactions, and owner-based token recovery. The contract utilizes a modular architecture with Solidity 0.8.28, benefiting from modern security features. The `TokenRecovery` module is assumed to allow recovery of non-native ERC20 tokens, not its own fixed-supply token, which would otherwise be a critical vulnerability.

> **Final Recommendation:** To enhance the security posture, ensure that the initial `holders` and `allocations` arrays for the `batchMint` function in the constructor are within practical gas limits to prevent deployment failures. Consider implementing a two-step ownership transfer mechanism for the `ContractOwnership` to provide a safer process for changing administrative control. Additionally, verify the specific implementation of the `TokenRecovery` module to confirm it exclusively allows recovery of non-native tokens, preventing any potential backdoor for the owner to seize native tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract exhibits a robust technical architecture (7.1), leveraging modern Solidity features (0.8.28) and a modular design with extensive library usage for ERC-20 functionalities, batch… |
| **Governance / Economics** | 1/10 | High | The token has a fixed supply (7.4), established during construction, which provides predictable tokenomics. Ownership (7.3) is managed via a standard ERC-173 pattern, allowing the deployer to… |
| **Upgrades** | 6/10 | Medium | The `ERC20FixedSupply` contract is implemented as a standard, non-upgradeable contract. There are no proxy patterns or upgrade mechanisms (7.7) integrated, which simplifies its architecture and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Deployment DoS via Large `batchMint` Arrays  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC20FixedSupply` constructor calls `ERC20Storage.layout().batchMint(holders, allocations)`. If the `holders` and `allocations` arrays are excessively large, the gas cost of this operation could exceed the block gas limit, preventing the contract from being deployed. This constitutes a denial-of-service at deployment time (7.2).

**Recommendation:** Prior to deployment, carefully calculate the gas cost of the `batchMint` operation with the intended array sizes. If the arrays are too large, consider reducing the initial number of recipients to ensure the constructor call fits within a single transaction's gas limit. For a fixed-supply token, the entire initial allocation must be processed in the constructor.


### `L-01` — Single-step Ownership Transfer  *(Severity: Low · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `transferOwnership` function in `ContractOwnershipBase` allows the current owner to transfer ownership to a new address in a single transaction (7.3). While functional, this pattern carries a risk: if the `newOwner` address is incorrect (e.g., a typo or an unowned address), the contract's ownership could be permanently lost or transferred to an inaccessible address (7.8).

**Recommendation:** Implement a two-step ownership transfer mechanism. This typically involves a `proposeOwner` function where the current owner nominates a new owner, and an `acceptOwnership` function that the nominated new owner must call to finalize the transfer. This mitigates the risk of accidental ownership loss.


### `I-01` — Reliance on External Forwarder Registry  *(Severity: Informational · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The `ERC20FixedSupply` contract integrates `ForwarderRegistryContext` and relies on an external `IForwarderRegistry` contract for meta-transaction support. The security and availability of this external registry are critical for the proper functioning of meta-transactions within the token (7.6).

**Recommendation:** Ensure that the `IForwarderRegistry` contract used is thoroughly audited, well-maintained, and deployed by a trusted entity. Understand its operational risks and potential points of failure, as any issues with the registry could impact the user experience for meta-transactions.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x752c...c858`](https://basescan.org/address/0x752c5a95d202972e124390f30a50154409d3c858) |
| **Network** | Base |
| **Price** | $0.009783 |
| **24h Volume** | $389.5K |
| **Liquidity** | $203.0K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 94.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9501 buys / 9996 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x44b5d0d8ce8c643c7e217e92492621c4c0ae3121)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ofc-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*

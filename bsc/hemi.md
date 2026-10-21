---
token: Hemi
ticker: HEMI
network: bsc
risk_score: 68
status: high
date: 2026-08-30
---

# Hemi (HEMI) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 68/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/hemi-bsc)

---

## Audit Summary

The audit of the BinanceHemiOFT contract, an extension of LayerZero's OFT, revealed a well-structured codebase with clear logic for its core functionality. The contract introduces a 'manager' role with significant control over token transfer restrictions, allowing for granular control over who can send and receive tokens. While the technical implementation is robust, the high degree of centralization around the manager role presents a significant operational and governance risk. The contract is not upgradeable, simplifying its lifecycle management.

> **Final Recommendation:** To enhance the security posture of the BinanceHemiOFT contract, it is strongly recommended to implement robust access control mechanisms for the 'manager' role, ideally by assigning it to a well-secured multisignature wallet with a high threshold. Consider adding time-locks for critical manager operations to provide a window for review and intervention. Thoroughly document the intended long-term strategy for the `revokeManagement` function, ensuring all stakeholders understand its irreversible implications for transfer controls.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical implementation of the BinanceHemiOFT contract is straightforward and adheres to common Solidity patterns. It correctly inherits from LayerZero's OFT and OpenZeppelin's Ownable… |
| **Governance / Economics** | 1/10 | High | The contract design introduces a 'manager' role with extensive control over token transfers, including the ability to halt all transfers or selectively whitelist/blacklist accounts (7.3 Access… |
| **Upgrades** | 6/10 | Medium | The provided contract is not implemented as an upgradeable proxy (7.7 Upgrades). This simplifies the contract's lifecycle and removes the complexities and potential risks associated with upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Transfers by Manager  *(Severity: High · Status: Unresolved)*

The `manager` role possesses extensive control over token transfer functionality. The manager can enable/disable all transfers via `isTransferEnabled`, and selectively whitelist/blacklist accounts for sending (`canSendToAnyone`, `canSendToWhitelisted`) and receiving (`canReceive`). A compromised manager account could lead to a denial of service for all token holders by halting transfers, or selectively freeze funds by restricting specific accounts. This represents a significant centralization risk (7.3 Access Control, 7.4 Economic).

**Recommendation:** Assign the `manager` role to a robust multisignature wallet with a high transaction threshold to distribute control and reduce the risk of a single point of failure. Implement off-chain governance procedures for manager actions, ensuring transparency and community oversight.


### `M-01` — Irreversible Revocation of Management  *(Severity: Medium · Status: Unresolved)*

The `revokeManagement()` function permanently sets the `manager` address to `address(0)` and, crucially, globally enables transfers by calling `updateTransferEnabled(true)`. While this decentralizes control over transfer restrictions, it means that once revoked, the transfer restriction mechanism can never be re-established or modified. This design choice is irreversible and might limit future flexibility if unforeseen circumstances require re-enabling transfer controls (7.5 Governance, 7.8 Operations).

**Recommendation:** Ensure that the irreversible nature of `revokeManagement` is a deliberate design decision and is clearly communicated to all stakeholders. If future flexibility is desired, consider an alternative mechanism that allows for temporary suspension or a multi-step process for permanent revocation, possibly involving a governance vote.


### `L-01` — Manager Role Not Enforced as Multisig On-Chain  *(Severity: Low · Status: Unresolved)*

The `manager` role, which holds significant power over token transfers, is defined as a single `address`. While the prefill indicates the `owner` (from `Ownable`) is a multisig, there is no on-chain enforcement or mechanism to ensure that the `manager` address itself is a multisig wallet. If the `manager` is an Externally Owned Account (EOA), it represents a single point of failure, increasing the risk of compromise (7.3 Access Control, 7.8 Operations).

**Recommendation:** If the intention is for the `manager` to be a multisig, consider implementing a check in the constructor or `updateManager` function to verify if the new manager address is a known multisig contract, or explicitly document the off-chain policy requiring a multisig for this role.


### `I-01` — Lack of Time-Locks for Critical Manager Operations  *(Severity: Informational · Status: Unresolved)*

Critical operations performed by the `manager`, such as `updateTransferEnabled`, `updateCanSendToAnyone`, `updateCanReceive`, and `updateManager`, are executed immediately upon transaction. The absence of time-locks means that malicious or erroneous actions by a compromised manager could have immediate and irreversible consequences, leaving no window for community review or emergency intervention (7.8 Operations).

**Recommendation:** Consider implementing a time-lock mechanism for critical manager functions. This would introduce a delay between the initiation and execution of sensitive changes, allowing for potential detection of malicious activity or correction of errors before they take full effect.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x5ffd...fc5b`](https://bscscan.com/address/0x5ffd0eadc186af9512542d0d5e5eafc65d5afc5b) |
| **Network** | BNB Chain |
| **Price** | $0.01634 |
| **24h Volume** | $10.16M |
| **Liquidity** | $668.0K |
| **Volume / Liquidity** | 15.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 92.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15976 buys / 16830 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1b54cd932b6b751803c996cbef36280b53795f81)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/hemi-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

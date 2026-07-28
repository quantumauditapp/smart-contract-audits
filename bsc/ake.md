---
token: AKE
ticker: AKE
network: bsc
risk_score: 48
status: high
date: 2026-07-26
---

# AKE (AKE) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 48/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ake-bsc)

---

## Audit Summary

The AKEToken contract implements a standard ERC20 token with custom transfer restrictions managed by a 'transfer controller' role. The contract utilizes OpenZeppelin's Ownable and ERC20 implementations, contributing to a solid foundation. Key risks include significant centralization of control over token transfers and an initial restricted transfer mode. The owner role is managed by a multisig, which is a strong security practice, but the transfer controller could be a single EOA.

> **Final Recommendation:** To enhance the security and decentralization of the AKEToken, it is recommended to carefully manage the `_transferController` role. Consider assigning this critical role to a robust multi-signature wallet or a decentralized autonomous organization (DAO) to mitigate the risk of a single point of failure. Additionally, ensure clear communication to users regarding the initial transfer restrictions and the irreversible nature of setting the transfer mode to 'NORMAL'.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical security practices (7.2 Code Security) by inheriting from battle-tested OpenZeppelin contracts (ERC20, Ownable) and using Solidity 0.8+, which includes… |
| **Governance / Economics** | 3/10 | High | The contract design introduces significant centralization (7.3 Access Control, 7.4 Economic, 7.5 Governance). The `_transferController` role has the power to restrict or halt all token transfers… |
| **Upgrades** | 7/10 | Low | The AKEToken contract is not designed as an upgradeable proxy (7.7 Upgrades). Therefore, there are no upgrade-related risks or considerations for this specific contract. Any changes to its logic… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.6% |
| **Top-3 Unlocked** | ⚠️ 99.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control Over Token Transfers  *(Severity: High · Status: Unresolved)*

The `_transferController` role possesses the ability to set the `_transferMode` to `RESTRICTED` or `CONTROLLED`, effectively halting all token transfers or limiting them to only transfers involving the controller. This grants significant power to a single entity, potentially impacting token liquidity and user asset control. While the `owner` (a multisig) can change the `_transferController`, the controller itself could be an EOA, representing a single point of failure (7.3 Access Control, 7.4 Economic).

**Recommendation:** It is strongly recommended to assign the `_transferController` role to a robust multi-signature wallet with a high threshold or a decentralized autonomous organization (DAO). This would distribute control and reduce the risk associated with a single point of failure or compromise. Clearly communicate the capabilities of this role to all token holders.


### `M-01` — Irreversible Transfer Mode Change to NORMAL  *(Severity: Medium · Status: Unresolved)*

The `setTransferMode` function includes a condition `if (_transferMode != TransferMode.NORMAL)` which prevents the transfer mode from being changed once it has been set to `NORMAL`. This means that after transfers are fully enabled, the `_transferController` cannot re-restrict them. While this provides a degree of security for users, it also removes any future flexibility for the project to re-introduce restrictions if unforeseen circumstances arise (7.1 Architecture, 7.8 Operations).

**Recommendation:** Ensure this design choice is intentional and aligns with the long-term strategy for the token. If future flexibility to re-introduce restrictions is desired, consider modifying the logic to allow a controlled reversal, perhaps with a timelock, governance vote, or a higher-level access control mechanism.


### `L-01` — Initial Restricted Transfer Mode  *(Severity: Low · Status: Unresolved)*

Upon deployment, the `AKEToken` contract initializes with `_transferMode` set to `CONTROLLED`. This means that token transfers are restricted from the outset, only allowing transfers where either the sender or receiver is the `_transferController`. This might be unexpected for users anticipating a standard, unrestricted ERC20 token (7.4 Economic, 7.8 Operations).

**Recommendation:** Clearly document the initial transfer restrictions and the process by which the token's transfer mode will transition to `NORMAL`. This transparency will help manage user expectations and prevent confusion regarding token functionality.


### `I-01` — Interface Mismatch for `isTransferController`  *(Severity: Informational · Status: Unresolved)*

The `isTransferController` function in the `IFourERC20` interface is declared as `external returns (bool)`, while its implementation in `AKEToken` is `external view returns (bool)`. Although this difference does not cause a runtime error (a `view` function can be called where a non-`view` is expected), it represents an inconsistency between the interface and its concrete implementation (7.1 Architecture).

**Recommendation:** Update the `IFourERC20` interface to include the `view` keyword for the `isTransferController` function to accurately reflect the implementation in `AKEToken`. This ensures better adherence to interface contracts and improves code clarity.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2c3a...f7db`](https://bscscan.com/address/0x2c3a8ee94ddd97244a93bc48298f97d2c412f7db) |
| **Network** | BNB Chain |
| **Price** | $0.004249 |
| **24h Volume** | $14.32M |
| **Liquidity** | $1.04M |
| **Volume / Liquidity** | 13.8× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 56.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 34847 buys / 38524 sells |

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

## Frequently Asked Questions

### Is AKE a scam?

Based on automated analysis, AKE scores 64/100 (High Risk) on our risk scale. No honeypot was detected, but always verify independently before investing.

### Is AKE safe to buy?

Our scanner flagged a risk score of 64/100. Ownership has not been renounced, which is a risk factor. DYOR before purchasing any token.

### Has AKE been audited?

The contract has not been verified on-chain. Verification is not the same as a full security audit. Use Quantum Audit's free tool to run a deeper analysis of the contract code.

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x4d3bf29ba30f8bfe4624e7678709afa195689c5d)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ake-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-07-26*

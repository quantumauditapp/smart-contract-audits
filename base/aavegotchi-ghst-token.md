---
token: Aavegotchi GHST Token
ticker: GHST
network: base
risk_score: 60
status: medium
date: 2026-08-30
---

# Aavegotchi GHST Token (GHST) — Smart Contract Security Analysis | Base

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/aavegotchi-ghst-token-base)

---

## Audit Summary

The OptimismMintableERC20 contract provides a standard ERC-20 token with controlled minting and burning capabilities, intended for cross-chain bridging. The contract leverages well-audited OpenZeppelin libraries and implements clear access control, restricting token supply manipulation to a designated bridge address. While the contract's internal code is robust, a significant centralization risk exists due to its reliance on the security of the external bridge contract, which has exclusive control over token minting and burning. The contract is non-upgradeable, simplifying its architecture but requiring redeployment for any future changes.

> **Final Recommendation:** Prioritize a comprehensive security audit of the associated `BRIDGE` contract, as its security directly dictates the integrity of this token. Ensure robust operational procedures are in place for managing the `BRIDGE` address, including multi-signature controls and emergency response plans. Given the non-upgradeable nature, plan for potential future redeployments and the associated migration efforts if critical addresses or logic require changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract exhibits strong technical security, leveraging battle-tested OpenZeppelin libraries for its ERC20 implementation (7.2 Code Security). Access control for critical `mint` and `burn`… |
| **Governance / Economics** | 1/10 | High | The economic model of the `OptimismMintableERC20` token is inherently tied to the security of its external `BRIDGE` contract (7.4 Economic, 7.6 External). The `BRIDGE` possesses exclusive rights to… |
| **Upgrades** | 3/10 | High | This contract is designed without an upgradeability mechanism, which simplifies its architecture and reduces the attack surface associated with proxy patterns (7.7 Upgrades). The `Semver`… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 50.1% |
| **Top-3 Unlocked** | ⚠️ 97.3% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 3 Informational_

### `H-01` — Centralization Risk and External Dependency on Bridge  *(Severity: High · Status: Unresolved)*

The `OptimismMintableERC20` contract grants exclusive minting and burning privileges to the `BRIDGE` address. This design introduces a significant centralization risk, as the security and integrity of the token are entirely dependent on the security of the `BRIDGE` contract. A compromise of the `BRIDGE` contract would allow an attacker to arbitrarily mint or burn tokens, leading to a loss of trust and potential economic exploit. (7.3 Access Control, 7.4 Economic, 7.6 External)

**Recommendation:** Ensure the `BRIDGE` contract itself undergoes rigorous security audits and implements robust access controls (e.g., multi-signature wallets, time-locks) to mitigate the risk of a single point of failure. Implement comprehensive monitoring for unusual activity originating from the `BRIDGE` address.


### `L-01` — Immutability of Bridge and Remote Token Addresses  *(Severity: Low · Status: Unresolved)*

The `BRIDGE` and `REMOTE_TOKEN` addresses are set as `immutable` in the constructor. While this enhances security by preventing unauthorized modification post-deployment, it also means these critical addresses cannot be updated if the underlying bridge contract or remote token contract needs to be changed (e.g., due to an upgrade or a critical vulnerability in the bridge). This requires a full redeployment of the `OptimismMintableERC20` contract and an update to the bridge's configuration if such a change becomes necessary. (7.1 Architecture, 7.8 Operations)

**Recommendation:** Acknowledge this design trade-off. For future versions, consider if a controlled mechanism for updating these addresses (e.g., via a governance-controlled proxy or a timelock) might be beneficial, weighing the added complexity against the operational flexibility gained. For the current version, ensure clear documentation and operational plans for redeployment scenarios.


### `I-01` — Use of Well-Audited OpenZeppelin Libraries  *(Severity: Informational · Status: Unresolved)*

The contract leverages standard and widely-audited OpenZeppelin contracts (ERC20, IERC165, Strings). This significantly reduces the risk of common vulnerabilities related to token standards and utility functions, contributing to the overall robustness of the codebase. (7.2 Code Security)

**Recommendation:** Continue to utilize well-established and audited libraries for core functionalities to maintain high security standards.


### `I-02` — Clear and Effective Access Control  *(Severity: Informational · Status: Unresolved)*

The `onlyBridge` modifier is correctly implemented and applied to the `mint` and `burn` functions, ensuring that only the designated `BRIDGE` contract can perform these critical operations. This clear access control mechanism prevents unauthorized token supply manipulation. (7.3 Access Control)

**Recommendation:** Maintain clear and explicit access control mechanisms for all sensitive functions to prevent unauthorized actions.


### `I-03` — Non-Upgradeability  *(Severity: Informational · Status: Unresolved)*

The contract is not designed with an upgrade proxy pattern. This simplifies the contract's architecture and reduces the attack surface associated with upgrade mechanisms. However, any future feature enhancements or bug fixes would necessitate deploying a new contract and updating all integrations, including the `BRIDGE` contract, to point to the new address. (7.7 Upgrades)

**Recommendation:** Document the non-upgradeable nature of the contract and establish a clear process for redeployment and migration if future changes are required. Ensure all dependent systems are aware of this design choice.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcd2f...9bcb`](https://basescan.org/address/0xcd2f22236dd9dfe2356d7c543161d4d260fd9bcb) |
| **Network** | Base |
| **Price** | $0.06485 |
| **24h Volume** | $343.2K |
| **Liquidity** | $700.8K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 90.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 811 buys / 1471 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x41d4934322f2bd6fe1dbe4124070fe61651a2067)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/aavegotchi-ghst-token-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-30*

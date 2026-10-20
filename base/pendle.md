---
token: Pendle
ticker: PENDLE
network: base
risk_score: 56
status: medium
date: 2026-09-23
---

# Pendle (PENDLE) — Smart Contract Security Analysis | Base

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pendle-base)

---

## Audit Summary

The OptimismMintableERC20 contract implements a standard ERC-20 token designed for cross-chain bridging, allowing a designated bridge contract to mint and burn tokens. The contract leverages OpenZeppelin libraries for core ERC-20 functionality and enforces strict access control for minting and burning operations. While the implementation is robust, the token's security and economic stability are heavily reliant on the integrity and security of the external bridge contract.

> **Final Recommendation:** Ensure the `BRIDGE` contract, which has sole authority to mint and burn tokens, undergoes rigorous security audits and maintains robust operational security. Implement comprehensive monitoring for the `BRIDGE` contract's activities, especially for minting and burning events. During deployment, carefully verify all constructor arguments, particularly the `_decimals` value, as it is immutable and cannot be corrected post-deployment.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract demonstrates good technical security practices (7.2 Code Security). It utilizes battle-tested OpenZeppelin libraries for ERC-20 implementation and Solidity 0.8.15, which includes… |
| **Governance / Economics** | 2/10 | High | The economic model of this token is straightforward: it's a mintable/burnable token whose supply is controlled by an external bridge (7.4 Economic). There is no internal governance mechanism within… |
| **Upgrades** | 3/10 | High | This contract is not designed to be upgradeable (7.7 Upgrades), which eliminates upgrade-specific risks such as storage collisions or logic errors during upgrades. All critical addresses and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `M-01` — Centralization Risk via Bridge Control  *(Severity: Medium · Status: Unresolved)*

The `OptimismMintableERC20` contract grants exclusive control over `mint` and `burn` operations to a single `BRIDGE` address. While this is an inherent design choice for a cross-chain bridge token, it introduces a significant centralization risk. If the `BRIDGE` contract or its controlling entity is compromised, an attacker could mint an arbitrary amount of tokens, leading to severe economic consequences for the token holders and the broader ecosystem. This falls under 7.3 Access Control and 7.4 Economic.

**Recommendation:** Acknowledge and manage the inherent risk associated with the centralized `BRIDGE` control. Implement robust security measures for the `BRIDGE` contract, including multi-signature requirements for critical operations, time-locks, and continuous monitoring. Consider a decentralized bridge architecture in future iterations if feasible.


### `L-01` — Immutable Decimals Set at Deployment  *(Severity: Low · Status: Unresolved)*

The `DECIMALS` variable is set as `immutable` in the constructor and cannot be changed after deployment. While immutability is generally a good security practice, an incorrect `_decimals` value set during deployment would permanently affect how the token is displayed and interacted with across all integrated platforms. This could lead to significant user experience issues or incorrect calculations in DeFi protocols. This relates to 7.8 Operations.

**Recommendation:** Ensure thorough testing and verification of the `_decimals` parameter during the deployment process. Implement a robust deployment checklist and double-check all constructor arguments before final deployment to production environments.


### `I-01` — Redundant View Functions for Bridge and Remote Token Addresses  *(Severity: Informational · Status: Unresolved)*

The contract includes redundant view functions: `l1Token()` and `remoteToken()` both return the `REMOTE_TOKEN` address, and `l2Bridge()` and `bridge()` both return the `BRIDGE` address. While not a vulnerability, this duplication adds unnecessary code complexity and slightly increases contract size. This relates to 7.2 Code Security.

**Recommendation:** Consider consolidating these redundant functions to a single, clearly named function for each address (e.g., `remoteToken()` and `bridge()`) to improve code clarity and reduce contract size. If the duplication is for interface compatibility (e.g., `ILegacyMintableERC20`), document this design choice clearly.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa99f...eb3e`](https://basescan.org/address/0xa99f6e6785da0f5d6fb42495fe424bce029eeb3e) |
| **Network** | Base |
| **Price** | $2.4200 |
| **24h Volume** | $191.9K |
| **Liquidity** | $218.4K |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 65.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 753 buys / 521 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x016df91005f30039c9f1a89b44db5e8c60613603)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pendle-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-23*

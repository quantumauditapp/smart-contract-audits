---
token: Supergemma4-26b-multimodal
ticker: SUPERGEMMA
network: base
risk_score: 47
status: high
date: 2026-08-01
---

# Supergemma4-26b-multimodal (SUPERGEMMA) — Smart Contract Security Analysis | Base

> **Risk Score: 47/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/supergemma4-26b-multimodal-base)

---

## Audit Summary

The DERC20 token contract implements an ERC20 token with voting, permit, and custom inflation and vesting mechanisms. It utilizes battle-tested OpenZeppelin libraries for core functionalities. The contract design centralizes significant control in the owner, particularly regarding token supply dynamics and a unique pool locking mechanism. While the code quality is generally good, the high degree of owner privilege introduces notable economic and operational risks.

> **Final Recommendation:** To mitigate the risks associated with centralized control, consider implementing a multi-signature wallet or a decentralized autonomous organization (DAO) for the contract's ownership. This would distribute control over critical functions like `lockPool`, `burn`, and `updateMintRate`, reducing the impact of a single point of failure or compromised key. For the `lockPool` functionality, re-evaluate its necessity; if retained, implement a timelock and a robust governance process to prevent arbitrary freezing of funds. Additionally, ensure the complete vesting mechanism is implemented and publicly available for users to claim their vested tokens.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract leverages battle-tested OpenZeppelin libraries for ERC20, ERC20Votes, and ERC20Permit functionalities, enhancing code security (7.2). Custom logic for inflation and vesting appears… |
| **Governance / Economics** | 4/10 | Medium | The contract exhibits a high degree of centralization, primarily due to the `Ownable` pattern (7.5). The owner has sole control over critical economic parameters such as the yearly mint rate, token… |
| **Upgrades** | 7/10 | Low | The contract is not designed as an upgradeable proxy (7.7), which simplifies its architecture and eliminates upgrade-related risks such as storage collisions or proxy implementation vulnerabilities.… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 87.6% |
| **Top-3 Unlocked** | ⚠️ 95.8% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 1 Informational_

### `H-01` — Centralized Control over Pool Funds via `lockPool`  *(Severity: High · Status: Unresolved)*

The `lockPool` function allows the contract owner to designate a `pool` address and subsequently prevent any token transfers *from* that address by setting `isPoolUnlocked` to `false`. This mechanism is enforced in the `_beforeTokenTransfer` hook. This grants the owner the unilateral power to freeze tokens held by any contract designated as the `pool`, posing a significant centralization and economic risk (7.3, 7.4).

**Recommendation:** Re-evaluate the necessity of the `lockPool` mechanism. If this functionality is critical, consider implementing a timelock, multi-signature approval, or a more decentralized governance mechanism for its activation. Clearly document this capability and its intended use to ensure transparency for users and integrators.


### `M-01` — Owner's Sole Control over Inflation and Burning  *(Severity: Medium · Status: Unresolved)*

The `mintInflation` function, while publicly callable, directs all newly minted tokens to the `owner()`. Additionally, the `burn` and `updateMintRate` functions are restricted to `onlyOwner`. This grants the owner significant, centralized control over the token's supply dynamics, including inflation and deflation, which could be exploited or lead to governance concerns (7.3, 7.4, 7.5).

**Recommendation:** For core economic parameters like inflation and burning, consider transitioning to a more decentralized governance model (e.g., a DAO) or implementing a timelock for sensitive operations. This would provide transparency, introduce a delay for malicious actions, and reduce reliance on a single entity.


### `L-01` — Missing `releaseVestedTokens` Function  *(Severity: Low · Status: Unresolved)*

The contract includes a `VestingData` struct, a `getVestingDataOf` mapping, and several vesting-related error messages (`ReleaseAmountInvalid`, `VestingNotStartedYet`). However, the `releaseVestedTokens` function, which would allow users to claim their vested tokens, is not present in the provided source code snippet. This makes the vesting mechanism incomplete or unusable as presented (7.1).

**Recommendation:** Ensure the complete vesting logic, including the `releaseVestedTokens` function, is implemented and available for users to claim their vested tokens. This function should correctly calculate and transfer available vested amounts based on `vestingStart`, `vestingDuration`, and `block.timestamp`.


### `I-01` — BUSL-1.1 License Usage  *(Severity: Informational · Status: Unresolved)*

The contract uses the Business Source License 1.1 (BUSL-1.1). This is a non-open-source license that typically restricts usage for a certain period (e.g., 3-5 years) before converting to an open-source license like MIT. This licensing choice might have implications for project adoption, integration, and future development depending on the specific terms (7.6).

**Recommendation:** Be aware of the implications of BUSL-1.1. Ensure all stakeholders understand the licensing terms and their potential impact on the project's ecosystem, community engagement, and future development plans.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x572c...aba3`](https://basescan.org/address/0x572c4fa77623652411574c51b5ddb7e1b750aba3) |
| **Network** | Base |
| **Price** | $0.00001181 |
| **24h Volume** | $168.3K |
| **Liquidity** | $511.8K |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 33.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 505 buys / 726 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0x7016371c9642e346094b51b9603e429828d3f8063537770020115af81b019145)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/supergemma4-26b-multimodal-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-01*

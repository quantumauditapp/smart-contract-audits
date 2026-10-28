---
token: NODF
ticker: NODF
network: base
risk_score: 58
status: medium
date: 2026-10-28
---

# NODF (NODF) — Smart Contract Security Analysis | Base

> **Risk Score: 58/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nodf-base-6970)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 token with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation, pool locking, and vesting releases. While the code follows standard OpenZeppelin patterns, the high degree of administrative control presents a significant centralization risk for token holders.

> **Final Recommendation:** To improve trust, the protocol should consider transitioning ownership to a multi-signature wallet or a decentralized DAO. Implementing a timelock on sensitive functions like updateMintRate and lockPool would provide transparency and allow the community to react to administrative changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture utilizes robust OpenZeppelin libraries for ERC-20 and governance features (7.1 Architecture). Code security is high, adhering to modern Solidity practices with proper input… |
| **Governance / Economics** | 3/10 | High | Economic parameters are managed by the owner, allowing for inflation adjustments up to a hard-coded limit (7.4 Economic). Governance is currently centralized, lacking a decentralized voting mechanism… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy and does not support upgrades (7.7 Upgrades). This ensures immutability of the core logic, which is a strength for security. No upgrade-related risks are present. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to mint new tokens via the updateMintRate and release functions. This allows the owner to increase the total supply at their discretion, which can dilute the value of existing holdings.

**Recommendation:** Implement a timelock for all minting-related functions to ensure that any supply changes are transparent and predictable to the community.


### `CP-05` — Centralized Control Over Transfer Functionality  *(Severity: Medium · Status: Unresolved)*

The owner can toggle the isPoolUnlocked switch using the lockPool and unlockPool functions. This allows the owner to arbitrarily halt or enable token transfers, effectively freezing user assets or liquidity.

**Recommendation:** Remove the ability for the owner to pause transfers, or move this functionality to a decentralized governance vote to prevent potential abuse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 1,503 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,503 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $472K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $472K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x46a7...d6ff`](https://basescan.org/address/0x46a719bd1a5cc429dc3ab3499d797fb0b567d6ff) |
| **Network** | Base |
| **Price** | $0.9194 |
| **24h Volume** | $1.29M |
| **Liquidity** | $472.5K |
| **Volume / Liquidity** | 2.7× |
| **Token Age** | 3h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1668 buys / 123 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xcc1d3ce036a7f64a65729c941917cdffcd0e0e41ee03505db51c8d453466c07a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nodf-base-6970)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*

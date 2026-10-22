---
token: NODF
ticker: NODF
network: base
risk_score: 77
status: high
date: 2026-10-22
---

# NODF (NODF) — Smart Contract Security Analysis | Base

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nodf-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with additional governance and vesting capabilities. The protocol relies on a centralized owner to manage inflation rates and pool access. While the code follows standard OpenZeppelin patterns, the high degree of administrative control over token supply and transferability presents a significant centralization risk.

> **Final Recommendation:** To improve security and trust, consider transitioning ownership to a multi-signature wallet or a decentralized DAO governance contract. This would mitigate the risk of a single point of failure regarding the minting and pool-locking functions.

Additionally, implement a timelock mechanism for all privileged functions. A delay of 24-48 hours on administrative actions like `updateMintRate` or `lockPool` would provide users with sufficient notice and the ability to react to changes in the protocol's economic parameters.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The contract utilizes well-audited OpenZeppelin libraries for ERC-20 and governance features. 7.1 Architecture is modular, and 7.2 Code Security is high due to the use of standard, battle-tested… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance aspects are heavily centralized under the contract owner. The owner has the ability to mint tokens up to a 2% annual cap and manipulate transferability via the pool… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. The logic is immutable, providing transparency to users regarding the current rules. No upgrade risk exists for this specific deployment. |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner can call updateMintRate and release to increase the total supply of tokens. This allows the owner to dilute existing token holders at their discretion within the defined annual limits.

**Recommendation:** Transition ownership to a decentralized governance model or implement a timelock on all minting-related functions to ensure transparency and community oversight.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to lock or unlock the pool via lockPool and unlockPool. This effectively allows the owner to halt all transfers or sales of the token, creating a significant centralization risk for liquidity providers and users.

**Recommendation:** Remove the ability for the owner to arbitrarily lock transfers, or restrict this functionality to a time-bound emergency pause mechanism governed by a multi-signature or DAO.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 6,042 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

6,042 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $177K (DexScreener, all pools). 24h trading volume $2.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $177K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd82f...3465`](https://basescan.org/address/0xd82f874713e4a93217f05d8a824dcff3b8873465) |
| **Network** | Base |
| **Price** | $1.2500 |
| **24h Volume** | $2.17M |
| **Liquidity** | $177.1K |
| **Volume / Liquidity** | 12.3× |
| **Token Age** | 7h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3427 buys / 2912 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xb5ba82cdd0ad07571d3f811a69fde6513d253b02cfa5af203484b674ae155bbf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nodf-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*

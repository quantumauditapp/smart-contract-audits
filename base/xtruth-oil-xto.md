---
token: XTruth Oil (XTO)
ticker: XTO
network: base
risk_score: 59
status: medium
date: 2026-10-24
---

# XTruth Oil (XTO) (XTO) — Smart Contract Security Analysis | Base

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xtruth-oil-xto-base)

---

## Audit Summary

The DERC20 contract is a standard ERC-20 implementation with added governance, voting, and vesting capabilities. The protocol relies heavily on a centralized owner to manage minting rates and liquidity pool access. While the code follows established OpenZeppelin standards, the high degree of administrative control over token supply and transferability introduces significant centralization risk for token holders.

> **Final Recommendation:** To improve security and trust, consider transitioning the owner role to a multi-signature wallet or a decentralized DAO structure. This would mitigate the risks associated with a single point of failure regarding minting and pool locking.

Additionally, implement a timelock controller for all privileged functions. This would provide transparency to the community by ensuring that any changes to minting rates or pool access are subject to a mandatory delay before execution.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes robust, battle-tested OpenZeppelin libraries for ERC-20, voting, and permit functionality. Coverage 7.1 Architecture and 7.2 Code Security are strong, adhering to standard… |
| **Governance / Economics** | 3/10 | High | The economic model is governed by the owner, who can influence supply through inflation adjustments (7.4 Economic). 7.5 Governance is limited, as there is no decentralized mechanism to check the… |
| **Upgrades** | 4/10 | Medium | The contract is not a proxy and does not support 7.7 Upgrades. 7.8 Operations are static, meaning the logic cannot be altered post-deployment. This provides immutability but prevents fixing logic… |

## Security Findings

_🟡 2 Medium · ⚪ 5 Informational_

### `CP-01` — Centralized Control Over Token Supply  *(Severity: Medium · Status: Unresolved)*

The owner has the authority to call updateMintRate and release, which can increase the total supply of tokens. This allows the owner to dilute the holdings of all existing token holders at their discretion.

**Recommendation:** Implement a timelock on all minting-related functions and consider capping the total supply or moving to a pre-defined, immutable emission schedule.


### `CP-05` — Centralized Control Over Transferability  *(Severity: Medium · Status: Unresolved)*

The owner can use the lockPool and unlockPool functions to enable or disable transfers for specific pools. This gives the owner the power to effectively freeze user assets or prevent trading activity.

**Recommendation:** Remove the ability for the owner to arbitrarily lock pools, or replace this mechanism with a decentralized governance vote to trigger such actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. Of that, 3.8% burned — not holders that can sell, so excluded from the concentration score. What remains: 16.2% in wallets, 80.0% in other contracts. The deployer/owner wallet itself holds 16.2%. 2,138 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

2,138 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $230K (DexScreener, all pools). 24h trading volume $971K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $230K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd867...7e30`](https://basescan.org/address/0xd8679ef9e2b2f54aac4adc43399e0cd5baf97e30) |
| **Network** | Base |
| **Price** | $0.5394 |
| **24h Volume** | $971.4K |
| **Liquidity** | $230.0K |
| **Volume / Liquidity** | 4.2× |
| **Token Age** | 13h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1347 buys / 1287 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb7e1cd788f3cdfa6f2e92a45b3d250de61da2660fdf38fc13c490271bef36b25)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xtruth-oil-xto-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

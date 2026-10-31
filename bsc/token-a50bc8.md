---
token: 狙姬
ticker: 狙姬
network: bsc
risk_score: 55
status: medium
date: 2026-10-31
---

# 狙姬 (狙姬) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 55/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/token-a50bc8-bsc)

---

## Audit Summary

GangToken is an ERC-20 token implementation featuring centralized control mechanisms managed by a 'launchpad' address. The contract includes standard token functionality alongside specific administrative functions that allow the launchpad to reclaim tokens or pull funds from user allowances. The architecture relies heavily on the security of the launchpad address, which holds significant power over token flows and supply management.

> **Final Recommendation:** The protocol should prioritize the security of the launchpad address, as it holds extensive control over user balances and token mechanics. Implementing a multi-signature wallet or a timelock for the launchpad functions would significantly mitigate the risk of unauthorized or malicious administrative actions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin ERC-20 patterns, ensuring 7.1 Architecture and 7.2 Code Security compliance. 7.3 Access Control is implemented via a custom 'onlyLaunchpad' modifier. 7.6… |
| **Governance / Economics** | 1/10 | High | 7.4 Economic and 7.5 Governance aspects are centralized under the launchpad address. The ability to reclaim tokens or pull allowances creates a significant trust requirement for token holders. While… |
| **Upgrades** | 4/10 | Medium | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are restricted to the launchpad, which manages the lifecycle of the token pair and transfer rules. No further… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Null Address |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `CP-01` — Centralized Control over Token Balances  *(Severity: Medium · Status: Unresolved)*

The 'reclaim' and 'pullFor' functions allow the launchpad address to move tokens from user wallets or spend user allowances without direct user consent. This grants the launchpad controller the ability to effectively seize or redistribute tokens, which poses a significant centralization risk to token holders.

**Recommendation:** Restrict the use of these functions to emergency scenarios only, and consider implementing a timelock or multi-signature requirement for the launchpad address to prevent unilateral actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 39.3% of supply. Of that, 23.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 9.6% in wallets, 6.0% in other contracts. The deployer/owner wallet itself holds 1.6%. 467 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

467 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $20K (DexScreener, all pools). 24h trading volume $692K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: 2.2% on buy, 2.21% on sell. Market: $20K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x481f...7059`](https://bscscan.com/address/0x481f5963bf10cba972d52f138740155b2cda7059) |
| **Network** | BNB Chain |
| **Price** | $0.00004277 |
| **24h Volume** | $691.7K |
| **Liquidity** | $19.8K |
| **Volume / Liquidity** | 34.9× |
| **Token Age** | 12h |
| **Top-10 Holders** | 39.3% of supply |
| **Buy / Sell Tax** | 2.2% / 2.2% |
| **24h Transactions** | 4873 buys / 8226 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x04bde3a60b58c0cffe5e16ba640eab57e50d8336)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/token-a50bc8-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

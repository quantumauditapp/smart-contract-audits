---
token: American Oil Dividend Fund
ticker: AODF
network: base
risk_score: 61
status: medium
date: 2026-10-30
---

# American Oil Dividend Fund (AODF) — Smart Contract Security Analysis | Base

> **Risk Score: 61/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-73ca)

---

## Audit Summary

The contract at the provided address is not verified on the Base block explorer. Consequently, the source code is inaccessible for security analysis. Investors should exercise extreme caution as the lack of transparency prevents verification of ownership, tax mechanisms, or liquidity safety.

> **Final Recommendation:** Do not interact with this contract. The lack of source code verification is a major red flag that prevents any meaningful security assessment. Without transparency, there is no assurance that the contract functions as intended or that funds are secure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The technical architecture cannot be assessed due to the absence of verified source code. 7.1 Architecture, 7.2 Code Security, 7.3 Access Control, and 7.6 External dependencies remain entirely… |
| **Governance / Economics** | 4/10 | Medium | Economic parameters such as 7.4 Economic sustainability and 7.5 Governance mechanisms are hidden from public view. There is no way to verify if the token supply is inflationary or if the owner has… |
| **Upgrades** | 6/10 | Medium | The contract's upgradeability status (7.7 Upgrades) cannot be determined. It is unknown if the contract uses a proxy pattern or if the logic can be altered post-deployment. 7.8 Operations are… |

## Security Findings

_🔴 1 Critical · ⚪ 5 Informational_

### `C-01` — Unverified Source Code  *(Severity: Critical · Status: Unresolved)*

The contract source code is not published on the block explorer, making it impossible to verify the logic, ownership, or security of the contract.

**Recommendation:** Verify the contract source code on the block explorer to allow for community and security auditing.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.7% of supply. What remains: 28.7% in wallets, 0.0% in other contracts. The deployer/owner wallet itself holds 15.1%. 713 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

713 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $130K (DexScreener, all pools). 24h trading volume $878K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $130K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x20ad...0788`](https://basescan.org/address/0x20ad201a7585f1ef6185039b305f7b1bfff80788) |
| **Network** | Base |
| **Price** | $0.0004665 |
| **24h Volume** | $878.3K |
| **Liquidity** | $130.1K |
| **Volume / Liquidity** | 6.7× |
| **Token Age** | 12h |
| **Top-10 Holders** | 28.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1199 buys / 947 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0x49efc5ee53c00b67782848ab738008ad22f0b1c2ba473baa21a724844a20dd95)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/american-oil-dividend-fund-base-73ca)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

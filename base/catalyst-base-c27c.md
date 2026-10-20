---
token: Catalyst
ticker: CATALYST
network: base
risk_score: 67
status: high
date: 2026-10-14
---

# Catalyst (CATALYST) — Smart Contract Security Analysis | Base

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/catalyst-base-c27c)

---

## Audit Summary

This report is based on an audit request for the contract at 0xa1af1beabd885181a4927f91d66dfe2140cb077c on the Base network. No Solidity source code was provided for analysis. Therefore, a comprehensive security audit could not be performed, and no specific vulnerabilities or strengths can be identified. The findings are limited to an informational note regarding the absence of source code.

> **Final Recommendation:** To enable a comprehensive security assessment, it is crucial to provide the full Solidity source code for the contract at 0xa1af1beabd885181a4927f91d66dfe2140cb077c. This will allow for a thorough analysis of its architecture, security mechanisms, economic model, and upgradeability, leading to actionable security recommendations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | Due to the absence of Solidity source code, a technical analysis of the contract's architecture (7.1), code security (7.2), and access control mechanisms (7.3) could not be performed. Without the… |
| **Governance / Economics** | 1/10 | High | Without access to the contract's source code, an assessment of its economic model (7.4), governance structure (7.5), and interactions with external protocols (7.6) is not possible. This prevents the… |
| **Upgrades** | 5/10 | Medium | The upgradeability aspects (7.7) and operational procedures (7.8) of the contract cannot be determined without the source code. It is unknown if the contract employs a proxy pattern (e.g., UUPS… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 1 address(es) other than the owner/deployer. One of them — a contract, 0xdc2e…1fd8 — holds 100.0% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `I-01` — No Source Code Provided for Audit  *(Severity: Informational · Status: Unresolved)*

The audit was requested for the contract at address 0xa1af1beabd885181a4927f91d66dfe2140cb077c on the Base network. However, no Solidity source code was supplied for analysis. Without the source code, a detailed security audit, including vulnerability identification, architectural review, and economic analysis, cannot be performed.

**Recommendation:** Provide the complete and verified Solidity source code for the contract. This includes all dependent libraries and imported contracts, along with the correct compiler version and optimization settings used during deployment. This will enable a full and accurate security assessment.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 48.8% of supply. What remains: 21.9% in wallets, 26.8% in other contracts. 1,053 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1,053 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $114K (DexScreener, all pools). 24h trading volume $129K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mint capability could not be read. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $114K of DEX liquidity across 1 pools. Launch: 1 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 1 day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 1 day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa1af...077c`](https://basescan.org/address/0xa1af1beabd885181a4927f91d66dfe2140cb077c) |
| **Network** | Base |
| **Price** | $0.577 |
| **24h Volume** | $128.5K |
| **Liquidity** | $114.3K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 1d |
| **Top-10 Holders** | 48.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 676 buys / 96 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xf7df59789c2dcc67f7e692f4cd57511c130a9885)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/catalyst-base-c27c)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*

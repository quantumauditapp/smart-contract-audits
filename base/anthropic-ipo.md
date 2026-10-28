---
token: Anthropic IPO
ticker: ANT
network: base
risk_score: 48
status: medium
date: 2026-10-28
---

# Anthropic IPO (ANT) — Smart Contract Security Analysis | Base

> **Risk Score: 48/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anthropic-ipo-base)

---

## Audit Summary

The StandardToken contract is a standard ERC-20 implementation utilizing OpenZeppelin libraries. It includes burnable and permit functionality. The contract lacks any privileged roles or administrative backdoors, ensuring a decentralized and immutable token structure.

> **Final Recommendation:** The contract is secure and follows standard practices. No further action is required as the code is immutable and lacks privileged functions that could introduce risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows industry-standard OpenZeppelin patterns for ERC-20 tokens. Code security is high due to the reliance on audited, battle-tested libraries for core logic. 7.1 Architecture… |
| **Governance / Economics** | 4/10 | Medium | The token has no governance or economic parameters that can be adjusted by an owner. 7.4 Economic: Standard supply mechanics; 7.5 Governance: None; 7.8 Operations: Fully automated via smart contract… |
| **Upgrades** | 8/10 | Low | The contract is not a proxy and is immutable. 7.7 Upgrades: Not applicable as the contract cannot be modified after deployment. |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No issues identified in the reviewed source  *(Severity: Informational · Status: Acknowledged)*

The verified source code was reviewed and no issue rising to Informational severity or above was identified. This is a statement about the code that was read, not a guarantee: the review covers the published source only. Fact-layer checks (mint capability, holder concentration) were applied separately and feed the risk score.

**Recommendation:** Re-check after any contract upgrade or ownership change, both of which can alter behaviour without changing this page.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 85.4% of supply. What remains: 85.4% in wallets, 0.0% in other contracts. 527 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

527 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $59K (DexScreener, all pools). 24h trading volume $36K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $59K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x545f...cfc7`](https://basescan.org/address/0x545f7abcbb0ff2ce93979794a8ce92eb4cfecfc7) |
| **Network** | Base |
| **Price** | $0.00003863 |
| **24h Volume** | $36.1K |
| **Liquidity** | $59.2K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 18h |
| **Top-10 Holders** | 85.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1061 buys / 757 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/base/0xaff5fa94ca78430ecb1855f5e77bf1a5bf5e993842823d3a45cdd62f2c4ac663)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anthropic-ipo-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*

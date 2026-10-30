---
token: Zeroday
ticker: ZERODAY
network: solana
risk_score: 21
status: low
date: 2026-10-30
---

# Zeroday (ZERODAY) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/zeroday-sol-cd7d)

---

## Audit Summary

The Zeroday token (9ZRHMX...) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. However, the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, and the low liquidity pool creates significant slippage risks for holders. Third-party risk registry data confirms the low liquidity status.

> **Final Recommendation:** Investors should exercise extreme caution regarding the high volume-to-liquidity ratio, which often precedes volatility or liquidity exhaustion. Monitor the DEX pool for any unexpected price deviations.

Verify that the token address matches the official contract provided by the project team. Given the low liquidity, avoid placing large market orders to prevent significant slippage losses.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program with no active transfer hooks or default frozen states. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis reveals a high volume-to-liquidity ratio of 303.08, indicating suspicious trading activity. 7.6 External market data shows liquidity is only $2,409, though 100% of the pool is… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable. 7.8 Operations are secure as metadata is immutable and no balance-mutating authorities exist. The token configuration is finalized. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $2,409. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth before executing trades.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 303.08x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity may not represent organic market interest.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $25K (DexScreener, all pools). 24h trading volume $346K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $25K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`9ZRHMX...pump`](https://solscan.io/account/9ZRHMXqFTucBLuCs3TqmDEPjQCzhSuZ3bQR6dqpepump) |
| **Network** | Solana |
| **Price** | $0.00009665 |
| **24h Volume** | $338.1K |
| **Liquidity** | $24.7K |
| **Volume / Liquidity** | 13.7× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3154 buys / 1926 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/6lovbxun4oj6q2qvzwgmykjzyed8c7x8umug4pq3pgeq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/zeroday-sol-cd7d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

---
token: KuriboCoin
ticker: KURIBO
network: solana
risk_score: 24
status: low
date: 2026-10-24
---

# KuriboCoin (KURIBO) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/kuribocoin-sol)

---

## Audit Summary

KuriboCoin is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against administrative abuse. However, the token exhibits a high volume-to-liquidity ratio suggesting potential wash trading, and liquidity is very low. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity and high volume-to-liquidity ratio, which may lead to significant slippage and difficulty in exiting positions. Monitor the token on block explorers to ensure no unexpected minting or authority changes occur, despite the current revoked status.

Verify the current holder distribution once on-chain indexing services update to ensure no single entity controls a majority of the supply. Do not rely on the high trading volume as an indicator of organic market interest.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are permanently revoked. 7.2 Code Security is standard for SPL mints… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic and 7.5 Governance metrics indicate high risk due to very low liquidity ($8,525) and a volume/liquidity ratio of 132.27, which exceeds the 20x threshold for wash-trading signals. 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints are immutable. 7.8 Operations are secure as metadata is immutable and no balance-mutating authorities exist. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $8,525. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 132.27x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume may not reflect genuine market demand.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 82% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 17 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8WRdyR...pump`](https://solscan.io/account/8WRdyRqn2GeAxNb5MpGqHytXTD1MHEiTewbadR5hpump) |
| **Network** | Solana |
| **Price** | $0.00001619 |
| **24h Volume** | $1.12M |
| **Liquidity** | $9.7K |
| **Volume / Liquidity** | 115.5× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13436 buys / 9978 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fjirf8j2vlxkf1un2ex4odsrdufcyy1ltoy6sjhqtxfz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/kuribocoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

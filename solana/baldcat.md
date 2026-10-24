---
token: baldcat
ticker: BALDCAT
network: solana
risk_score: 24
status: low
date: 2026-10-24
---

# baldcat (BALDCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baldcat-sol)

---

## Audit Summary

The primary risk identified is an abnormal 24-hour volume-to-liquidity ratio of 48.75 on DEX markets, presenting a strong wash trading signal. Base technical controls are secured with both mint and freeze authorities permanently revoked and pool liquidity completely burned. Chain-native RPC holder distribution data was unavailable during this assessment.

> **Final Recommendation:** Analyze real-time transaction signatures on DEX pools to verify whether trading volume originates from organic market participants rather than automated circular wash-trading loops. Once RPC indexing for holder distribution is available, verify token distribution across the largest non-pool accounts to evaluate concentration risk prior to taking positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates on the spl-token-2022 program with a raw supply of 954,514,658,187,022 and 6 decimal places. Mint and freeze authorities are both revoked, precluding unauthorized token supply… |
| **Governance / Economics** | 7/10 | Low | Pool liquidity totals $16,166, with 100.0% of LP tokens burned to permanently prevent creator withdrawals. DEX market data indicates the trading pair was deployed 0 days ago with $788,093 in 24-hour… |
| **Upgrades** | 10/10 | Low | The mint possesses no upgradeable administrative keys as mint and freeze roles are set to null. Metadata mutability is disabled, ensuring token display parameters and branding cannot be altered… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 48.75x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for synthetic activity when assessing execution depth and avoid relying on 24-hour trading volume as a metric of true liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $886K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FFPSPa...pump`](https://solscan.io/account/FFPSPaZ6pZEeVET743ZBxAhbwQqKZhRp997dMWDNpump) |
| **Network** | Solana |
| **Price** | $0.00005226 |
| **24h Volume** | $780.5K |
| **Liquidity** | $18.7K |
| **Volume / Liquidity** | 41.8× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8992 buys / 6993 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6yutvnzenopxfen9ufxddsedkn1tqeon3jlzah4cqyes)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baldcat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

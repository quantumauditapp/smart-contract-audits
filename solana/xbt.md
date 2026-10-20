---
token: XBT
ticker: XBT
network: solana
risk_score: 21
status: low
date: 2026-10-19
---

# XBT (XBT) — Smart Contract Security Analysis | Solana

> **Risk Score: 21/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xbt-sol)

---

## Audit Summary

The primary risk identified is an extreme volume-to-liquidity ratio of 129.75, with 24-hour DEX volume reaching $2,428,257 against $18,715 in liquidity, signalling potential automated wash trading. Core mint and freeze authorities are safely revoked with zero adverse registry alerts. Holder concentration metrics were unavailable from chain-native RPC at the time of evaluation.

> **Final Recommendation:** Examine DEX swap transaction graphs to determine whether current trade turnover originates from organic unique buyers or circular bot transactions. Query the largest token accounts directly via native Solana RPC endpoints to manually verify wallet concentration before entering substantial positions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint utilizes the spl-token-2022 program with an initialized raw supply of 929310115620818 across 6 decimals. Both mint authority and freeze authority are permanently revoked (null), preventing… |
| **Governance / Economics** | 7/10 | Low | DEX liquidity is established at $18,715 with 100.0% of the LP position confirmed burned, ensuring pool liquidity cannot be drained by the deployer. Pair age stands at 0 days, contextualizing the… |
| **Upgrades** | 10/10 | Low | The token structure is fully immutable with no administrative authorities retained. Extension configurations confirm that transfer fee upgrades, transfer hook modifications, and metadata mutations… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 129.75x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for artificial trading inflation and inspect transaction dispersion across unique signatures prior to executing swaps.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 81% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23K (DexScreener, all pools). 24h trading volume $3.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23K of DEX liquidity across 28 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8NfX91...pump`](https://solscan.io/account/8NfX91yvHXyHKn8cnMjg9Q4bCeRLKFDoVtEomXstpump) |
| **Network** | Solana |
| **Price** | $0.00004537 |
| **24h Volume** | $2.43M |
| **Liquidity** | $18.9K |
| **Volume / Liquidity** | 128.1× |
| **Token Age** | 18h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23554 buys / 17990 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9cbefgu7crlytn7tfdr52o5yn4ppj8vy1wvdszk9gzsg)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xbt-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*

---
token: web4
ticker: COMPUTE
network: solana
risk_score: 20
status: low
date: 2026-10-19
---

# web4 (COMPUTE) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/web4-sol)

---

## Audit Summary

The primary risk identified is an anomalous volume-to-liquidity ratio of 75.11 ($2,906,247 24-hour volume against $38,692 liquidity), indicating potential artificial volume inflation. While mint and freeze permissions are revoked and pool liquidity is fully burned, chain-native RPC holder distribution data was unavailable during this assessment.

> **Final Recommendation:** Examine transaction history on-chain to determine whether swap activity stems from organic user demand or repeated cyclical trades among coordinated wallets. Query token largest accounts directly via RPC once available to evaluate wallet distribution prior to establishing exposure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint is deployed via the Token-2022 program with a raw supply of 961,835,816,964,339 units and 6 decimals. Both mint authority and freeze authority are permanently set to None, preventing… |
| **Governance / Economics** | 7/10 | Low | Total pool liquidity stands at $38,692, with 100.0% of LP tokens burned and unwithdrawable. The market records an extreme 24-hour trading turnover of $2,906,247 on a newly created pair (age 0 days)… |
| **Upgrades** | 10/10 | Low | Administrative keys are permanently revoked, eliminating minting, freezing, and account closure capabilities. Token metadata is immutable with mutable flags set to False. No upgradable transfer fees… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 75.11x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Analyze transaction logs for circular routing and repetitive wash trading before executing trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 85% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $49K (DexScreener, all pools). 24h trading volume $3.6M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $49K of DEX liquidity across 13 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GWe3TN...pump`](https://solscan.io/account/GWe3TNg1UPxeaSazxK8U49PDAqXCaX9Jc8zbttFLpump) |
| **Network** | Solana |
| **Price** | $0.0002032 |
| **24h Volume** | $2.89M |
| **Liquidity** | $42.1K |
| **Volume / Liquidity** | 68.7× |
| **Token Age** | 10h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 28366 buys / 23651 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cye8bngpo5rzruevnjxcrh997r8crqutsuvjvpvbhbhj)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/web4-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-19*

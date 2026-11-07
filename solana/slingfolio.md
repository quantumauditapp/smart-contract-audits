---
token: Slingfolio
ticker: SLINGFOLIO
network: solana
risk_score: 22
status: low
date: 2026-11-07
---

# Slingfolio (SLINGFOLIO) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/slingfolio-sol)

---

## Audit Summary

Slingfolio (SLINGFOLIO) exhibits secure base parameters with both mint and freeze authorities permanently revoked, and 100.0% of DEX pool liquidity permanently burned. However, DEX market activity reflects an anomalous volume-to-liquidity ratio of 28.68, indicating high potential for wash trading. Chain-native RPC holder distribution data was unavailable during this assessment.

> **Final Recommendation:** Inspect decentralized exchange transaction history directly to identify recurring bot loops before committing capital, accounting for the elevated volume-to-liquidity ratio. Re-query on-chain token largest accounts when RPC connectivity resumes to ensure circulating supply is not heavily concentrated among top individual wallets.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The mint operates under the spl-token-2022 program with an initialized raw supply of 948,706,134,775,279 across 6 decimals. Both mint authority and freeze authority are revoked (None), guaranteeing a… |
| **Governance / Economics** | 7/10 | Low | DEX liquidity totals $26,806, with 100.0% of LP tokens burned to ensure unremovable market depth. However, 24-hour DEX trading volume reached $768,893 on a 0-day-old pair, generating an elevated… |
| **Upgrades** | 10/10 | Low | All core administrative authorities are fully revoked, leaving no active keys capable of modifying mint state. Registry checks confirm balance mutability, metadata mutability, and transfer hook… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 28.68x liquidity ($768,893 volume against $26,806 liquidity) — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potential volume manipulation when assessing market demand, and evaluate transaction patterns for circular wash trades.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. This assessment covers the main pool, which holds 91% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $34K (DexScreener, all pools). 24h trading volume $840K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $34K of DEX liquidity across 26 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GoqdpM...pump`](https://solscan.io/account/GoqdpMVvqawNUvdfTmqXvvoSaDRrqDQexzG7wzf2pump) |
| **Network** | Solana |
| **Price** | $0.0001513 |
| **24h Volume** | $750.0K |
| **Liquidity** | $31.2K |
| **Volume / Liquidity** | 24.1× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12770 buys / 9186 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7g4rvlmnbubytt2cd8uuz6qhybfqdzzrknkl9633zsqa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/slingfolio-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-07*

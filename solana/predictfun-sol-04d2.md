---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 28
status: low
date: 2026-10-30
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-04d2)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high-risk economic indicators, specifically an extremely high volume-to-liquidity ratio suggesting potential wash trading and a lack of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high volume-to-liquidity ratio. Monitor the liquidity pool for sudden withdrawals, as the current lack of locks allows for potential removal of all backing assets.

Verify the current liquidity status on-chain before executing any trades. Avoid large positions given the low total liquidity and the high probability of artificial volume.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | 7.1 Architecture: The token is a standard SPL v3 mint. 7.2 Code Security: The mint uses the native, audited SPL Token program. 7.3 Access Control: Both mint and freeze authorities are revoked… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic: The liquidity pool is entirely unlocked, posing a significant risk of withdrawal. 7.5 Governance: Holder concentration data is unavailable. 7.6 External: The volume-to-liquidity ratio… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades: The mint is immutable with metadata_mutable set to False. No upgrade paths exist for the token program or its parameters. The configuration is fixed at deployment. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 214.63, which significantly exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Account for the high likelihood of manipulated volume when assessing market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity is fully exposed to withdrawal by the pool creator.

**Recommendation:** Treat the pool as removable until liquidity is provably locked or burned.


### `M-01` — High-Risk Third-Party Registry Signals  *(Severity: Medium · Status: Unresolved)*

Third-party registry flags indicate a large amount of unlocked liquidity and a low number of liquidity providers, increasing the risk of price volatility.

**Recommendation:** Monitor the liquidity provider addresses for signs of coordinated exit.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $94K (DexScreener, all pools). 24h trading volume $20.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $94K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5AQt8V...fQBo`](https://solscan.io/account/5AQt8VV5YmmmGmy8jifz7773xVv9w9NBQ8yzb7TQfQBo) |
| **Network** | Solana |
| **Price** | $0.0001275 |
| **24h Volume** | $20.38M |
| **Liquidity** | $93.9K |
| **Volume / Liquidity** | 217.1× |
| **Token Age** | 3h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21423 buys / 14027 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/o9sdnqiuje11eewkes4h3abjp84prejmplzbk2etnfa)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-04d2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 29
status: low
date: 2026-10-25
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-c11e)

---

## Audit Summary

The AlloX token mint has successfully revoked both mint and freeze authorities, mitigating risks of supply inflation and account freezing. However, the token exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio suggesting wash trading and a lack of locked liquidity. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume patterns. Monitor the liquidity pool for sudden withdrawals, as the current lack of locks allows for potential removal of all pool assets.

Verify the current liquidity status on-chain before executing any trades. Avoid large market orders to mitigate the impact of high slippage and potential volatility associated with the reported wash-trading signals.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for non-extension tokens. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a volume-to-liquidity ratio of 129.99, significantly exceeding the 20x threshold for wash-trading signals. 7.6 External data indicates 0% of liquidity is locked or… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to standard SPL mints. Metadata is immutable, and no transfer hooks or fee extensions are active. The configuration is fixed and cannot be altered by any authority. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 129.99, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation and account for high slippage when trading.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the liquidity is not protected against withdrawal by the pool creator or current holders.

**Recommendation:** Treat the pool as removable and monitor for liquidity depletion.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $348K (DexScreener, all pools). 24h trading volume $33.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $348K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4k8MuV...QNe5`](https://solscan.io/account/4k8MuVSJHxD9RiJHdDy9b3JSsYquX6sGUvHEthyMQNe5) |
| **Network** | Solana |
| **Price** | $0.00001343 |
| **24h Volume** | $33.39M |
| **Liquidity** | $347.6K |
| **Volume / Liquidity** | 96.1× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16385 buys / 14750 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/elde3zuy4fmxqszqxuqsnow6r1xskzjrowe3h2fvpqqq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-c11e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*

---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 26
status: low
date: 2026-11-05
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-a44d)

---

## Audit Summary

The token mint and freeze authorities are successfully revoked, preventing supply inflation and account freezing. However, the protocol exhibits high-risk economic indicators, specifically a volume-to-liquidity ratio suggesting wash trading and 100% of pool liquidity remaining unlocked. Holder distribution data was unavailable from the source.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool's liquidity levels on-chain to ensure the creator does not withdraw the remaining funds.

Verify the current liquidity pool address on-chain to track if any portion of the liquidity is moved to a time-locked contract. Avoid large market orders until the volume-to-liquidity ratio stabilizes to more sustainable levels.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic indicators show significant risk with a volume/liquidity ratio of 271.46, exceeding the 20x threshold for wash-trading signals. 7.5 Governance and 7.6 External signals indicate that 100%… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token. Metadata is immutable, and no transfer hooks or fee extensions are present. The token state is fixed and cannot be modified by the… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 271.46, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Monitor trading activity for signs of manipulation before executing large trades.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity provider can withdraw the entire pool at any time.

**Recommendation:** Treat the pool as removable until liquidity is burned or moved to a time-locked vault.


### `M-01` — Low Amount of LP Providers  *(Severity: Medium · Status: Unresolved)*

Third-party registry signals indicate a low number of liquidity providers, increasing the risk of price volatility.

**Recommendation:** Assess the depth of the order book before entering a position.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $147K (DexScreener, all pools). 24h trading volume $39.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $147K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3Tcaty...GHC7`](https://solscan.io/account/3TcatyZ3BffdhzmMmF2AcBbc4myVHUvtE63iUeeyGHC7) |
| **Network** | Solana |
| **Price** | $0.00001176 |
| **24h Volume** | $39.87M |
| **Liquidity** | $147.0K |
| **Volume / Liquidity** | 271.2× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35762 buys / 32491 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8qv79veb8ra4rlhi7ckxnup78is7hrqvdozjjzdsauyl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-a44d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

---
token: predictdotfun
ticker: PREDICT
network: solana
risk_score: 30
status: low
date: 2026-10-29
---

# predictdotfun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictdotfun-sol)

---

## Audit Summary

The PREDICT token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high risk due to extreme wash-trading signals and the lack of locked liquidity, which remains fully withdrawable by anonymous holders. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Before interacting, verify the current liquidity pool status on-chain to ensure the creator has not withdrawn the remaining funds. Monitor the token's volume-to-liquidity ratio to avoid executing trades during periods of extreme price manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is highly volatile with a volume/liquidity ratio of 237.87, indicating significant wash-trading (7.4 Economic). 100% of the pool liquidity is currently unlocked and potentially withdrawable… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns inherent to this SPL mint (7.7 Upgrades). The mint… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 237.87, which significantly exceeds the 20x threshold, indicating artificial trade volume.

**Recommendation:** Monitor trading activity for signs of price manipulation and avoid high-slippage trades.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool liquidity is burned or locked, meaning the liquidity provider can withdraw all funds at any time.

**Recommendation:** Verify if the liquidity provider has committed to a time-locked contract before providing liquidity.


### `M-01` — Third-Party Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

The token is flagged by a third-party registry for having a large amount of unlocked LP and single-holder ownership risks.

**Recommendation:** Perform independent due diligence on the developer's wallet history and liquidity management.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $108K (DexScreener, all pools). 24h trading volume $17.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $108K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EqGGUW...KcGy`](https://solscan.io/account/EqGGUWEVCHaNoJrDvdzzP4X6FwiM58BdHeXPxe1qKcGy) |
| **Network** | Solana |
| **Price** | $0.00009782 |
| **24h Volume** | $17.28M |
| **Liquidity** | $108.0K |
| **Volume / Liquidity** | 160.0× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16911 buys / 11477 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/4py9h92cxbbxurv9rvton1t2tjnmalcnexjm5cxgcvkq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictdotfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

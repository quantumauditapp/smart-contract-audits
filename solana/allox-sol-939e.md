---
token: AlloX
ticker: ALLOX
network: solana
risk_score: 29
status: low
date: 2026-10-23
---

# AlloX (ALLOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/allox-sol-939e)

---

## Audit Summary

The AlloX token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits significant economic risks, including a high volume-to-liquidity ratio suggesting potential wash trading and 100% of pool liquidity remaining unlocked. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high probability of artificial trading volume. Monitor the pool's liquidity levels on-chain to detect sudden withdrawals by the liquidity providers.

Verify the current liquidity provider addresses via block explorer tools to assess the risk of a liquidity pull. Avoid large positions until the liquidity is either burned or locked in a recognized time-locked contract.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing is possible (7.3… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume-to-liquidity ratio of 150.10, which is significantly above the 20x threshold, indicating potential wash trading (7.4 Economic). 100% of the pool liquidity is unlocked and… |
| **Upgrades** | 8/10 | Low | The token mint is immutable with no upgrade paths for metadata or transfer logic (7.7 Upgrades). Metadata is non-mutable, preventing branding changes post-launch (7.6 External). No administrative… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 150.10, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market demand.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

100% of the pool's liquidity is unlocked and can be withdrawn by the liquidity providers at any time.

**Recommendation:** Monitor the liquidity pool for sudden withdrawals; consider the risk of total liquidity removal.


### `M-01` — High-Risk Third-Party Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party risk registries have flagged the token for having a large amount of unlocked liquidity and a low number of liquidity providers.

**Recommendation:** Review the token's external risk profile and provider concentration before interacting.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $333K (DexScreener, all pools). 24h trading volume $48.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $333K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`B44Upt...xsM8`](https://solscan.io/account/B44UptqVg1fnkc7eUJy1TmbyGxUnsgmDg1dciMsMxsM8) |
| **Network** | Solana |
| **Price** | $0.00001624 |
| **24h Volume** | $48.46M |
| **Liquidity** | $333.4K |
| **Volume / Liquidity** | 145.3× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 23115 buys / 20960 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/bljvc4njycyptuv68fghnxn47lolah5e2rwyiyxyfzzu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/allox-sol-939e)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

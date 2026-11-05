---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 29
status: low
date: 2026-11-05
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-ebb6)

---

## Audit Summary

The PREDICT token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the protocol exhibits high risk due to extreme wash-trading signals and the lack of locked liquidity, which remains fully withdrawable by anonymous holders. Holder concentration data was unavailable from the provided sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows for potential sudden removal of the trading pool. Monitor the liquidity pool's status on-chain to ensure that the pool creator does not withdraw the underlying assets.

Verify that the mint and freeze authorities remain revoked by checking the mint account state periodically. Given the high volume-to-liquidity ratio, avoid relying on 24-hour volume as a metric for market health or liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 5/10 | Medium | The token exhibits a volume/liquidity ratio of 92.64, significantly exceeding the 20x threshold for wash-trading (7.4 Economic). Liquidity is $187,906, but 100% of the pool remains unlocked and… |
| **Upgrades** | 8/10 | Low | Metadata is immutable, preventing changes to the token's branding or identity (7.7 Upgrades). The token program configuration is fixed, as no mutable extensions were enabled at initialization. There… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0% of the pool's liquidity is burned or locked, meaning the total liquidity is withdrawable by the anonymous pool creator.

**Recommendation:** Lock or burn the liquidity provider tokens to prevent the pool from being drained.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 92.64, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution; high volume relative to liquidity is often used to create a false impression of market activity.


### `M-01` — Third-Party Risk Registry Flag  *(Severity: Medium · Status: Unresolved)*

Third-party registries have flagged the token for having a large amount of unlocked liquidity and a low number of liquidity providers.

**Recommendation:** Review the liquidity provider distribution and consider the risks associated with low-provider pools.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $183K (DexScreener, all pools). 24h trading volume $16.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $183K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2dZz37...ET2f`](https://solscan.io/account/2dZz37f1bpm2iv4wxfpLeBtEikghUEc2b8GTnB4DET2f) |
| **Network** | Solana |
| **Price** | $0.00000692 |
| **24h Volume** | $16.36M |
| **Liquidity** | $183.3K |
| **Volume / Liquidity** | 89.3× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15282 buys / 13804 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/frsrupvvuf4bseqazdvrcnmvwywhzr2s8cknmn5uznx7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-ebb6)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 29
status: low
date: 2026-11-03
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 29/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-f6b0)

---

## Audit Summary

The PREDICT token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. However, the token exhibits high-risk economic indicators, specifically a high volume-to-liquidity ratio suggesting potential wash trading and a lack of locked liquidity. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and the high volume-to-liquidity ratio. Monitor the pool's liquidity levels on-chain to ensure the creator does not withdraw the remaining funds.

Verify the absence of minting capabilities by checking the mint account's authority fields on a block explorer. Given the high volume, ensure that price data is sourced from multiple reliable DEX aggregators to avoid being misled by potential wash trading.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard SPL Token program (7.1 Architecture). Security is bolstered by the revocation of both mint and freeze authorities (7.3 Access Control). No Token-2022 extensions… |
| **Governance / Economics** | 5/10 | Medium | Liquidity is currently $162,517 with 0% locked or burned (7.4 Economic). The volume-to-liquidity ratio of 332.38 significantly exceeds the 20x threshold, indicating potential wash trading (7.6… |
| **Upgrades** | 8/10 | Low | The mint is immutable regarding its authority structure (7.7 Upgrades). Metadata is immutable, preventing post-launch branding changes (7.8 Operations). No upgradeable extensions are present. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 332.38, which is significantly higher than the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution when relying on volume metrics for liquidity assessment.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity provider can withdraw the funds at any time.

**Recommendation:** Monitor the liquidity pool for sudden withdrawals.


### `M-01` — Large Amount of LP Unlocked  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry flags the token for having a large amount of unlocked liquidity, increasing the risk of a liquidity rug pull.

**Recommendation:** Treat the pool as removable until liquidity is locked or burned.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $193K (DexScreener, all pools). 24h trading volume $50.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $193K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`G5SiJa...Scrm`](https://solscan.io/account/G5SiJaFwUn75gK6kjj2v57LKDpr3ZmvK5vcf8c82Scrm) |
| **Network** | Solana |
| **Price** | $0.00001451 |
| **24h Volume** | $50.70M |
| **Liquidity** | $193.2K |
| **Volume / Liquidity** | 262.4× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 46444 buys / 42452 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/chwfqvlokivak6xvzcrufjgqbwvfsrntejbnvpcjors)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-f6b0)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

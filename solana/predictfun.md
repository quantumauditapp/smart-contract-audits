---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 27
status: low
date: 2026-10-29
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol)

---

## Audit Summary

The PREDICT token mint has successfully revoked both mint and freeze authorities, mitigating risks of supply inflation and account freezing. However, the protocol exhibits high economic risk due to a high volume-to-liquidity ratio suggesting potential wash trading and the absence of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the liquidity pool for sudden withdrawals, as the lack of locked liquidity allows the creator to remove the pool at any time. Given the high volume-to-liquidity ratio, exercise caution regarding the authenticity of trading activity.

Verify the current liquidity status on-chain before executing large trades. Avoid relying on volume metrics as a primary indicator of market health for this asset.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is inherent to the… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.6 External signals indicate significant risk. The volume-to-liquidity ratio of 71.57 exceeds the 20 threshold, signaling potential wash trading. 7.5 Governance is impacted by the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint as it does not utilize a proxy pattern. Metadata is immutable, preventing post-launch branding changes. No further upgrade paths exist for the… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $201,593. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 71.57x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution when interpreting volume metrics.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked; the rest can be withdrawn by whoever holds the LP tokens.

**Recommendation:** Watch the liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $197K (DexScreener, all pools). 24h trading volume $13.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $197K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Arawud...v4aN`](https://solscan.io/account/ArawudEneA7TsKkc6GTrksSNyCzYqy4Gq1bPNhZ7v4aN) |
| **Network** | Solana |
| **Price** | $0.00000829 |
| **24h Volume** | $13.86M |
| **Liquidity** | $197.1K |
| **Volume / Liquidity** | 70.4× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26508 buys / 24180 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9i64mve7junemnt94qwt2exdtkhzhfadenuszzbhnuwv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

---
token: predict.fun
ticker: PREDICT
network: solana
risk_score: 27
status: low
date: 2026-11-02
---

# predict.fun (PREDICT) — Smart Contract Security Analysis | Solana

> **Risk Score: 27/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/predictfun-sol-72e2)

---

## Audit Summary

The PREDICT token mint has successfully revoked both mint and freeze authorities, mitigating risks of supply inflation and account freezing. However, the token exhibits high-risk economic indicators, including a volume-to-liquidity ratio suggesting wash trading and a lack of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity and suspicious trading volume. Monitor the pool for sudden liquidity removal, as the current configuration allows the pool creator to withdraw all funds at any time.

Verify the current liquidity status on-chain before executing any trades. Do not rely on high 24-hour volume as an indicator of organic market demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for non-extension mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis reveals a volume-to-liquidity ratio of 263.18, which is significantly above the 20x threshold, indicating potential wash trading. 7.6 External data shows 0% of liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable to this SPL token mint. Metadata is immutable, and no extensions are configured that allow for balance or transfer modifications. |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $158,753. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the fee in any swap calculation.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 263.18x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume may not reflect genuine market interest.


### `M-01` — Pool Liquidity Not Locked  *(Severity: Medium · Status: Unresolved)*

0% of the pool's liquidity is burned or locked; the rest can be withdrawn by whoever holds the LP tokens.

**Recommendation:** Watch the pool creator's wallet liquidity position; treat the pool as removable until the liquidity is burned or locked.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $151K (DexScreener, all pools). 24h trading volume $39.7M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $151K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5UZP7X...uxN8`](https://solscan.io/account/5UZP7XpYD26AU4fPeE3PLd9cQZCfkjxXv8frvn9iuxN8) |
| **Network** | Solana |
| **Price** | $0.00001154 |
| **24h Volume** | $39.75M |
| **Liquidity** | $151.5K |
| **Volume / Liquidity** | 262.4× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35790 buys / 32701 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3kzbpfg3ofxry2sbdkugaqv3m7hww5zjzt87gauqzqtl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/predictfun-sol-72e2)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-02*

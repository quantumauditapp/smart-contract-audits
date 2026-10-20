---
token: FABLES
ticker: FABLES
network: solana
risk_score: 26
status: low
date: 2026-10-20
---

# FABLES (FABLES) — Smart Contract Security Analysis | Solana

> **Risk Score: 26/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fables-sol)

---

## Audit Summary

The FABLES token mint demonstrates strong security regarding administrative control, as both mint and freeze authorities are revoked. However, the economic structure presents significant risks, specifically regarding liquidity management and suspicious trading activity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows the pool creator to withdraw all funds at any time. Monitor the liquidity pool for sudden removals and avoid trading if the volume-to-liquidity ratio remains at anomalous levels.

Verify the current liquidity status via block explorers before executing trades. Do not rely on the token's branding as metadata is immutable, but the underlying economic risk remains high due to the potential for liquidity withdrawal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, with both mint and freeze authorities… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate high risk. The volume/liquidity ratio of 122.33 suggests potential wash trading. 7.6 External data confirms 0% of liquidity is locked, meaning the… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token. Metadata is immutable, preventing post-launch branding changes. No further upgrade paths exist for this mint. |

## Security Findings

_🟠 2 High · ⚪ 5 Informational_

### `H-01` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the pool creator can withdraw all liquidity at any time.

**Recommendation:** The liquidity provider should burn or lock the LP tokens to ensure the pool's stability.


### `H-02` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 122.33, which is significantly above the 20x threshold, indicating potential artificial trade volume.

**Recommendation:** Exercise caution as high volume-to-liquidity ratios often indicate manipulated market activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $364K (DexScreener, all pools). 24h trading volume $43.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $364K of DEX liquidity across 2 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DS8Z3w...ezhQ`](https://solscan.io/account/DS8Z3wJyYky4H7oCQguRsethxhDAwoowXA5F3HFbezhQ) |
| **Network** | Solana |
| **Price** | $0.00001825 |
| **24h Volume** | $43.94M |
| **Liquidity** | $364.2K |
| **Volume / Liquidity** | 120.6× |
| **Token Age** | 7h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 21826 buys / 19620 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gf7narhaoceqqt3tp21c2kcbfmipp3woxcotknlasife)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fables-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

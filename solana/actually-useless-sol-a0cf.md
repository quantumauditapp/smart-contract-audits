---
token: Actually Useless
ticker: AU
network: solana
risk_score: 30
status: low
date: 2026-10-22
---

# Actually Useless (AU) — Smart Contract Security Analysis | Solana

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/actually-useless-sol-a0cf)

---

## Audit Summary

The token mint and freeze authorities are successfully revoked, providing a secure foundation for supply. However, the protocol exhibits high economic risk due to extreme wash-trading signals and the lack of locked liquidity. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should exercise extreme caution due to the lack of locked liquidity, which allows for the potential removal of the entire pool. Monitor the liquidity pool for sudden withdrawals before interacting with the token.

Verify the current liquidity status via on-chain explorers to ensure the pool has not been drained. Given the high wash-trading volume, do not rely on DEX-reported volume as an indicator of genuine market interest or liquidity depth.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust as both mint and freeze authorities are… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic and 7.5 Governance metrics indicate significant risk. The volume/liquidity ratio of 57.97 suggests heavy wash-trading. 7.6 External signals confirm that 100% of pool liquidity is… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as this is a standard SPL token mint. Metadata is immutable, preventing branding changes post-launch. No administrative backdoors or upgrade paths exist for the token… |

## Security Findings

_🟠 2 High · 🟡 1 Medium · ⚪ 5 Informational_

### `H-01` — High Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 57.97, which significantly exceeds the 20x threshold, indicating artificial trade volume.

**Recommendation:** Do not use volume as a metric for market health; perform independent analysis of trade frequency.


### `H-02` — Pool Liquidity Not Locked  *(Severity: High · Status: Unresolved)*

0.0% of the pool's liquidity is burned or locked, meaning the liquidity is fully withdrawable by the anonymous pool creator.

**Recommendation:** Avoid providing liquidity or trading in pools where the creator retains full withdrawal rights.


### `M-01` — Low Number of LP Providers  *(Severity: Medium · Status: Unresolved)*

Third-party registry data indicates a low number of liquidity providers, increasing the risk of price manipulation.

**Recommendation:** Monitor the pool for sudden changes in liquidity depth.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 0.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $212K (DexScreener, all pools). 24h trading volume $12.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun (PumpSwap), a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $212K of DEX liquidity across 1 pools. Launch: launched on pump.fun (PumpSwap), under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8trzyT...Yinn`](https://solscan.io/account/8trzyTDGJ4bHsixAY7YzzASk1L64fkky8gLBrtxkYinn) |
| **Network** | Solana |
| **Price** | $0.0001398 |
| **24h Volume** | $11.98M |
| **Liquidity** | $211.9K |
| **Volume / Liquidity** | 56.5× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16409 buys / 10382 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3kmj1chkoqo37juq4b5e4vrn6dzvepqupuwnvayjybnq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/actually-useless-sol-a0cf)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*

---
token: Baby Uni
ticker: BABYUNI
network: solana
risk_score: 17
status: low
date: 2026-11-01
---

# Baby Uni (BABYUNI) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/baby-uni-sol)

---

## Audit Summary

Baby Uni (BABYUNI) is a Token-2022 asset with fully revoked mint and freeze authorities, providing strong protection against supply inflation and account freezing. However, the token exhibits high economic risk due to very low liquidity and a high volume-to-liquidity ratio. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise extreme caution due to the low liquidity environment, which may prevent efficient exit from positions. Monitor DEX market data for significant changes in liquidity depth before executing large trades.

Verify that no new authorities have been granted by checking the mint account state periodically. Given the lack of holder concentration data, assume high volatility and potential for price manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program, ensuring modern extension compatibility. 7.1 Architecture and 7.2 Code Security are standard for this program type. 7.3 Access Control is robust, as… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are elevated due to low liquidity ($5,709) and a high volume-to-liquidity ratio of 15.33. While 100% of pool liquidity is burned, preventing creator withdrawal… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades and 7.8 Operations are secure as metadata is immutable and balance-mutating authorities are disabled. The token configuration is static, preventing post-launch changes to branding or… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `H-01` — Very Low Liquidity  *(Severity: High · Status: Unresolved)*

Total DEX liquidity is $5,709. Slippage will be severe; large positions cannot be exited without significant loss.

**Recommendation:** Account for the liquidity depth in any swap calculation and avoid large market orders.


### `M-01` — High Volume/Liquidity Ratio  *(Severity: Medium · Status: Unresolved)*

The 24-hour volume to liquidity ratio is 15.33, which is a pattern associated with artificially inflated trade volume.

**Recommendation:** Exercise caution as high volume relative to liquidity may indicate non-organic trading activity.


### `L-01` — Low Number of LP Providers  *(Severity: Low · Status: Unresolved)*

Third-party registry signals indicate a low number of liquidity providers, increasing the risk of price volatility.

**Recommendation:** Monitor the liquidity pool for provider diversity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $82K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 4 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EaYd9u...pump`](https://solscan.io/account/EaYd9uBdkMpgDB6JAu2igUAXKmNrJGB1hiL22PeMpump) |
| **Network** | Solana |
| **Price** | $0.00004002 |
| **24h Volume** | $81.4K |
| **Liquidity** | $11.9K |
| **Volume / Liquidity** | 6.8× |
| **Token Age** | 0h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 927 buys / 935 sells |

## Security Flags (4/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/7tenn5utfmpjefca3mo27admr4gbuyn5f4sq7c1szrry)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/baby-uni-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*

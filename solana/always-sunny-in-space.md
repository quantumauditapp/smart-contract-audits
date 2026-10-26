---
token: Always Sunny in Space
ticker: ASS
network: solana
risk_score: 23
status: low
date: 2026-10-26
---

# Always Sunny in Space (ASS) — Smart Contract Security Analysis | Solana

> **Risk Score: 23/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/always-sunny-in-space-sol)

---

## Audit Summary

The Always Sunny in Space (ASS) token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. No adverse flags were reported by third-party registries.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs given the concentration levels. Due to the high volume-to-liquidity ratio, exercise caution regarding price discovery and slippage when executing large trades.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.8 Operations are secure as… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic analysis shows 15.95% concentration among the top 10 holders. 7.6 External market data indicates $16,299 in liquidity, which is fully burned, preventing rug pulls via liquidity… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as SPL mints do not use proxy patterns. The token configuration is immutable, with metadata and extension parameters locked. No further changes to the token's core… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 32.95, which exceeds the 20 threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Perform independent verification of trade history on-chain to identify if volume is organic before committing capital.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.6% of supply. Of that, 17.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 15.9% in wallets, 0.0% in other contracts. 993 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

993 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $610K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 21 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3Vkkvo...pump`](https://solscan.io/account/3Vkkvo8jxHy6B4pxRLLV3F9EBYRS1NE8mKCxhi1Mpump) |
| **Network** | Solana |
| **Price** | $0.0000486 |
| **24h Volume** | $528.9K |
| **Liquidity** | $18.4K |
| **Volume / Liquidity** | 28.8× |
| **Token Age** | 4h |
| **Top-10 Holders** | 33.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8376 buys / 5832 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7ttrywfgute5mqf1vfk26odiwyejqcsw12xlgusuwyrw)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/always-sunny-in-space-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

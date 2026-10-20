---
token: 剣を持った犬
ticker: MONAKA
network: solana
risk_score: 40
status: medium
date: 2026-10-20
---

# 剣を持った犬 (MONAKA) — Smart Contract Security Analysis | Solana

> **Risk Score: 40/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monaka-sol)

---

## Audit Summary

The token 剣を持った犬 (Monaka) utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully burned, eliminating withdrawal risks, though the high volume-to-liquidity ratio suggests potential wash trading. Holder concentration data is unavailable, and third-party registry data shows no adverse flags.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which may indicate artificial trading activity rather than organic demand. Given the low liquidity, large trades will experience significant slippage.

Verify current market conditions on-chain before executing swaps. Monitor the token's price stability and volume trends to distinguish between organic interest and potential wash trading patterns.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 5/10 | Medium | Total liquidity is $9,279, which is fully burned and inaccessible to any creator (7.4 Economic). The 24-hour volume of $525,825 relative to liquidity indicates a ratio of 56.67, suggesting… |
| **Upgrades** | 8/10 | Low | The mint is immutable regarding authority changes as both are revoked (7.7 Upgrades). Metadata is non-mutable, preventing branding changes post-launch. No upgrade paths exist for the token program or… |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume to liquidity ratio is 56.67, exceeding the 20x threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for potential liquidity manipulation and volatility when assessing the token's market health.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $9K (DexScreener, all pools). 24h trading volume $617K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $9K of DEX liquidity across 8 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`8Vb5f7...pump`](https://solscan.io/account/8Vb5f7enGjp2uHuRqh1F5AVoXoXrYVZHwuw2orjepump) |
| **Network** | Solana |
| **Price** | $0.00001349 |
| **24h Volume** | $523.0K |
| **Liquidity** | $8.5K |
| **Volume / Liquidity** | 61.5× |
| **Token Age** | 11h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8105 buys / 6045 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5fs68n3lthuvil6yge1wvf9r9zjn33toagdn25mzhaju)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monaka-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-20*

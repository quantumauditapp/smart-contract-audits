---
token: Wen Lambo
ticker: WENLAMBO
network: solana
risk_score: 42
status: medium
date: 2026-10-30
---

# Wen Lambo (WENLAMBO) — Smart Contract Security Analysis | Solana

> **Risk Score: 42/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wen-lambo-sol)

---

## Audit Summary

The WENLAMBO token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is fully burned, the token exhibits moderate holder concentration and has been flagged by a third-party risk registry for high ownership concentration. All sources, including on-chain registry and DEX market data, were successfully retrieved.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for potential coordinated sell-offs given the 69.95% concentration. While the liquidity is safely burned, the high ownership concentration remains the primary risk factor for market stability.

Verify the current holder distribution periodically via block explorers to ensure no single entity accumulates a controlling stake. Do not rely solely on the lack of administrative authorities as a guarantee against market-driven price volatility.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control). The… |
| **Governance / Economics** | 7/10 | Low | The top 10 holders control 69.95% of the supply, presenting a moderate risk of price volatility (7.4 Economic). Liquidity is $39,459 and is 100% burned, preventing withdrawal by the creator (7.8… |
| **Upgrades** | 8/10 | Low | The token metadata is immutable, and there are no upgradeable extensions (7.7 Upgrades). The mint and freeze authorities are permanently revoked, precluding any administrative changes to the token's… |

## Security Findings

_🟡 1 Medium · ⚪ 6 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 69.95% of the supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for signs of distribution or coordinated selling.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.5% of supply. Of that, 11.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 70.0% in wallets, 0.0% in other contracts. 472 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

472 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $37K (DexScreener, all pools). 24h trading volume $40K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $37K of DEX liquidity across 9 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`C6NniJ...pump`](https://solscan.io/account/C6NniJqUMTMhGGgr1RNyDsUgbLQwrLfrxhm8kG3opump) |
| **Network** | Solana |
| **Price** | $0.0001713 |
| **24h Volume** | $39.6K |
| **Liquidity** | $37.2K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 12h |
| **Top-10 Holders** | 81.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 586 buys / 399 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g5kuewqz8a96kdxa54x7yledm8wjmgxlfiezbpxn11ve)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wen-lambo-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

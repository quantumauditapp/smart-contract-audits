---
token: TDCCP
ticker: TDCCP
network: solana
risk_score: 34
status: low
date: 2026-10-18
---

# TDCCP (TDCCP) — Smart Contract Security Analysis | Solana

> **Risk Score: 34/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tdccp-sol)

---

## Audit Summary

The TDCCP SPL token mint exhibits a medium risk due to significant holder concentration, with the top ten sellable holders controlling 67.41% of the supply. Key authorities like mint and freeze are revoked, indicating a fixed supply and unfreezable accounts. Information regarding the locking status of the pool's liquidity was unavailable.

> **Final Recommendation:** Holders should closely monitor the wallets identified as the top ten holders that can sell, given their significant control over the supply. Any large movements from these addresses could indicate potential sell-offs impacting market price. Verify on-chain that the mint and freeze authorities remain revoked to confirm the fixed supply and unfreezable nature of the token. Seek additional information regarding the locking status of the DEX pool's liquidity to assess the risk of liquidity withdrawal.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The TDCCP token is an SPL token operating under the `spl-token` program. Its mint authority and freeze authority are both revoked, ensuring that no new tokens can be minted and no existing token… |
| **Governance / Economics** | 5/10 | Medium | The economic stability of TDCCP is influenced by a notable holder concentration, with the ten largest holders that can sell controlling 67.41% of the total supply. The token has a liquidity of… |
| **Upgrades** | 8/10 | Low | The TDCCP token mint has a fixed configuration as both the mint authority and freeze authority have been revoked, preventing any further issuance or freezing of tokens. The token's metadata is… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 67.41% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant holder concentration when assessing market stability and potential price volatility.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 68.8% of supply. Of that, 1.4% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 62.2% in wallets, 5.2% in other contracts. 17,816 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as TDCCP (TDCCP), market cap $15M, rank #989. 17,816 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $163K (DexScreener, all pools). 24h trading volume $47K (CoinGecko, all markets, daily snapshot). 24h trading volume $104K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.441 on 2025-09-08; the price is now 94.85% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $163K of DEX liquidity across 30 pools. Launch: 591 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Hg8bKz...mfrD`](https://solscan.io/account/Hg8bKz4mvs8KNj9zew1cEF9tDw1x2GViB4RFZjVEmfrD) |
| **Network** | Solana |
| **Price** | $0.02292 |
| **24h Volume** | $59.2K |
| **Liquidity** | $123.6K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 68.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 698 buys / 509 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fsjhlehhbnscgyrcrwcuupgzn7nzebj79anffsawbboo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tdccp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-18*

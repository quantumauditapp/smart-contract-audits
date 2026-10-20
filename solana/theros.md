---
token: THEROS
ticker: THEROS
network: solana
risk_score: 25
status: low
date: 2026-10-08
---

# THEROS (THEROS) — Smart Contract Security Analysis | Solana

> **Risk Score: 25/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/theros-sol)

---

## Audit Summary

The THEROS SPL token mint audit identified a medium risk due to significant holder concentration, with the top ten sellable holders controlling 69.88% of the supply. Key authorities like mint and freeze are revoked, indicating a fixed supply and unfreezable accounts. Information regarding pool liquidity locking status was unavailable.

> **Final Recommendation:** Holders should monitor the wallets identified as the top ten holders that can sell for any significant movements, as their combined holdings represent a substantial portion of the supply. While mint and freeze authorities are revoked, providing supply stability, the lack of information on pool liquidity locking means this aspect should be verified independently if possible.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The THEROS token is an SPL token operating on the Solana blockchain, utilizing the `spl-token` program. Its mint authority is revoked, ensuring no new tokens can be created, and the total supply is… |
| **Governance / Economics** | 6/10 | Medium | The token exhibits a medium level of holder concentration, with the ten largest holders that can sell controlling 69.88% of the total supply. This concentration could lead to price volatility from… |
| **Upgrades** | 8/10 | Low | The THEROS token mint has both its mint and freeze authorities permanently revoked, preventing any further issuance or freezing of tokens. The token's metadata is immutable, meaning its name, symbol… |

## Security Findings

_🟡 1 Medium · ⚪ 4 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 69.88% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Be aware that a significant portion of the token supply is concentrated among a few holders. Monitor these large holders for any signs of coordinated selling activity, which could impact market price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.0% of supply. Of that, 11.2% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 17.3% in wallets, 52.6% in other contracts. 53,844 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Theros (THEROS), market cap $22M, rank #823. 53,844 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.7M (DexScreener, all pools). 24h trading volume $21K (CoinGecko, all markets, daily snapshot). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.7M of DEX liquidity across 7 pools. Launch: 317 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`2UfBjN...cPa2`](https://solscan.io/account/2UfBjNeDwzZsoUnr3hNKF4vkzAgiGmBNYCAxLq72cPa2) |
| **Network** | Solana |
| **Price** | $0.2771 |
| **24h Volume** | $31.3K |
| **Liquidity** | $2.74M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 10mo |
| **Top-10 Holders** | 81.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 493 buys / 277 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/behtrqrfgfamdp82vbj161ybd8xyedb422hwaf1gfm3u)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/theros-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-08*

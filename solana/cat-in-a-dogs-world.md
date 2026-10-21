---
token: cat in a dogs world
ticker: MEW
network: solana
risk_score: 28
status: low
date: 2026-10-21
---

# cat in a dogs world (MEW) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cat-in-a-dogs-world-sol)

---

## Audit Summary

The token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While holder concentration is notable, the liquidity is substantial and the majority of LP tokens are burned. Third-party registry data indicates high concentration risks, but no critical technical vulnerabilities were identified.

> **Final Recommendation:** Investors should monitor the top 10 holder wallets for significant movement, as the current concentration could lead to price volatility. No further technical action is required as the mint and freeze authorities are correctly revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed via the standard spl-token program. 7.1 Architecture and 7.3 Access Control are robust as both mint and freeze authorities are revoked. 7.2 Code Security is maintained by using… |
| **Governance / Economics** | 5/10 | Medium | 7.4 Economic analysis shows a top 10 holder concentration of 64.70%, which triggers a medium risk rating. 7.6 External market data confirms high liquidity of ~$9.8M with a healthy volume/liquidity… |
| **Upgrades** | 8/10 | Low | 7.7 Upgrades are not applicable as SPL token mints are immutable once initialized. Metadata is immutable, and there are no upgradeable hooks or fee structures. The token state is fixed and… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 64.70% of the total supply. Coordinated sell-offs by these entities could significantly impact the market price.

**Recommendation:** Monitor top holder wallet activity for potential large-scale sell pressure.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 76.4% of supply. Of that, 11.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 64.7% in wallets, 0.0% in other contracts. 156,736 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as cat in a dogs world (MEW), market cap $37M, rank #561. 156,736 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10.1M (DexScreener, all pools). 24h trading volume $1.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $4.0M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0129 on 2024-11-17; the price is now 96.791% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: IP Meme. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10.1M of DEX liquidity across 30 pools. Launch: 938 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`MEW1gQ...cPP5`](https://solscan.io/account/MEW1gQWJ3nEXg2qgERiKu7FAFj79PHvQVREQUzScPP5) |
| **Network** | Solana |
| **Price** | $0.0005307 |
| **24h Volume** | $4.05M |
| **Liquidity** | $10.07M |
| **Volume / Liquidity** | 0.4× |
| **Token Age** | 2y |
| **Top-10 Holders** | 76.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4609 buys / 4845 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/879f697iudjgmevrkrcnw21fcxiaeljk1ffsw2atebce)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cat-in-a-dogs-world-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

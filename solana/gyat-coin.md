---
token: Gyat Coin
ticker: GYAT
network: solana
risk_score: 17
status: low
date: 2026-10-24
---

# Gyat Coin (GYAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 17/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gyat-coin-sol)

---

## Audit Summary

Gyat Coin is a standard SPL token with both mint and freeze authorities successfully revoked. The token exhibits moderate holder concentration and sufficient liquidity, with no adverse flags from third-party registries. All requested data sources were successfully retrieved.

> **Final Recommendation:** Investors should monitor the top holder wallets for potential coordinated sell-offs given the 58.76% concentration. As the mint and freeze authorities are revoked, the token supply is fixed and cannot be manipulated by the original deployer.

Verify the current holder distribution periodically via block explorers to ensure concentration does not increase. No further technical action is required as the core security parameters are optimally configured.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). The mint state is… |
| **Governance / Economics** | 9/10 | Low | The top 10 holders control 58.76% of the supply, presenting a moderate concentration risk (7.4 Economic). Liquidity is stable at $135,196 with a healthy volume-to-liquidity ratio of 3.14 (7.4… |
| **Upgrades** | 10/10 | Low | The token mint is immutable, as both mint and freeze authorities are revoked (7.7 Upgrades). Metadata is non-mutable, preventing branding changes (7.2 Code Security). There are no upgradeable… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell control 58.76% of the total supply. This concentration increases the risk of price volatility if these holders coordinate a sell-off.

**Recommendation:** Monitor the activity of the top 10 wallets to identify potential liquidity events or dumping patterns.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $130K (DexScreener, all pools). 24h trading volume $12K (CoinGecko, all markets, daily snapshot). 24h trading volume $381K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.026 on 2025-02-03; the price is now 99.3532% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 58.8% of supply. What remains: 27.3% in wallets, 31.4% in other contracts. 8,406 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GYAT Coin (GYAT), rank #4996. 8,406 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $130K of DEX liquidity across 4 pools. Launch: launched on pump.fun, 630 days of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EfgEGG...pump`](https://solscan.io/account/EfgEGG9PxLhyk1wqtqgGnwgfVC7JYic3vC9BCWLvpump) |
| **Network** | Solana |
| **Price** | $0.0003931 |
| **24h Volume** | $381.0K |
| **Liquidity** | $130.0K |
| **Volume / Liquidity** | 2.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 58.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2826 buys / 1901 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dgqd4rmbkf3upcy7guklmyosap4hpzmuwsvsuzatjlky)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gyat-coin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

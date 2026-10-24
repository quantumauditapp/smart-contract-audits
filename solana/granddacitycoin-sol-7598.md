---
token: GrandDacityCoin
ticker: GDC
network: solana
risk_score: 15
status: low
date: 2026-10-24
---

# GrandDacityCoin (GDC) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/granddacitycoin-sol-7598)

---

## Audit Summary

GrandDacityCoin (GDC) is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder distribution data was unavailable from the RPC source.

> **Final Recommendation:** Investors should monitor the token's trading volume to determine if the high activity is organic or artificial. Given the lack of holder concentration data, users should exercise caution regarding potential whale activity that may not be visible in current market metrics.

Verify the current supply and authority status directly via a block explorer to ensure no unexpected changes have occurred. Do not rely solely on DEX-reported volume when assessing the token's market health.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the spl-token-2022 program. 7.1 Architecture is standard for SPL tokens. 7.3 Access Control is robust as both mint and freeze authorities are revoked. 7.2 Code Security is… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic stability is supported by 100% of liquidity being burned, preventing rug pulls. However, 7.6 External market data indicates a volume/liquidity ratio of 20.48, which is a high signal for… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable as the mint is immutable. 7.8 Operations are secure due to the permanent revocation of metadata and balance-mutating authorities. The token configuration is fixed and… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume/liquidity ratio is 20.48, exceeding the 20 threshold, which is a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Perform independent analysis of trade history to verify the authenticity of volume before committing capital.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $67K (DexScreener, all pools). 24h trading volume $1.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $67K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`4ipcoJ...pump`](https://solscan.io/account/4ipcoJ37nXNXs66SR9MVYTz6vwUdqsXYfLD4vYE6pump) |
| **Network** | Solana |
| **Price** | $0.0005899 |
| **24h Volume** | $1.50M |
| **Liquidity** | $66.9K |
| **Volume / Liquidity** | 22.4× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 28282 buys / 6749 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/au5eqdjhkeho4e7ub78p2dbdjurebskeyr9dmphwgbrh)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/granddacitycoin-sol-7598)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

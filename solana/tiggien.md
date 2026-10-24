---
token: Tiggien
ticker: TIGGIEN
network: solana
risk_score: 28
status: low
date: 2026-10-24
---

# Tiggien (TIGGIEN) — Smart Contract Security Analysis | Solana

> **Risk Score: 28/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tiggien-sol)

---

## Audit Summary

The Tiggien token is a Token-2022 asset with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. All third-party registry data was available and no adverse flags were reported.

> **Final Recommendation:** Investors should exercise caution regarding the high volume-to-liquidity ratio, which often indicates artificial trading activity rather than organic demand. Monitor the top holder wallets for potential coordinated sell-offs, as they control a significant portion of the circulating supply.

Verify the current supply and holder distribution via a block explorer before executing large trades. Ensure that your trading strategy accounts for the high slippage inherent in low-liquidity environments, despite the safety provided by the burned liquidity pool.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Security is bolstered by the revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or balance-mutating… |
| **Governance / Economics** | 7/10 | Low | The top 10 holders control 20.62% of the supply (7.4 Economic). Liquidity is $18,370 and is 100% burned, preventing rug pulls via liquidity withdrawal (7.5 Governance). However, the… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable (7.7 Upgrades). There are no upgradeable components or proxy-like structures present (7.8 Operations). The configuration is finalized and cannot be altered by the… |

## Security Findings

_🟠 1 High · ⚪ 6 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 53.08, which exceeds the 20x threshold, indicating a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Exercise extreme caution; high volume in low-liquidity pools can be misleading and may not represent genuine market interest.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 55.2% of supply. Of that, 31.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 23.5% in wallets, 0.0% in other contracts. 179 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

179 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $18K (DexScreener, all pools). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $18K of DEX liquidity across 6 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6NQ6R8...pump`](https://solscan.io/account/6NQ6R8ndUED8s1MN6zawrhwoekF6Ep78656W9cwTpump) |
| **Network** | Solana |
| **Price** | $0.00004306 |
| **24h Volume** | $972.3K |
| **Liquidity** | $17.1K |
| **Volume / Liquidity** | 57.0× |
| **Token Age** | 22h |
| **Top-10 Holders** | 55.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 12725 buys / 9365 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dyrfvuaixnjagwxacmkgxwvarcnrvqq3ewgpeahcv9fv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tiggien-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

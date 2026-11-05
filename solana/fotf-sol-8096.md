---
token: FOTF
ticker: FOTF
network: solana
risk_score: 20
status: low
date: 2026-11-05
---

# FOTF (FOTF) — Smart Contract Security Analysis | Solana

> **Risk Score: 20/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/fotf-sol-8096)

---

## Audit Summary

The FOTF token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, the token exhibits a high volume-to-liquidity ratio, suggesting potential wash trading. Holder concentration data is currently unavailable from on-chain sources.

> **Final Recommendation:** Investors should exercise caution due to the high volume-to-liquidity ratio, which is a common indicator of artificial trading volume. Monitor the token's market activity on block explorers to verify if the high volume translates into genuine organic interest.

Verify the current holder distribution once on-chain data becomes available to ensure that supply is not heavily concentrated among a few wallets. Do not rely solely on the burned liquidity status as a guarantee of price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or custom… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully burned, ensuring the pool creator cannot withdraw funds (7.4 Economic). However, the volume-to-liquidity ratio of 74.81 indicates significant wash trading activity (7.6 External).… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing future branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token-2022 standard. The mint and freeze… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 74.81, which significantly exceeds the 20x threshold, indicating potential wash trading.

**Recommendation:** Monitor market activity for organic volume and avoid trading during periods of extreme volatility.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $16K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $16K of DEX liquidity across 3 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`AJQ9Xj...pump`](https://solscan.io/account/AJQ9XjcRA9NBSvvxkCcifh2kuzvEunbVhzpjqgxpump) |
| **Network** | Solana |
| **Price** | $0.00004391 |
| **24h Volume** | $1.17M |
| **Liquidity** | $15.6K |
| **Volume / Liquidity** | 74.8× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 35199 buys / 1348 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/crgikcjrmfljlwrbej6kt6bwwevtpudnih9eyybfit6m)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/fotf-sol-8096)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-05*

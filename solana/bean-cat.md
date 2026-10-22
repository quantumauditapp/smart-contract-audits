---
token: bean cat
ticker: BEANCAT
network: solana
risk_score: 16
status: low
date: 2026-10-22
---

# bean cat (BEANCAT) — Smart Contract Security Analysis | Solana

> **Risk Score: 16/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bean-cat-sol)

---

## Audit Summary

The bean cat (beancat) token is a standard SPL Token-2022 implementation with both mint and freeze authorities successfully revoked. While the liquidity is fully burned, third-party registry data indicates potential risks regarding holder concentration and low liquidity provider diversity. Holder distribution data was unavailable for this analysis.

> **Final Recommendation:** Investors should monitor the token's holder distribution via block explorers to verify if concentration levels pose a risk to price stability. Given the low liquidity provider diversity, exercise caution when executing large market orders to avoid excessive slippage.

Verify the current supply and authority status directly on-chain using a Solana explorer to ensure no unexpected changes have occurred since this audit. Do not rely solely on third-party registry flags; perform independent due diligence on the token's market activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the SPL Token-2022 program (7.1 Architecture). Access control is secure as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or custom extensions… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully secured with 100% of LP tokens burned, preventing creator withdrawal (7.4 Economic). Trading volume is healthy relative to liquidity, with a ratio of 1.74 (7.6 External). However… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable extensions or balance-mutating authorities present (7.8 Operations). The token state… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — Low Liquidity Provider Diversity  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate a low number of liquidity providers, which may lead to increased price volatility.

**Recommendation:** Monitor the liquidity pool for signs of provider exit or concentration.


### `L-01` — Potential Single Holder Concentration  *(Severity: Low · Status: Unresolved)*

Third-party risk registry flags suggest potential single-holder ownership, which could lead to significant sell pressure.

**Recommendation:** Review top holder accounts on-chain to assess the risk of a coordinated sell-off.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $19K (DexScreener, all pools). 24h trading volume $31K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: meme vocabulary in name/ticker (cat); launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $19K of DEX liquidity across 2 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`BvzwP1...pump`](https://solscan.io/account/BvzwP111BGSRHWepDRZqe5Ug875iqp7SYLbEb3Nvpump) |
| **Network** | Solana |
| **Price** | $0.00004851 |
| **24h Volume** | $31.0K |
| **Liquidity** | $18.8K |
| **Volume / Liquidity** | 1.7× |
| **Token Age** | 22h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 288 buys / 194 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/8r13ybabnuahacy6qwu3qpver3mb9xykcpkv89izcsoo)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bean-cat-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-22*

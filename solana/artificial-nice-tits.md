---
token: Artificial Nice Tits
ticker: ANT
network: solana
risk_score: 2
status: low
date: 2026-10-26
---

# Artificial Nice Tits (ANT) — Smart Contract Security Analysis | Solana

> **Risk Score: 2/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/artificial-nice-tits-sol)

---

## Audit Summary

The ANT token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured through a 100% burn of LP tokens, mitigating withdrawal risks. Holder distribution data was unavailable, and a third-party registry flagged high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's market activity given the third-party registry flag regarding holder correlation. Since holder distribution data is currently unavailable, users should exercise caution regarding potential price volatility caused by concentrated supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $463,950 with 100% of LP tokens burned, ensuring permanent availability (7.4 Economic). Trading volume is healthy relative to liquidity (7.6 External). Holder concentration… |
| **Upgrades** | 10/10 | Low | The mint is immutable regarding metadata and authority settings (7.7 Upgrades). No upgrade paths exist for the token program or its extensions (7.8 Operations). |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation Flag  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related entities.

**Recommendation:** Monitor on-chain movements of large wallets and exercise caution regarding potential market manipulation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $463K (DexScreener, all pools). 24h trading volume $253K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $463K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`MuS7RF...pump`](https://solscan.io/account/MuS7RFYZQpChxAewvy7j5zwaMY9yTyr713rSVfKpump) |
| **Network** | Solana |
| **Price** | $0.03039 |
| **24h Volume** | $252.8K |
| **Liquidity** | $462.5K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 8h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 26161 buys / 449 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gr1p4dssqmvs5g4gxlsfnezx1hmiuiibfspbcb47vjas)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/artificial-nice-tits-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

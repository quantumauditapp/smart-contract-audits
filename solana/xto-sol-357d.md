---
token: XTO
ticker: XTO
network: solana
risk_score: 1
status: low
date: 2026-10-21
---

# XTO (XTO) — Smart Contract Security Analysis | Solana

> **Risk Score: 1/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/xto-sol-357d)

---

## Audit Summary

The XTO token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. Liquidity is fully secured via a 100% burn of LP tokens, mitigating withdrawal risks. However, third-party registry data indicates high holder correlation and single-entity ownership, which may impact market stability.

> **Final Recommendation:** Investors should monitor the token's holder distribution on-chain to assess the impact of the flagged high holder correlation. Given the immutable nature of the mint, no further administrative actions are required by the issuer.

Users should verify the current holder concentration using block explorers to ensure that the single-entity ownership identified by third-party registries does not pose a systemic risk to their specific investment strategy.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring supply immutability and preventing account freezing (7.3 Access Control). No… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $1.17M with 100% of LP tokens burned, preventing rug-pulls via liquidity withdrawal (7.4 Economic). Trading volume is healthy relative to liquidity (7.8 Operations).… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, and no upgradeable extensions are enabled (7.7 Upgrades). The revocation of mint and freeze authorities provides a permanent state for the token's operational… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry data indicates high holder correlation and single-entity ownership, which may lead to centralized control over market price movements.

**Recommendation:** Monitor on-chain holder distribution and trading activity for signs of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $706K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GdXeF5...pump`](https://solscan.io/account/GdXeF5bdJkHSJESkyGHnet6YVXc2s9qNfwr4LYAxpump) |
| **Network** | Solana |
| **Price** | $0.1839 |
| **24h Volume** | $705.7K |
| **Liquidity** | $1.17M |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 14h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 22644 buys / 670 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/6iq2k8mfggm6jbdaxzxbjjebjfepjexxdybzysm6o37a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/xto-sol-357d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

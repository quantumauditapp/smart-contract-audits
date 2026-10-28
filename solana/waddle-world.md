---
token: Waddle World
ticker: WADDLE
network: solana
risk_score: 22
status: low
date: 2026-10-28
---

# Waddle World (WADDLE) — Smart Contract Security Analysis | Solana

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/waddle-world-sol)

---

## Audit Summary

Waddle World utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. The liquidity pool is fully burned, eliminating withdrawal risks for the creator. However, the high volume-to-liquidity ratio suggests potential wash trading, and holder distribution data was unavailable for analysis.

> **Final Recommendation:** Investors should monitor the token's trading activity, as the high volume-to-liquidity ratio is a strong indicator of artificial market inflation. Since holder distribution data is unavailable, users should exercise caution regarding potential whale concentration.

Verify the current supply and authority status directly via a block explorer to confirm that the mint and freeze authorities remain null. Do not rely on third-party volume metrics as a proxy for organic demand.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the Token-2022 program (7.1 Architecture). Security is bolstered by the permanent revocation of both mint and freeze authorities (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 7/10 | Low | Liquidity is fully secured with 100% of LP tokens burned (7.4 Economic). The 24h volume-to-liquidity ratio of 48.28 indicates significant wash-trading activity (7.8 Operations). Holder concentration… |
| **Upgrades** | 10/10 | Low | The mint is immutable with metadata and balance-mutating authorities disabled (7.7 Upgrades). There are no upgradeable components or proxy-like structures present in the SPL mint architecture. All… |

## Security Findings

_🟠 1 High · ⚪ 5 Informational_

### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

The 24-hour volume-to-liquidity ratio is 48.28, which exceeds the 20x threshold, indicating artificially inflated trade volume.

**Recommendation:** Exercise caution; high volume-to-liquidity ratios often indicate non-organic trading activity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17K (DexScreener, all pools). 24h trading volume $870K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17K of DEX liquidity across 5 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Bfmqsb...pump`](https://solscan.io/account/BfmqsbahsqYju8eTtCFVsLiwSdHqQsuMcTRsZhsspump) |
| **Network** | Solana |
| **Price** | $0.00004195 |
| **24h Volume** | $795.2K |
| **Liquidity** | $17.1K |
| **Volume / Liquidity** | 46.5× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7891 buys / 6824 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2nnhjxa299gq3gajcfrdsybhh2qknjqpdunyovtgjz82)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/waddle-world-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*

---
token: Bitaxum
ticker: BTX
network: solana
risk_score: 0
status: low
date: 2026-11-06
---

# Bitaxum (BTX) — Smart Contract Security Analysis | Solana

> **Risk Score: 0/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bitaxum-sol-ac5d)

---

## Audit Summary

Bitaxum (BTX) is a Token-2022 asset with fully revoked mint and freeze authorities, ensuring supply immutability and transfer safety. Liquidity is fully burned, eliminating withdrawal risks for the pool creator. Holder distribution data is unavailable, and a third-party registry flags high holder correlation, which should be monitored.

> **Final Recommendation:** Investors should monitor the token's market activity given the third-party registry flag regarding holder correlation. Since holder distribution data is currently unavailable, users should exercise caution regarding potential price volatility caused by concentrated supply.

Verify the current mint and freeze authority status periodically via block explorers to ensure no unexpected state changes have occurred. Use on-chain tools to track the largest token accounts to assess real-time concentration risks as data becomes available.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the Token-2022 program (7.1 Architecture). Both mint and freeze authorities are revoked, preventing supply inflation and account freezing (7.3 Access Control). No transfer hooks or… |
| **Governance / Economics** | 10/10 | Low | Liquidity is robust at $413,140 with 100% of LP tokens burned, ensuring permanent pool availability (7.4 Economic). Trading volume is healthy relative to liquidity, with a 0.64 ratio indicating no… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns, as is standard for SPL mints. All authority-related… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry flags the token for high holder correlation, suggesting that a significant portion of the supply may be controlled by a small group of related entities.

**Recommendation:** Monitor the top token holders on-chain to identify potential concentration risks and assess the impact of coordinated sell-offs.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's LP tokens are burned — that liquidity can never be withdrawn by anyone.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $414K (DexScreener, all pools). 24h trading volume $262K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Meme token  *(Severity: Informational · Status: Acknowledged)*

A community token whose value comes from attention rather than a product. Being a meme is not a risk in itself: it is scored on exactly the same contract and market facts as any other token. The class itself adds no points; the contract and market facts decide the score. Basis: launched on pump.fun, a meme launchpad. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $414K of DEX liquidity across 1 pools. Launch: launched on pump.fun, under a day of market history.

**Recommendation:** Expect attention-driven volatility; the facts in this report say whether the contract itself can be used against holders.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GNggUo...pump`](https://solscan.io/account/GNggUoCrkgcshssMFn1AxRGEeiNpS7fFaLJMEbSWpump) |
| **Network** | Solana |
| **Price** | $0.02722 |
| **24h Volume** | $262.4K |
| **Liquidity** | $413.6K |
| **Volume / Liquidity** | 0.6× |
| **Token Age** | 17h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 20801 buys / 2677 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ayqr8jmffl8kmxoejcgcx2vmths7hmxuurg22kytayfb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bitaxum-sol-ac5d)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*

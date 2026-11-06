---
token: IFHC
ticker: IFHC
network: solana
risk_score: 14
status: low
date: 2026-11-06
---

# IFHC (IFHC) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ifhc-sol)

---

## Audit Summary

The IFHC token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While liquidity is fully locked, third-party registry data indicates potential risks regarding holder correlation and LP provider concentration. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the token's holder distribution once data becomes available to assess the impact of the flagged high holder correlation. Given the low number of LP providers, ensure that slippage remains within acceptable bounds before executing large trades.

Verify the current mint and freeze authority status on-chain using a block explorer to confirm they remain set to null. No further administrative actions are required as the contract is immutable.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully locked (100%), preventing rug-pulls via liquidity withdrawal (7.4 Economic). Trading volume is healthy relative to liquidity, with a ratio of 1.31 (7.6 External). However… |
| **Upgrades** | 10/10 | Low | The token mint is immutable as both authorities are revoked (7.7 Upgrades). Metadata is not mutable, preventing branding changes (7.8 Operations). No further upgrade paths exist for this token… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `M-01` — High Holder Correlation  *(Severity: Medium · Status: Unresolved)*

Third-party risk registry signals indicate high holder correlation, which may suggest that a significant portion of the supply is controlled by a small group of related entities.

**Recommendation:** Monitor on-chain wallet movements for coordinated activity and assess the impact of potential concentrated selling pressure.


### `L-01` — Low LP Provider Count  *(Severity: Low · Status: Unresolved)*

Third-party registry data flags a low number of liquidity providers, which can lead to increased price volatility and difficulty in exiting large positions.

**Recommendation:** Exercise caution when trading and utilize limit orders to mitigate slippage risks associated with thin liquidity pools.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $28K (DexScreener, all pools). 24h trading volume $48K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $28K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`EJaknL...EVjv`](https://solscan.io/account/EJaknLSRiM3Xbd9oKEJ8X2ZxQ6AkiwC6RUwfE4suEVjv) |
| **Network** | Solana |
| **Price** | $0.00009062 |
| **24h Volume** | $34.6K |
| **Liquidity** | $27.3K |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 4h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 695 buys / 270 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5kgzg3tdk4kbxxhhg4zmqtgh9wusvewqborjy2hlywxq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ifhc-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-06*

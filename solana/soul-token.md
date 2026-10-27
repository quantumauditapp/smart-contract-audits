---
token: Soul Token
ticker: SOUL
network: solana
risk_score: 14
status: low
date: 2026-10-27
---

# Soul Token (SOUL) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/soul-token-sol)

---

## Audit Summary

The Soul Token (SOUL) utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While liquidity is robustly protected with 98.6% burned or locked, third-party registry data indicates a single-holder ownership risk. Holder distribution data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the single-holder concentration flagged by external registries, as this may lead to significant price volatility. Verify the current holder distribution using block explorers to assess the impact of the identified concentration before executing large trades.

Ensure that any future interaction with this token is conducted through decentralized exchanges that support the locked liquidity pool. No further action is required regarding authority management as the mint and freeze capabilities are already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token operates on the standard SPL Token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access Control).… |
| **Governance / Economics** | 9/10 | Low | Liquidity is well-secured with 98.6% locked, preventing rug-pulls via liquidity withdrawal (7.4 Economic). The volume/liquidity ratio is 8.55, indicating active trading relative to pool depth (7.6… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing unauthorized branding changes (7.7 Upgrades). As a standard SPL token, there are no upgradeable proxy patterns or administrative backdoors (7.8… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Single Holder Concentration  *(Severity: Medium · Status: Unresolved)*

A third-party risk registry has flagged the token for single-holder ownership, which may indicate high centralization of supply.

**Recommendation:** Monitor the top holder's wallet activity and assess the risk of a large-scale sell-off impacting market liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.8% of the pool's LP is burned or time-locked. 99.8% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity. 0.2% is held, unlocked, by 1 address(es) other than the pool's creator. This assessment covers the main pool, which holds 93% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $41K (DexScreener, all pools). 24h trading volume $273K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $41K of DEX liquidity across 5 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`E8hghm...Z9ve`](https://solscan.io/account/E8hghmFbrwhLHy4xzSS6Y5ubkPsk2uUnH9Cpn4S9Z9ve) |
| **Network** | Solana |
| **Price** | $0.0001279 |
| **24h Volume** | $264.1K |
| **Liquidity** | $38.2K |
| **Volume / Liquidity** | 6.9× |
| **Token Age** | 2h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1472 buys / 1014 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g6d6xpnh6kfku8c7cplgrulxzxtghr8dwvgtp6sgakku)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/soul-token-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*

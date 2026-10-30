---
token: JET
ticker: JET
network: solana
risk_score: 15
status: low
date: 2026-10-30
---

# JET (JET) — Smart Contract Security Analysis | Solana

> **Risk Score: 15/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/jet-sol)

---

## Audit Summary

The JET token utilizes the standard SPL Token program with both mint and freeze authorities successfully revoked. While liquidity is fully locked, the token is flagged as a 'Copycat token' by a third-party risk registry. Holder concentration data is currently unavailable.

> **Final Recommendation:** Investors should exercise caution due to the 'Copycat token' classification from third-party registries. Verify the token mint address against official project channels before interacting.

Monitor the token's liquidity and volume on-chain to ensure the market remains stable. Since holder concentration data is unavailable, avoid large positions that could be subject to significant price slippage.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is initialized on the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are revoked, ensuring no further supply inflation or account freezing (7.3 Access… |
| **Governance / Economics** | 9/10 | Low | Liquidity is fully locked (100.0%), preventing rug pulls via liquidity withdrawal (7.4 Economic). The volume/liquidity ratio is 7.78, indicating active but potentially volatile trading (7.8… |
| **Upgrades** | 10/10 | Low | The token metadata is immutable, preventing post-launch branding changes (7.7 Upgrades). There are no upgradeable components or proxy patterns in the SPL Token program (7.1 Architecture). All… |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `M-01` — Flagged as Copycat Token  *(Severity: Medium · Status: Unresolved)*

The token is identified as a 'Copycat token' by a third-party risk registry, suggesting it may be impersonating another project.

**Recommendation:** Verify the token's legitimacy through official project social media and documentation before trading.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in the pool program — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $10K (DexScreener, all pools). 24h trading volume $85K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $10K of DEX liquidity across 6 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`3uAfWx...QsBn`](https://solscan.io/account/3uAfWxkhj7SrTzpwvRAyxmupzQj3ds4zsHffHgNhQsBn) |
| **Network** | Solana |
| **Price** | $0.00001457 |
| **24h Volume** | $79.3K |
| **Liquidity** | $10.1K |
| **Volume / Liquidity** | 7.9× |
| **Token Age** | 6h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 705 buys / 458 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/n9t7wydjgtt5vsqcwa9tn3n5u9rosrevfuitxng9q5j)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/jet-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

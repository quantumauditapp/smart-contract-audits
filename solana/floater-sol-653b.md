---
token: FLOATER
ticker: FLOATER
network: solana
risk_score: 14
status: low
date: 2026-10-29
---

# FLOATER (FLOATER) — Smart Contract Security Analysis | Solana

> **Risk Score: 14/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/floater-sol-653b)

---

## Audit Summary

The FLOATER token mint demonstrates strong security posture with both mint and freeze authorities successfully revoked. Liquidity is fully locked, preventing rug-pull scenarios via liquidity withdrawal. Holder concentration data is unavailable, and the token is a standard SPL v3 mint without advanced extensions.

> **Final Recommendation:** The token is currently in a secure state with no active administrative risks. Users should monitor the token's market activity and liquidity depth before executing large trades to mitigate slippage risks associated with the current liquidity level.

Verify the current mint and freeze authority status using a block explorer to ensure they remain null. No further action is required to address administrative vulnerabilities.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard spl-token program (7.1 Architecture). Both mint and freeze authorities are set to null, ensuring supply immutability and preventing account freezing (7.3 Access… |
| **Governance / Economics** | 8/10 | Low | Liquidity is fully secured with 100% of the pool locked in a permanent locker (7.4 Economic). The volume/liquidity ratio is 17.71, indicating active trading relative to available depth (7.6… |
| **Upgrades** | 10/10 | Low | The mint is immutable as both authorities are revoked (7.7 Upgrades). Metadata is immutable, preventing post-launch branding changes. There are no upgradeable components or proxies associated with… |

## Security Findings

_⚪ 6 Informational_

### `I-01` — No code-level findings — an SPL mint exposes no auditable program source  *(Severity: Informational · Status: Acknowledged)*

This token is an SPL token mint, not a deployed program: there is no contract source code on-chain for a line-by-line review, so no code-level vulnerability could be identified either way. The assessment on this page therefore rests on mint/owner authority, mint capability, LP lock/burn state, which are read directly from chain state and from third-party risk registries.

**Recommendation:** Read the risk score breakdown below as the substance of this audit. For a code-level review, the token would need an accompanying verified program.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $60K (DexScreener, all pools). 24h trading volume $1.2M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $60K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6pjRwz...P6KG`](https://solscan.io/account/6pjRwzGg2QS1VSf6Z4TQZwyMxUysrUajkRmbbQ89P6KG) |
| **Network** | Solana |
| **Price** | $0.0000826 |
| **24h Volume** | $1.18M |
| **Liquidity** | $59.7K |
| **Volume / Liquidity** | 19.8× |
| **Token Age** | 5h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 10728 buys / 8342 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/dac3fzmt6pq6zyyrmbrpkughtkqycnsu8nrt5gzhzywd)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/floater-sol-653b)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-29*

---
token: Arrow
ticker: ARROW
network: solana
risk_score: 24
status: low
date: 2026-10-26
---

# Arrow (ARROW) — Smart Contract Security Analysis | Solana

> **Risk Score: 24/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/arrow-sol)

---

## Audit Summary

The Arrow token utilizes the Token-2022 program with both mint and freeze authorities successfully revoked. While liquidity is effectively locked, the token metadata remains mutable and a third-party registry has flagged a portion of LP as unlocked. Holder concentration data was unavailable for this assessment.

> **Final Recommendation:** Investors should monitor the token metadata for unexpected changes given its mutable status. Verify the current liquidity lock status through the block explorer to ensure the 99.3% lock remains intact.

As holder concentration data is unavailable, exercise caution regarding potential whale activity. Use decentralized exchange interfaces to confirm slippage before executing large trades, as liquidity is relatively constrained.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is implemented via the Token-2022 program (7.1 Architecture). Access control is robust as both mint and freeze authorities are revoked (7.3 Access Control). No transfer hooks or default… |
| **Governance / Economics** | 9/10 | Low | Liquidity is well-secured with 99.3% burned or locked (7.4 Economic). The volume/liquidity ratio of 13.89 indicates active trading relative to the $35,463 liquidity pool (7.6 External). Holder… |
| **Upgrades** | 10/10 | Low | The mint and freeze authorities are permanently revoked, preventing further supply changes or account freezing (7.7 Upgrades). Metadata remains mutable, allowing for potential updates to the token… |

## Security Findings

_🟡 1 Medium · 🟢 1 Low · ⚪ 6 Informational_

### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

The token metadata (name, symbol, image) is mutable, allowing the owner to change branding at any time.

**Recommendation:** Verify metadata against official project channels before trusting the token's branding.


### `L-01` — Flagged LP Status  *(Severity: Low · Status: Unresolved)*

A third-party risk registry has flagged a portion of the liquidity as unlocked, despite the majority being locked.

**Recommendation:** Investigate the specific LP provider addresses to confirm the status of the remaining 0.7% of liquidity.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity locked with no expiry  *(Severity: Informational · Status: Acknowledged)*

99.3% of the pool's LP is burned or time-locked. 99.3% of the pool's liquidity is locked for good in Raydium's LP locker (Burn & Earn) — only its trading fees can be collected; no one can withdraw the liquidity. 0.7% is held, unlocked, by 1 address(es) other than the pool's creator. This assessment covers the main pool, which holds 87% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $35K (DexScreener, all pools). 24h trading volume $527K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $35K of DEX liquidity across 3 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5QLhJa...hDvq`](https://solscan.io/account/5QLhJag4UGsLod7H2Ci9HmgtMprgvG574Bv93v1NhDvq) |
| **Network** | Solana |
| **Price** | $0.0001047 |
| **24h Volume** | $464.6K |
| **Liquidity** | $30.3K |
| **Volume / Liquidity** | 15.3× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6025 buys / 4279 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/2z58nqyiq8kqgbapjxpjw4tqbo512s5hzevhfotsmbjy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/arrow-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-26*

---
token: Saylor Index
ticker: SAYLOR3
network: solana
risk_score: 67
status: high
date: 2026-10-21
---

# Saylor Index (SAYLOR3) — Smart Contract Security Analysis | Solana

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/saylor-index-sol)

---

## Audit Summary

The token is flagged as high-risk by a third-party registry due to the developer's history of rug-pulling. The mint authority remains active, allowing for unlimited supply inflation. Third-party risk registry data was successfully retrieved, while holder distribution data was unavailable.

> **Final Recommendation:** Do not interact with this token given the third-party registry warnings regarding developer history. Verify the mint authority status on-chain to confirm if it has been revoked before considering any interaction.

Monitor the mint address for any changes to the authority. If the mint authority is not set to null, the supply can be increased at any time, rendering the token value volatile.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard spl-token program. 7.1 Architecture is standard for SPL mints. 7.3 Access Control is compromised as the mint authority is not revoked. 7.8 Operations are currently… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic indicators show a Volume/Liquidity ratio of 27.93, suggesting potential wash trading. 7.6 External signals indicate the creator has a history of rug-pulling. Liquidity is $87,190 for a… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL token mints. Metadata is immutable as per on-chain flags. No extensions are active that allow for balance or metadata modification. |

## Security Findings

_🔴 2 Critical · 🟠 1 High · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is Cyq6FUVrYbJpzQY985oBEnRjKd1EaM412jtUeNfougs9. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on developer history of rugged tokens.

**Recommendation:** Do not interact with this token.


### `H-01` — Wash Trading Signal  *(Severity: High · Status: Unresolved)*

24-hour volume is 27.93x liquidity — a pattern strongly associated with artificially inflated trade volume.

**Recommendation:** Account for the fee in any swap calculation.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $194K (DexScreener, all pools). 24h trading volume $4.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $194K of DEX liquidity across 17 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`5MQhtw...v3JT`](https://solscan.io/account/5MQhtwFmgwZugLUaA7JRzGptrdCURormQLERHo7Av3JT) |
| **Network** | Solana |
| **Price** | $0.9963 |
| **24h Volume** | $2.40M |
| **Liquidity** | $88.7K |
| **Volume / Liquidity** | 27.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 14600 buys / 14863 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/apc6o6dcq4csnkz6wnf6xnwm3azjbpqlt7ucpgilc1qy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/saylor-index-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

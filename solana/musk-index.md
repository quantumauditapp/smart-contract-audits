---
token: MUSK Index
ticker: MUSK4
network: solana
risk_score: 60
status: medium
date: 2026-10-21
---

# MUSK Index (MUSK4) — Smart Contract Security Analysis | Solana

> **Risk Score: 60/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/musk-index-sol)

---

## Audit Summary

The MUSK Index token presents critical risks due to an active mint authority and a negative reputation in third-party risk registries. While the freeze authority is revoked, the ability to inflate supply and the creator's history of malicious activity necessitate extreme caution. Third-party risk registry data was successfully retrieved.

> **Final Recommendation:** Do not interact with this token due to the active mint authority and the creator's history of malicious activity. If you currently hold the token, consider exiting your position immediately as the supply can be diluted at any time.

Verify the mint authority status on a block explorer; if it remains active, the token is not suitable for long-term holding. Monitor the creator's wallet for further suspicious activity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard, but 7.3 Access Control is compromised by an active mint authority (5FWbu1KohCDg1hYYNJvVQbnwj3KWAnY8rswpCNQAEWKn).… |
| **Governance / Economics** | 7/10 | Low | 7.4 Economic factors show a 4-day old pair with $133,149 in liquidity. Holder concentration is moderate, with the top 10 holders controlling 18.18% of the supply. 7.5 Governance is non-existent, and… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are not applicable to standard SPL tokens. Metadata is immutable, and no extensions like transfer hooks or permanent delegates are configured. The freeze authority is successfully… |

## Security Findings

_🔴 2 Critical · ⚪ 6 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 5FWbu1KohCDg1hYYNJvVQbnwj3KWAnY8rswpCNQAEWKn. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset regarding developer history.

**Recommendation:** Do not interact with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 44.1% of supply. Of that, 25.9% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.0% in wallets, 14.2% in other contracts. 10,751 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

10,751 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $448K (DexScreener, all pools). 24h trading volume $8.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $448K of DEX liquidity across 25 pools. Launch: 4 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`ysPp2B...oS5a`](https://solscan.io/account/ysPp2Bt2j2UQu2tZwtSJz7JxyrmQ8GJcNJE5NyDoS5a) |
| **Network** | Solana |
| **Price** | $1.0670 |
| **24h Volume** | $1.09M |
| **Liquidity** | $129.2K |
| **Volume / Liquidity** | 8.5× |
| **Token Age** | 4d |
| **Top-10 Holders** | 44.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 5496 buys / 5314 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/ahj4rz7q9iu9bxg7pfzqf3nse2rpwns2nce2btrtf4cz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/musk-index-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-21*

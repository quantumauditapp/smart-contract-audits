---
token: Umbra
ticker: UMBRA
network: solana
risk_score: 65
status: high
date: 2026-11-03
---

# Umbra (UMBRA) — Smart Contract Security Analysis | Solana

> **Risk Score: 65/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/umbra-sol)

---

## Audit Summary

The UMBRA token maintains an active mint authority, posing a significant risk of supply dilution. While the freeze authority is revoked, the token metadata remains mutable and holder concentration is elevated at 63.03%. Third-party registry data indicates high-risk flags regarding developer control and concentration.

> **Final Recommendation:** Investors should monitor the mint authority address for potential revocation. Verify the liquidity lock status through the DEX interface to ensure the pool creator cannot withdraw funds.

Users should exercise caution regarding the mutable metadata and high holder concentration. Avoid large positions until the mint authority is set to null and metadata is locked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for SPL mints. 7.3 Access Control is currently compromised by an active mint authority… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic analysis shows a 63.03% concentration among the top 10 holders. 7.5 Governance is centralized due to the active mint authority. Liquidity is robust at $1.74M with a healthy 0.31… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints, but 7.2 Code Security is impacted by mutable metadata. The token name and symbol can be altered by the current authority. No other upgradeable extensions… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 6VsC8PuKkXm5xo54c2vbrAaSfQipkpGHqNuKTxXFySx6. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Holder Concentration > 50%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 63.03% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallet activity for potential exit signals.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.3% of supply. Of that, 7.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 7.1% in wallets, 56.0% in other contracts. 6,210 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Umbra (UMBRA), market cap $8M, rank #1406. 6,210 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.7M (DexScreener, all pools). 24h trading volume $402K (CoinGecko, all markets, daily snapshot). 24h trading volume $511K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.7M of DEX liquidity across 20 pools. Launch: 389 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`PRVT6T...meta`](https://solscan.io/account/PRVT6TB7uss3FrUd2D9xs2zqDBsa3GbMJMwCQsgmeta) |
| **Network** | Solana |
| **Price** | $0.6075 |
| **24h Volume** | $504.4K |
| **Liquidity** | $1.71M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 598 buys / 488 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/blkbse96kqys7srmiokxemivbeo4ckk2y4n1jphkxynv)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/umbra-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-03*

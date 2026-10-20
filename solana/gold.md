---
token: GOLD
ticker: GOLD
network: solana
risk_score: 64
status: medium
date: 2026-10-02
---

# GOLD (GOLD) — Smart Contract Security Analysis | Solana

> **Risk Score: 64/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gold-sol)

---

## Audit Summary

The GOLD token mint has a critical security vulnerability due to an unrevoked mint authority, allowing the holder to create unlimited new tokens. Additionally, the token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. Third-party registry data on pool liquidity locking was unavailable for this assessment.

> **Final Recommendation:** Before engaging with the GOLD token, verify on-chain that the mint authority at HKMT2i4kGzktb4AVo4fKkHK4AmpxVyvGEAfotVX3tML4 has been set to null to ensure the supply is fixed. Monitor the token's metadata for any unexpected changes to its branding. Additionally, investigate the locking status of the token's liquidity pool to understand potential rug pull risks, as this information was not available during this audit.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The GOLD token is an SPL token operating under the `spl-token` program. It has a total supply of 576,247,312 tokens with 6 decimals. A critical risk is present as the mint authority… |
| **Governance / Economics** | 7/10 | Low | The token exhibits moderate holder concentration, with the top 10 holders that can sell accounting for 42.05% of the supply. Liquidity is substantial at $974,558 USD, with a healthy 24-hour volume of… |
| **Upgrades** | 5/10 | Medium | The mint authority for the GOLD token is still active, which allows for changes to the token's total supply. While the freeze authority has been revoked, the token's metadata is mutable, meaning its… |

## Security Findings

_🔴 1 Critical · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is HKMT2i4kGzktb4AVo4fKkHK4AmpxVyvGEAfotVX3tML4. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.7% of supply. Of that, 36.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 4.1% in wallets, 38.0% in other contracts. 11,116 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as GOLD (GOLD), market cap $2M, rank #2273. 11,116 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.4M (DexScreener, all pools). 24h trading volume $4.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $6.0M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.4M of DEX liquidity across 30 pools. Launch: 367 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GoLDpp...iw6A`](https://solscan.io/account/GoLDppdjB1vDTPSGxyMJFqdnj134yH6Prg9eqsGDiw6A) |
| **Network** | Solana |
| **Price** | $4,185.7300 |
| **24h Volume** | $717.5K |
| **Liquidity** | $974.6K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 1y |
| **Top-10 Holders** | 78.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1862 buys / 1677 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/cpg1zmhhk7igkpvs1a6ytf4hjbziy8xq1jkax5gbfaz2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gold-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-02*

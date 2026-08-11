---
token: NVIDIA xStock
ticker: NVDAX
network: solana
risk_score: 100
status: critical
date: 2026-08-11
---

# NVIDIA xStock (NVDAX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nvidia-xstock-sol)

---

## Audit Summary

The NVIDIA xStock (NVDAx) token mint has critical security risks due to unrevoked mint, freeze, and permanent delegate authorities, allowing the issuer to control supply and user funds. Additionally, holder concentration is very high, and metadata and balances can be mutated. Third-party registry data confirms these enabled controls.

> **Final Recommendation:** Before any interaction, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to ensure the supply is fixed and funds are secure from issuer control. Monitor the top holder accounts for any significant movements that could impact market stability. Be aware that token metadata can be changed, so confirm branding against official sources periodically.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL Token-2022 mint. It has a Mint Authority at `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`, allowing unlimited new token creation. A Freeze Authority at… |
| **Governance / Economics** | 1/10 | High | Holder concentration is very high, with the top 10 token accounts holding 82.03% of the total supply, posing a significant risk of price manipulation or sudden sell-offs. Liquidity is substantial at… |
| **Upgrades** | 1/10 | High | The token's core authorities, including Mint Authority, Freeze Authority, and Permanent Delegate, remain unrevoked, granting the issuer extensive control over the token's supply and user funds. While… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is `JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs`. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

`5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq` has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 82.03% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify user balances, as this grants significant control over token holdings.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xsc9qv...9qEh`](https://solscan.io/account/Xsc9qvGR1efVDFGLrVsmkzv3qi45LTBjeUKSPmx9qEh) |
| **Network** | Solana |
| **Price** | $219.8600 |
| **24h Volume** | $1.97M |
| **Liquidity** | $2.49M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 82.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7025 buys / 6440 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ❌ Fail |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ⚠️ Unknown |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ❌ | Source code is **not verified** — contract logic is opaque. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/49imatqtoyabsyaqc8gafvq6aebfvdxsrh44oiatyyw6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nvidia-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

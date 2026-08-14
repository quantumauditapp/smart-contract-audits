---
token: Circle xStock
ticker: CRCLX
network: solana
risk_score: 100
status: critical
date: 2026-08-14
---

# Circle xStock (CRCLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/circle-xstock-sol)

---

## Audit Summary

This audit identifies critical centralization risks for the Circle xStock (CRCLx) token due to active mint, freeze, and permanent delegate authorities, which allow for unlimited new token creation, account freezing, and unauthorized fund transfers. Additionally, a balance-mutating authority is present, and metadata can be changed. Holder concentration is moderate, with the top 10 accounts holding 64.54% of the supply. Third-party registry data indicates multiple high-risk flags, including enabled mint and freeze authorities and permanent control. Holder distribution data from chain-native RPC was unavailable.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint authority and freeze authority have been revoked to prevent supply dilution and account freezing. Confirm that the permanent delegate authority has been removed to ensure funds cannot be moved without consent. Monitor the token's metadata for any unexpected changes. Regularly check the holder distribution to assess changes in concentration and potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The Circle xStock (CRCLx) token operates on the spl-token-2022 program, indicating modern SPL token standards and extensions. However, significant centralized control exists. The mint authority… |
| **Governance / Economics** | 1/10 | High | The token exhibits a medium level of holder concentration, with the top 10 accounts holding 64.54% of the total supply. This concentration poses a risk of price volatility due to potential… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, meaning its name, symbol, or image can be altered post-launch. While the transfer hook is not currently active, its upgradability is enabled. The mint authority and… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

Top 10 token accounts hold 64.54% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the potential impact of large holder movements on market price.


### `M-02` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority on token supply and individual holdings.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsueG8...3bd1`](https://solscan.io/account/XsueG8BtpquVJX9LVLLEGuViXUungE6WmK5YZ3p3bd1) |
| **Network** | Solana |
| **Price** | $74.7500 |
| **24h Volume** | $2.31M |
| **Liquidity** | $2.47M |
| **Volume / Liquidity** | 0.9× |
| **Token Age** | 1y |
| **Top-10 Holders** | 64.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2160 buys / 1700 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g39wywqukbhk8f2wzzzfx3fcsyg91vccbbr6wevp5axy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/circle-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*

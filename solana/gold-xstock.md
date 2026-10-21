---
token: Gold xStock
ticker: GLDX
network: solana
risk_score: 100
status: critical
date: 2026-09-12
---

# Gold xStock (GLDX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gold-xstock-sol)

---

## Audit Summary

The Gold xStock (GLDx) SPL Token Mint presents critical security risks due to active Mint, Freeze, and Permanent Delegate authorities, which allow for unlimited minting, account freezing, and direct fund transfers without consent. Additionally, 97.2% of the token supply is concentrated in the top 10 accounts, posing a high risk of market manipulation. Third-party registry data confirms these active authorities and high holder concentration. Holder distribution data was unavailable for a full assessment.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority has been revoked to ensure a fixed supply. Confirm that the Freeze Authority is nullified to prevent arbitrary account freezes. Given the active Permanent Delegate, treat any holdings as fully custodial, as funds can be moved without your consent. Monitor the token's metadata for any changes to its branding or identity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token operates on the spl-token-2022 program, with a total supply of 11,626,888,692,537 tokens and 8 decimals. Critical authorities are active: the Mint Authority is… |
| **Governance / Economics** | 1/10 | High | Holder concentration is extremely high, with the top 10 token accounts holding 97.2% of the total supply, indicating significant centralization risk. The total DEX liquidity is $539,781, supporting a… |
| **Upgrades** | 1/10 | High | The Mint Authority, Freeze Authority, and Permanent Delegate are all active, granting significant control over the token's parameters and user funds. The token utilizes the spl-token-2022 program… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 97.2% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant risk of price volatility due to concentrated holdings.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify token balances directly.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xsv9hR...D3re`](https://solscan.io/account/Xsv9hRk1z5ystj9MhnA7Lq4vjSsLwzL2nxrwmwtD3re) |
| **Network** | Solana |
| **Price** | $396.3900 |
| **24h Volume** | $4.18M |
| **Liquidity** | $1.01M |
| **Volume / Liquidity** | 4.1× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 94.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 9377 buys / 8436 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/78revnmlgrwmjtf2hmbohue2prcsctxttbxjnbhchyze)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gold-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

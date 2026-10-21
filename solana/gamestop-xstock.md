---
token: Gamestop xStock
ticker: GMEX
network: solana
risk_score: 100
status: critical
date: 2026-09-22
---

# Gamestop xStock (GMEX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamestop-xstock-sol)

---

## Audit Summary

This SPL Token-2022 mint exhibits critical centralization risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing the issuer to control supply and user funds. Additionally, over 96% of the token supply is held by the top 10 accounts, posing a significant market manipulation risk. Third-party registry data was available and confirmed these authority risks.

> **Final Recommendation:** Before any interaction, verify on-chain that the Mint Authority and Freeze Authority have been set to null to prevent arbitrary supply inflation or account freezing. Given the presence of a Permanent Delegate, treat this token as fully custodial, as funds can be moved without consent. Monitor the top holder distribution for any changes, as the current concentration poses a significant risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The Gamestop xStock (GMEx) token is an SPL Token-2022 mint. It has an active Mint Authority at `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`, allowing for unlimited new token creation. A Freeze… |
| **Governance / Economics** | 1/10 | High | The token exhibits very high holder concentration, with the top 10 token accounts holding 96.47% of the total supply. This level of concentration makes the token highly susceptible to price… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. The `transfer_hook_upgradable` flag is true, but no transfer hook is currently active. The Mint… |

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

Top 10 token accounts hold 96.47% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant risk of price manipulation due to concentrated holdings.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to arbitrarily change token balances.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xsf9mB...PRGc`](https://solscan.io/account/Xsf9mBktVB9BSU5kf4nHxPq5hCBJ2j2ui3ecFGxPRGc) |
| **Network** | Solana |
| **Price** | $24.0350 |
| **24h Volume** | $3.35M |
| **Liquidity** | $437.5K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 96.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13873 buys / 14323 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hsqxf9l7tpwf1pkjwwsbnew2vytppgrfwwna4gq2n2x)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamestop-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*

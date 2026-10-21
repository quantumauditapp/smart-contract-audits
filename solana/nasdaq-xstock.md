---
token: Nasdaq xStock
ticker: QQQX
network: solana
risk_score: 100
status: critical
date: 2026-09-17
---

# Nasdaq xStock (QQQX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nasdaq-xstock-sol)

---

## Audit Summary

This Nasdaq xStock (QQQx) SPL Token-2022 mint presents critical centralization risks due to active Mint, Freeze, and Permanent Delegate authorities, which allow for supply manipulation, fund freezing, and unauthorized transfers. Holder concentration is very high, with the top 10 accounts controlling 85.89% of the supply. Third-party risk registry data was available and confirmed these active authorities and high ownership.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to prevent arbitrary supply inflation, account freezing, and fund confiscation. Monitor the token's metadata for any changes to its branding. Be aware of the high holder concentration and its potential impact on price stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL Token-2022 mint, indicating modern Solana token standards. However, the Mint Authority (7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj) and Freeze Authority… |
| **Governance / Economics** | 1/10 | High | The token exhibits high holder concentration, with the top 10 accounts holding 85.89% of the total supply, which creates a significant risk of price volatility from large sell-offs. Liquidity is… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. While the transfer hook is currently inactive, the `transfer_hook_upgradable` flag is true, allowing a… |

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

Top 10 token accounts hold 85.89% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the high concentration when assessing market stability and potential price impact from large holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify user balances, as this grants significant control over token holdings.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xs8S1u...mWHZ`](https://solscan.io/account/Xs8S1uUs1zvS2p7iwtsG3b6fkhpvmwz4GYU3gWAmWHZ) |
| **Network** | Solana |
| **Price** | $743.5100 |
| **24h Volume** | $1.20M |
| **Liquidity** | $2.28M |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 85.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1915 buys / 1966 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/gmjglwzvk75lpetrgamdexnvxc4fuuqpwjxeqqtdu1ag)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nasdaq-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*

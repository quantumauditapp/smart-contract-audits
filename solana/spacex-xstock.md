---
token: SpaceX xStock
ticker: SPCXX
network: solana
risk_score: 100
status: critical
date: 2026-09-20
---

# SpaceX xStock (SPCXX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-xstock-sol)

---

## Audit Summary

This SPL Token Mint audit for SpaceX xStock (SPCXx) reveals critical security risks due to active administrative authorities. The mint authority, freeze authority, and a permanent delegate are all unrevoked, allowing for unlimited new token minting, account freezing, and direct fund transfers without consent. Additionally, 92.17% of the token supply is held by the top 10 accounts, indicating high centralization. Third-party registry data was available, but chain-native holder distribution details were not.

> **Final Recommendation:** Holders should verify on-chain that the mint authority, freeze authority, and permanent delegate are revoked before considering the token supply fixed or their funds secure. Due to the high holder concentration, monitor large transfers from top accounts for potential market impact. Be aware that metadata can be changed, so verify branding periodically against official sources. Given the active administrative controls, treat this token as fully custodial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is implemented using the spl-token-2022 program. Critical administrative controls remain active: the mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj, the freeze authority is… |
| **Governance / Economics** | 1/10 | High | The token exhibits very high holder concentration, with the top 10 accounts holding 92.17% of the total supply, posing a significant risk of price manipulation. Total DEX liquidity is $1,784,690… |
| **Upgrades** | 1/10 | High | All primary administrative authorities (mint, freeze, permanent delegate) remain unrevoked, allowing for potential future changes to token parameters and supply. The token's metadata is mutable… |

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

Top 10 token accounts hold 92.17% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant market impact potential from large holders. Monitor top holder movements closely.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify user balances. This introduces a custodial element.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xs3oZw...qpH8`](https://solscan.io/account/Xs3oZwbHvqis4NYcf4YKWmEia2eC84wSiVrcYcTqpH8) |
| **Network** | Solana |
| **Price** | $152.7300 |
| **24h Volume** | $13.09M |
| **Liquidity** | $2.50M |
| **Volume / Liquidity** | 5.2× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 91.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 29344 buys / 26991 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ahnn6jmvagg6xuosg7ser38grydb2jtbuvqxvuqarhpq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*

---
token: Vida Global xStock
ticker: VIDAX
network: solana
risk_score: 100
status: critical
date: 2026-09-05
---

# Vida Global xStock (VIDAX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vida-global-xstock-sol)

---

## Audit Summary

This SPL Token Mint presents critical risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing for unlimited minting, account freezing, and direct fund confiscation. Additionally, 99.73% of the supply is held by the top 10 accounts, posing a significant centralization risk. Third-party registry data confirms these authority risks. Holder distribution data from chain-native RPC was unavailable, but GoPlus data provided top holder concentration.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to prevent arbitrary supply changes, account freezing, or fund confiscation. Monitor the token's holder distribution for decentralization improvements and observe market behavior as the DEX pair matures beyond its current 4-day age. Confirm the token's metadata against official sources to ensure branding consistency, given its mutability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL Token-2022 mint, indicating support for advanced extensions. However, the Mint Authority (7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj) remains active, allowing for arbitrary… |
| **Governance / Economics** | 1/10 | High | Holder concentration is extremely high, with the top 10 token accounts controlling 99.73% of the total supply, creating significant centralization risk. The token's DEX pair is very new, established… |
| **Upgrades** | 1/10 | High | The token's core authorities, including Mint Authority and Freeze Authority, are not revoked, allowing for future changes to supply and account status. The Permanent Delegate authority is also… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low_

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

Top 10 token accounts hold 99.73% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Be aware of the significant market manipulation risk due to extreme holder concentration.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 4 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the limited operational history of the DEX pair.


### `M-02` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand who controls the balance-mutating authority and its intended use before holding the token.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsfCC9...zmTk`](https://solscan.io/account/XsfCC9VL4DamVGNgdJpfLXB3sBVa158Gbx8sh7NzmTk) |
| **Network** | Solana |
| **Price** | $1.8800 |
| **24h Volume** | $67.9K |
| **Liquidity** | $49.5K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 4d |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2090 buys / 1943 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/edbmuqjwzwp8dxe7gwdtfsbsecr2hetyws8hxv2no95t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vida-global-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*

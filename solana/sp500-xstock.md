---
token: SP500 xStock
ticker: SPYX
network: solana
risk_score: 100
status: critical
date: 2026-09-12
---

# SP500 xStock (SPYX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sp500-xstock-sol)

---

## Audit Summary

This SPL Token-2022 mint exhibits critical risks due to the presence of a mint authority, freeze authority, and a permanent delegate, allowing for arbitrary token creation, account freezing, and fund confiscation. Additionally, a high concentration of tokens among the top holders poses a significant market manipulation risk. Third-party registry data was available and confirmed these authority risks.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint authority, freeze authority, and permanent delegate have been revoked to prevent arbitrary supply inflation, account freezing, or fund confiscation. Monitor for any changes to the token's metadata or the activation of a transfer hook, as these could introduce new risks. Given the high holder concentration, exercise caution regarding potential market manipulation.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL Token-2022 mint, indicating modern Solana token standards. However, the mint authority (7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj), freeze authority… |
| **Governance / Economics** | 1/10 | High | The token exhibits high holder concentration, with the top 10 accounts holding 74.12% of the total supply, posing a significant risk of price volatility from large sell-offs. Liquidity is robust at… |
| **Upgrades** | 1/10 | High | The token is an SPL Token-2022, supporting extensions. While the transfer hook is currently inactive, it is `transfer_hook_upgradable: True`, meaning one could be added later. The `metadata_mutable`… |

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

Top 10 token accounts hold 74.12% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the fee in any swap calculation.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Account for the fee in any swap calculation.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsoCS1...DF2W`](https://solscan.io/account/XsoCS1TfEyfFhfvj8EtZ528L3CaKBDBRqRapnBbDF2W) |
| **Network** | Solana |
| **Price** | $777.2300 |
| **24h Volume** | $12.14M |
| **Liquidity** | $3.79M |
| **Volume / Liquidity** | 3.2× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 67.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 25341 buys / 34838 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7a8xxajbeldo6p9diksyctdw6ce8f4mwr3ahcad8ao49)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sp500-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-12*

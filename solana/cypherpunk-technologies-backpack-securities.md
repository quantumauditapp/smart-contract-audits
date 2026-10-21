---
token: Cypherpunk Technologies - Backpack Securities
ticker: CYPH
network: solana
risk_score: 100
status: critical
date: 2026-09-20
---

# Cypherpunk Technologies - Backpack Securities (CYPH) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cypherpunk-technologies-backpack-securities-sol)

---

## Audit Summary

This SPL Token-2022 mint presents critical risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing for arbitrary minting, freezing, and fund transfers. Additionally, the token's balance mutability and mutable metadata introduce further control risks. Third-party registry data on holder distribution was unavailable.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to prevent unilateral control over supply and user funds. Monitor for any changes to the token's metadata, as it can be altered post-launch. Given the very new pair age, exercise extreme caution and observe market behavior over a longer period.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The token is an SPL Token-2022 mint with a total supply of 119,446,740.336 tokens (6 decimals). It features an active Mint Authority at `Cmzoo3U8ezcb95BJYmy3e6p6Lh1kyPm2bjDLcvNtVXES`, a Freeze… |
| **Governance / Economics** | 1/10 | High | The token has a liquidity of $165,561 USD and a 24-hour volume of $1,020,515 USD. The Volume/Liquidity Ratio is 6.16, indicating significant trading activity relative to available liquidity. The DEX… |
| **Upgrades** | 1/10 | High | The Mint Authority, Freeze Authority, and Permanent Delegate are all active, allowing for significant control over the token's parameters and user funds. The token's metadata is mutable, meaning its… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is Cmzoo3U8ezcb95BJYmy3e6p6Lh1kyPm2bjDLcvNtVXES. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value. (Fact: Mint Authority: Cmzoo3U8ezcb95BJYmy3e6p6Lh1kyPm2bjDLcvNtVXES)

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds. (Fact: Freeze Authority: 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a)

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent. (Fact: Permanent Delegate: 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a (can move user funds))

**Recommendation:** Treat this token as fully custodial.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 1 days ago. Insufficient track record to assess team or holder behaviour. (Fact: Pair Age (days): 1)

**Recommendation:** Exercise caution due to the lack of historical data and observe market behavior over a longer period.


### `M-02` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances. (Fact: balance_mutable: True)

**Recommendation:** Understand the implications of an authority being able to unilaterally modify user balances before holding this token.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch. (Fact: metadata_mutable: True)

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CYPHuM...uawK`](https://solscan.io/account/CYPHuMmCL1GxJWa2tsPhLKykC7GrHJTCHwbXD4g5uawK) |
| **Network** | Solana |
| **Price** | $3.4400 |
| **24h Volume** | $406.1K |
| **Liquidity** | $89.9K |
| **Volume / Liquidity** | 4.5× |
| **Token Age** | 1d |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2778 buys / 2752 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/9hykhcccuhnhc7192tkkrrmhvtpduxrmrdinhgcyyap1)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cypherpunk-technologies-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*

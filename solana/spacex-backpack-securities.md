---
token: SpaceX - Backpack Securities
ticker: SPCX
network: solana
risk_score: 100
status: critical
date: 2026-09-20
---

# SpaceX - Backpack Securities (SPCX) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-backpack-securities-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical security risks due to the presence of a mint authority, freeze authority, and a permanent delegate, allowing for arbitrary token minting, freezing of accounts, and transfer of user funds without consent. Additionally, a balance-mutating authority is active, and metadata can be changed. Third-party registry data was available and confirmed these authority flags. Holder distribution data was partially available, showing top 10 holders at 33.88%.

> **Final Recommendation:** Before interacting with this token, it is crucial to verify on-chain that the mint authority has been permanently revoked to ensure a fixed supply. Given the active freeze authority and permanent delegate, users should be aware of the custodial risks, as funds can be frozen or moved without consent. Monitor the token's metadata for any unannounced changes to branding.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | This token is implemented using the spl-token-2022 program, indicating support for advanced extensions (7.1 Architecture). As an SPL token mint, there is no on-chain source code for traditional code… |
| **Governance / Economics** | 1/10 | High | The token has a total DEX liquidity of $843,054, with a 24-hour volume of $316,899, resulting in a normal Volume/Liquidity Ratio of 0.38. The DEX pair has been active for 99 days, providing some… |
| **Upgrades** | 1/10 | High | The token mint's core authorities, including mint and freeze authorities, are not revoked, allowing for potential changes to the token supply and account states (7.7 Upgrades). A permanent delegate… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟡 1 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is HK6jF79duLLLfCMRQFBSgo6CgQ5mF4tFMFU7CmKcXctZ. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Treat this token as having a potential for balance manipulation.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SPCXxc...imGb`](https://solscan.io/account/SPCXxcqXj6e5dJDVNovHN8744zkbhM2bYudU45BimGb) |
| **Network** | Solana |
| **Price** | $151.5800 |
| **24h Volume** | $430.0K |
| **Liquidity** | $913.5K |
| **Volume / Liquidity** | 0.5× |
| **Token Age** | 3mo |
| **Top-10 Holders** | 36.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1701 buys / 1593 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7nvqtyqipn564e9obi6yzfgox4wl6cr4zslyyipqgtwu)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*

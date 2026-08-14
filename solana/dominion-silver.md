---
token: Dominion Silver
ticker: SILV
network: solana
risk_score: 100
status: critical
date: 2026-08-14
---

# Dominion Silver (SILV) — Smart Contract Security Analysis | Solana

> **Risk Score: 100/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dominion-silver-sol)

---

## Audit Summary

This SPL Token Mint presents critical risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing the issuer to control supply and user funds. Holder concentration is extremely high at 94.84% among the top 10 accounts, posing significant market manipulation risk. The DEX pair is also very new, having been created 0 days ago. Third-party registry data on holder distribution was unavailable from chain-native RPC, but external security signals provided top holder percentage.

> **Final Recommendation:** Prospective holders should verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked before considering any interaction with this token. Given the active Permanent Delegate, treat this token as fully custodial, where funds can be moved without consent. Monitor the token's holder distribution for significant decentralization and observe the pair's trading activity over a longer period to establish a track record.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 1/10 | High | The Dominion Silver (SILV) token is an SPL Token-2022 mint. It has an active Mint Authority at 6FtT3CBaXVArhd2C4egCsQb1f1NF3FAfA6xhXJXD8chR, enabling the creation of new tokens. A Freeze Authority is… |
| **Governance / Economics** | 1/10 | High | Economic stability is severely impacted by high holder concentration, with the top 10 token accounts holding 94.84% of the total supply, indicating a high risk of price volatility from large… |
| **Upgrades** | 2/10 | High | The token's mutability features present ongoing risks. The Mint Authority and Freeze Authority are both active, allowing for future changes to supply and account status. A Permanent Delegate is also… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 6FtT3CBaXVArhd2C4egCsQb1f1NF3FAfA6xhXJXD8chR. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is FqFNXCMeEYUD64tLPhvVzBAnovfYBAGsU8d6qdLnvzZ3. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

FqFNXCMeEYUD64tLPhvVzBAnovfYBAGsU8d6qdLnvzZ3 has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 94.84% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the high concentration when assessing market stability and potential price volatility.


### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 0 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution and monitor the token's performance and team activity over a longer period before making significant investments.


### `M-02` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Be aware that an authority exists which can modify token balances directly, potentially without user consent.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SiLVFM...B35L`](https://solscan.io/account/SiLVFMgD3eD2rgK628NbTBq9MnuJF5FW2CRaVyTB35L) |
| **Network** | Solana |
| **Price** | $64.3400 |
| **24h Volume** | $1.07M |
| **Liquidity** | $919.3K |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 19h |
| **Top-10 Holders** | 94.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 6418 buys / 5684 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hbufqhp3qkevbas1t4kgwazdu9yxlryyagppxpyk2x6t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dominion-silver-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*

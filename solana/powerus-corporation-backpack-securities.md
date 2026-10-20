---
token: Powerus Corporation - Backpack Securities
ticker: PUSA
network: solana
risk_score: 77
status: high
date: 2026-10-03
---

# Powerus Corporation - Backpack Securities (PUSA) — Smart Contract Security Analysis | Solana

> **Risk Score: 77/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/powerus-corporation-backpack-securities-sol)

---

## Audit Summary

This SPL Token Mint has critical centralized control risks. The mint authority, freeze authority, and a permanent delegate are all active, allowing the controlling entity to mint new tokens, freeze accounts, and transfer user funds without consent. Additionally, balance and metadata mutability are enabled. Holder distribution and pool liquidity lock status were unavailable for this assessment.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint authority and freeze authority have been revoked to prevent arbitrary supply increases or account freezing. Given the active permanent delegate, treat this token as fully custodial, as funds can be moved without consent. Monitor the controlling addresses for any unexpected activity, especially regarding token minting or account freezing.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is an SPL Token-2022 mint with a total supply of 138,102,755.900 PUSA (6 decimals). Critical centralized control is present with an active mint authority… |
| **Governance / Economics** | 1/10 | High | The token has a total DEX liquidity of $537,950, with a 24-hour trading volume of $2,766,234. The Volume/Liquidity Ratio is 5.14, indicating active trading relative to liquidity. The pair is very… |
| **Upgrades** | 1/10 | High | The token's mint authority and freeze authority remain active, allowing for potential changes to supply and account states. The permanent delegate is also active. Metadata is mutable, meaning the… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is DWvr3rVt8PesAfetQTQrRdTu26PrNA3VKDfhAwo82wBq. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** A balance-mutating authority can adjust user balances.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $724K (DexScreener, all pools). 24h trading volume $9.9M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $724K of DEX liquidity across 29 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`PUSAG1...m6hy`](https://solscan.io/account/PUSAG1stksTcAoK9MjinEHUwAYRJsbovywYCk37m6hy) |
| **Network** | Solana |
| **Price** | $3.2200 |
| **24h Volume** | $2.76M |
| **Liquidity** | $538.1K |
| **Volume / Liquidity** | 5.1× |
| **Token Age** | 18h |
| **Top-10 Holders** | N/A of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 8288 buys / 7918 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3d1puof9kcrb5td5umhiax8cbs6dz2bggfgkjioay7jb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/powerus-corporation-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*

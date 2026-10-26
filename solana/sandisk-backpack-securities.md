---
token: Sandisk - Backpack Securities
ticker: SNDK
network: solana
risk_score: 84
status: high
date: 2026-09-17
---

# Sandisk - Backpack Securities (SNDK) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/sandisk-backpack-securities-sol)

---

## Audit Summary

This SPL Token Mint exhibits critical security risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing for arbitrary token creation, account freezing, and fund confiscation. Additionally, over 70% of the supply is held by the top 10 accounts, posing a significant market manipulation risk. All available third-party registry data confirmed these risks.

> **Final Recommendation:** Before any interaction, verify on-chain that the Mint Authority has been revoked to ensure a fixed supply. Confirm the Freeze Authority is nullified to prevent account freezing. Given the Permanent Delegate authority, treat this token as fully custodial and understand that funds can be moved without consent. Monitor holder distribution for any reduction in concentration and be aware that metadata can change.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | This token is an SPL Token-2022 mint with a total supply of 1,168,354,486 tokens and 6 decimals. Critical authorities are active: a Mint Authority at umtnrdLnVDfqXgm9iTnU1jFphfEgYMTJRSgryahGWky can… |
| **Governance / Economics** | 1/10 | High | The token exhibits high holder concentration, with the top 10 accounts controlling 72.02% of the total supply, which presents a substantial risk of market manipulation or price crashes from large… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, allowing for changes to its name, symbol, or image post-launch. While no transfer hook is currently active, the transfer_hook_upgradable flag is true, meaning a… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 3 Critical · 🟠 1 High · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is umtnrdLnVDfqXgm9iTnU1jFphfEgYMTJRSgryahGWky. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

2cVYpagTt7ZGc3mmTXBa7fAznUtx5DUu6aCq8uVDaf4a has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

Top 10 token accounts hold 72.02% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the potential impact of large holder sell-offs on price stability.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority and its potential impact on token holdings.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.6% of supply. What remains: 70.6% in wallets, 0.0% in other contracts.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Sandisk (Backpack Securities) (SNDK), market cap $2M, rank #2453.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $132K (DexScreener, all pools). 24h trading volume $250K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $132K of DEX liquidity across 8 pools. Launch: 84 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`SNDKbw...RhfH`](https://solscan.io/account/SNDKbwMUQvZhnLnxLduradgLHG5KrPuKwpnrkkGRhfH) |
| **Network** | Solana |
| **Price** | $1,757.1700 |
| **24h Volume** | $250.1K |
| **Liquidity** | $120.7K |
| **Volume / Liquidity** | 2.1× |
| **Token Age** | 2mo |
| **Top-10 Holders** | 70.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2442 buys / 2602 sells |

## Security Flags (2/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ⚠️ Unknown |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/4vrc6qne8hpun98mjr88vrkrd9n4cadyrgtpwvu3cv86)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/sandisk-backpack-securities-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-17*

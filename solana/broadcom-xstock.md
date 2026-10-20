---
token: Broadcom xStock
ticker: AVGOX
network: solana
risk_score: 84
status: high
date: 2026-10-13
---

# Broadcom xStock (AVGOX) — Smart Contract Security Analysis | Solana

> **Risk Score: 84/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/broadcom-xstock-sol)

---

## Audit Summary

This SPL Token Mint presents critical risks due to multiple unrevoked authorities: the mint authority, freeze authority, and a permanent delegate that can move user funds. Furthermore, an independent third-party risk registry flags this token as high-risk. Holder concentration is also very high, with the top 10 holders controlling 94.45% of the supply. Information regarding pool liquidity locking was unavailable.

> **Final Recommendation:** Holders should immediately verify the on-chain status of the mint authority, freeze authority, and permanent delegate. Do not interact with this token unless these critical authorities are demonstrably revoked and the permanent delegate is unset. Monitor the top holder wallets for any significant movements, as their concentrated holdings pose a substantial risk. Given the high-risk flagging by a third-party registry, extreme caution is advised.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | This token is an SPL Token-2022 mint, indicating support for advanced features. However, the mint authority (7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj) remains active, allowing for unlimited new… |
| **Governance / Economics** | 1/10 | High | The token exhibits extremely high holder concentration, with the top 10 holders that can sell controlling 94.45% of the total supply, posing a significant risk of price manipulation or sudden dumps.… |
| **Upgrades** | 1/10 | High | The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. The mint authority and freeze authority are not revoked, allowing for future changes to supply and… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 4 Critical · 🟠 2 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `C-03` — Permanent Delegate Configured  *(Severity: Critical · Status: Unresolved)*

5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `C-04` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 94.45% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings.


### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; change any holder's balance (seize or credit tokens); freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Balance Mutability Authority  *(Severity: Medium · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority and verify its intended use case.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.1% of supply. Of that, 1.6% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 94.4% in wallets, 0.0% in other contracts. 7,084 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Broadcom xStock (AVGOX), market cap $7M, rank #1451. 7,084 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $593K (DexScreener, all pools). 24h trading volume $7.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $7.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $593K of DEX liquidity across 30 pools. Launch: 237 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsgSaS...PJGo`](https://solscan.io/account/XsgSaSvNSqLTtFuyWPBhK9196Xb9Bbdyjj4fH3cPJGo) |
| **Network** | Solana |
| **Price** | $354.8000 |
| **24h Volume** | $4.97M |
| **Liquidity** | $543.5K |
| **Volume / Liquidity** | 9.1× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 96.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 24608 buys / 23810 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ekpbwmpzrzfsv2xkjrdvws61arudbvdrjk7wqmctbfnb)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/broadcom-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-13*

---
token: SpaceX xStock
ticker: SPCXX
network: solana
risk_score: 8
status: low
date: 2026-09-20
---

# SpaceX xStock (SPCXX) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/spacex-xstock-sol)

---

## Audit Summary

This SPL Token Mint audit for SpaceX xStock (SPCXx) reveals critical security risks due to active administrative authorities. The mint authority, freeze authority, and a permanent delegate are all unrevoked, allowing for unlimited new token minting, account freezing, and direct fund transfers without consent. Additionally, 92.17% of the token supply is held by the top 10 accounts, indicating high centralization. Third-party registry data was available, but chain-native holder distribution details were not.

> **Final Recommendation:** Holders should verify on-chain that the mint authority, freeze authority, and permanent delegate are revoked before considering the token supply fixed or their funds secure. Due to the high holder concentration, monitor large transfers from top accounts for potential market impact. Be aware that metadata can be changed, so verify branding periodically against official sources. Given the active administrative controls, treat this token as fully custodial.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is implemented using the spl-token-2022 program. Critical administrative controls remain active: the mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj, the freeze authority is… |
| **Governance / Economics** | 9/10 | Low | The token exhibits very high holder concentration, with the top 10 accounts holding 92.17% of the total supply, posing a significant risk of price manipulation. Total DEX liquidity is $1,784,690… |
| **Upgrades** | 7/10 | Low | All primary administrative authorities (mint, freeze, permanent delegate) remain unrevoked, allowing for potential future changes to token parameters and supply. The token's metadata is mutable… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_⚪ 11 Informational_

### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is 7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Freeze Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The freeze authority is JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `I-03` — Permanent Delegate Configured  *(Severity: Informational · Status: Unresolved)*

5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `I-04` — Holder Concentration > 70%  *(Severity: Informational · Status: Unresolved)*

Top 10 token accounts hold 92.17% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant market impact potential from large holders. Monitor top holder movements closely.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify user balances. This introduces a custodial element.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 91.0% of supply. What remains: 91.0% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as SpaceX xStock (SPCXX), market cap $66M, rank #364. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Circle xStock: one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.7M (DexScreener, all pools). 24h trading volume $13.1M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.7M of DEX liquidity across 16 pools. Launch: 99 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

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

- [View on DexScreener](https://dexscreener.com/solana/ahnn6jmvagg6xuosg7ser38grydb2jtbuvqxvuqarhpq)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/spacex-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-20*

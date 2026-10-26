---
token: Gamestop xStock
ticker: GMEX
network: solana
risk_score: 12
status: low
date: 2026-09-22
---

# Gamestop xStock (GMEX) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/gamestop-xstock-sol)

---

## Audit Summary

This SPL Token-2022 mint exhibits critical centralization risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing the issuer to control supply and user funds. Additionally, over 96% of the token supply is held by the top 10 accounts, posing a significant market manipulation risk. Third-party registry data was available and confirmed these authority risks.

> **Final Recommendation:** Before any interaction, verify on-chain that the Mint Authority and Freeze Authority have been set to null to prevent arbitrary supply inflation or account freezing. Given the presence of a Permanent Delegate, treat this token as fully custodial, as funds can be moved without consent. Monitor the top holder distribution for any changes, as the current concentration poses a significant risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Gamestop xStock (GMEx) token is an SPL Token-2022 mint. It has an active Mint Authority at `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`, allowing for unlimited new token creation. A Freeze… |
| **Governance / Economics** | 9/10 | Low | The token exhibits very high holder concentration, with the top 10 token accounts holding 96.47% of the total supply. This level of concentration makes the token highly susceptible to price… |
| **Upgrades** | 7/10 | Low | The token's metadata is mutable, meaning its name, symbol, or image can be changed post-launch. The `transfer_hook_upgradable` flag is true, but no transfer hook is currently active. The Mint… |

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

Top 10 token accounts hold 96.47% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the significant risk of price manipulation due to concentrated holdings.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to arbitrarily change token balances.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.5% of supply. What remains: 96.5% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Gamestop xStock (GMEX), market cap $2M, rank #2315. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Circle xStock: one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $710K (DexScreener, all pools). 24h trading volume $3.3M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $710K of DEX liquidity across 17 pools. Launch: 43 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xsf9mB...PRGc`](https://solscan.io/account/Xsf9mBktVB9BSU5kf4nHxPq5hCBJ2j2ui3ecFGxPRGc) |
| **Network** | Solana |
| **Price** | $24.0350 |
| **24h Volume** | $3.35M |
| **Liquidity** | $437.5K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 96.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13873 buys / 14323 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hsqxf9l7tpwf1pkjwwsbnew2vytppgrfwwna4gq2n2x)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/gamestop-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-22*

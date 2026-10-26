---
token: Circle xStock
ticker: CRCLX
network: solana
risk_score: 10
status: low
date: 2026-08-14
---

# Circle xStock (CRCLX) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/circle-xstock-sol)

---

## Audit Summary

This audit identifies critical centralization risks for the Circle xStock (CRCLx) token due to active mint, freeze, and permanent delegate authorities, which allow for unlimited new token creation, account freezing, and unauthorized fund transfers. Additionally, a balance-mutating authority is present, and metadata can be changed. Holder concentration is moderate, with the top 10 accounts holding 64.54% of the supply. Third-party registry data indicates multiple high-risk flags, including enabled mint and freeze authorities and permanent control. Holder distribution data from chain-native RPC was unavailable.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the mint authority and freeze authority have been revoked to prevent supply dilution and account freezing. Confirm that the permanent delegate authority has been removed to ensure funds cannot be moved without consent. Monitor the token's metadata for any unexpected changes. Regularly check the holder distribution to assess changes in concentration and potential market manipulation risks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The Circle xStock (CRCLx) token operates on the spl-token-2022 program, indicating modern SPL token standards and extensions. However, significant centralized control exists. The mint authority… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a medium level of holder concentration, with the top 10 accounts holding 64.54% of the total supply. This concentration poses a risk of price volatility due to potential… |
| **Upgrades** | 7/10 | Low | The token's metadata is mutable, meaning its name, symbol, or image can be altered post-launch. While the transfer hook is not currently active, its upgradability is enabled. The mint authority and… |

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


### `I-04` — Holder Concentration > 50%  *(Severity: Informational · Status: Unresolved)*

Top 10 token accounts hold 64.54% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the potential impact of large holder movements on market price.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority on token supply and individual holdings.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 67.6% of supply. What remains: 67.6% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Circle xStock (CRCLX), market cap $107M, rank #264. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Tesla xStock: one issuer's programme, read on-chain. Verified by: CoinGecko, issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $4.5M (DexScreener, all pools). 24h trading volume $8.5M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $4.5M of DEX liquidity across 16 pools. Launch: 409 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsueG8...3bd1`](https://solscan.io/account/XsueG8BtpquVJX9LVLLEGuViXUungE6WmK5YZ3p3bd1) |
| **Network** | Solana |
| **Price** | $95.6700 |
| **24h Volume** | $8.51M |
| **Liquidity** | $2.75M |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1y |
| **Top-10 Holders** | 67.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2160 buys / 1700 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/g39wywqukbhk8f2wzzzfx3fcsyg91vccbbr6wevp5axy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/circle-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-14*

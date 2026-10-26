---
token: NVIDIA xStock
ticker: NVDAX
network: solana
risk_score: 8
status: low
date: 2026-08-11
---

# NVIDIA xStock (NVDAX) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/nvidia-xstock-sol)

---

## Audit Summary

The NVIDIA xStock (NVDAx) token mint has critical security risks due to unrevoked mint, freeze, and permanent delegate authorities, allowing the issuer to control supply and user funds. Additionally, holder concentration is very high, and metadata and balances can be mutated. Third-party registry data confirms these enabled controls.

> **Final Recommendation:** Before any interaction, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to ensure the supply is fixed and funds are secure from issuer control. Monitor the top holder accounts for any significant movements that could impact market stability. Be aware that token metadata can be changed, so confirm branding against official sources periodically.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is an SPL Token-2022 mint. It has a Mint Authority at `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`, allowing unlimited new token creation. A Freeze Authority at… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is very high, with the top 10 token accounts holding 82.03% of the total supply, posing a significant risk of price manipulation or sudden sell-offs. Liquidity is substantial at… |
| **Upgrades** | 7/10 | Low | The token's core authorities, including Mint Authority, Freeze Authority, and Permanent Delegate, remain unrevoked, granting the issuer extensive control over the token's supply and user funds. While… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_⚪ 11 Informational_

### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is `7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj`. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Freeze Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The freeze authority is `JDq14BWvqCRFNu1krb12bcRpbGtJZ1FLEakMw6FdxJNs`. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `I-03` — Permanent Delegate Configured  *(Severity: Informational · Status: Unresolved)*

`5aMNNLQJwAEeoemTEMkv5NVjqKwvvefRYCQ5Z67HFvEq` has permanent delegate authority and can transfer any holder's tokens without consent.

**Recommendation:** Treat this token as fully custodial.


### `I-04` — Holder Concentration > 70%  *(Severity: Informational · Status: Unresolved)*

Top 10 token accounts hold 82.03% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of an authority being able to modify user balances, as this grants significant control over token holdings.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 80.7% of supply. What remains: 80.7% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as NVIDIA xStock (NVDAX), market cap $47M, rank #473. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Circle xStock: one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $3.1M (DexScreener, all pools). 24h trading volume $8.6M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $3.1M of DEX liquidity across 22 pools. Launch: 405 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`Xsc9qv...9qEh`](https://solscan.io/account/Xsc9qvGR1efVDFGLrVsmkzv3qi45LTBjeUKSPmx9qEh) |
| **Network** | Solana |
| **Price** | $227.2100 |
| **24h Volume** | $8.59M |
| **Liquidity** | $2.48M |
| **Volume / Liquidity** | 3.5× |
| **Token Age** | 1y |
| **Top-10 Holders** | 80.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 7025 buys / 6440 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/49imatqtoyabsyaqc8gafvq6aebfvdxsrh44oiatyyw6)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/nvidia-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-11*

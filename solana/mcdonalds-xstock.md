---
token: McDonald's xStock
ticker: MCDX
network: solana
risk_score: 12
status: low
date: 2026-09-15
---

# McDonald's xStock (MCDX) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/mcdonalds-xstock-sol)

---

## Audit Summary

This SPL Token Mint exhibits multiple critical security risks. The mint authority, freeze authority, and a permanent delegate are all active, allowing the issuer to mint new tokens, freeze accounts, and transfer user funds without consent. Furthermore, a third-party risk registry has flagged this token as high-risk due to these enabled authorities and extremely high holder concentration. Holder concentration is 98.51% for the top 10 accounts, posing a significant market manipulation risk. Third-party registry data was available, but chain-native holder distribution details were not.

> **Final Recommendation:** Holders should immediately verify the on-chain status of the mint authority, freeze authority, and permanent delegate. Do not interact with this token unless these critical authorities are irrevocably revoked to prevent dilution, account freezing, or unauthorized fund transfers. Given the extreme holder concentration and the third-party high-risk flagging, consider this token highly speculative and prone to significant price volatility. Monitor on-chain for any changes to authority statuses or large movements from top holders before making any investment decisions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | This token is an SPL Token-2022 mint, indicating it uses the latest Solana token program features. Critical authorities remain active: the mint authority… |
| **Governance / Economics** | 9/10 | Low | The economic stability of this token is severely compromised by extreme holder concentration, with the top 10 accounts holding 98.51% of the total supply. This level of concentration creates a high… |
| **Upgrades** | 7/10 | Low | The token's metadata is mutable, meaning the name, symbol, or image can be changed post-launch, which could lead to branding confusion. While the token program itself is spl-token-2022, the critical… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🔴 1 Critical · ⚪ 11 Informational_

### `C-04` — Flagged High-Risk by Third-Party Registry  *(Severity: Critical · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements), citing enabled Mint Authority, Permanent Control, Freeze Authority, and high ownership concentration.

**Recommendation:** Do not interact with this token.


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

Top 10 token accounts hold 98.51% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the high concentration risk in any investment decision.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand the implications of a balance-mutating authority and verify its revocation if not desired.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 96.7% of supply. What remains: 96.7% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as McDonald's xStock (MCDX), market cap $2M, rank #2242. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Circle xStock: one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $528K (DexScreener, all pools). 24h trading volume $480K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $528K of DEX liquidity across 10 pools. Launch: 373 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsqE9c...AWT2`](https://solscan.io/account/XsqE9cRRpzxcGKDXj1BJ7Xmg4GRhZoyY1KpmGSxAWT2) |
| **Network** | Solana |
| **Price** | $252.7100 |
| **24h Volume** | $480.3K |
| **Liquidity** | $218.1K |
| **Volume / Liquidity** | 2.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 96.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3192 buys / 2723 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/5mgvnj9rnknmzwp1ltzuqkzoneytkj3juiynqeuu2dsf)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/mcdonalds-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-15*

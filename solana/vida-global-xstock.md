---
token: Vida Global xStock
ticker: VIDAX
network: solana
risk_score: 8
status: low
date: 2026-09-05
---

# Vida Global xStock (VIDAX) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vida-global-xstock-sol)

---

## Audit Summary

This SPL Token Mint presents critical risks due to active Mint, Freeze, and Permanent Delegate authorities, allowing for unlimited minting, account freezing, and direct fund confiscation. Additionally, 99.73% of the supply is held by the top 10 accounts, posing a significant centralization risk. Third-party registry data confirms these authority risks. Holder distribution data from chain-native RPC was unavailable, but GoPlus data provided top holder concentration.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority, Freeze Authority, and Permanent Delegate have been revoked to prevent arbitrary supply changes, account freezing, or fund confiscation. Monitor the token's holder distribution for decentralization improvements and observe market behavior as the DEX pair matures beyond its current 4-day age. Confirm the token's metadata against official sources to ensure branding consistency, given its mutability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token is an SPL Token-2022 mint, indicating support for advanced extensions. However, the Mint Authority (7pt9tkctJPK7PPNQJ77GKg8ZffSF6QxoMiCFYHxrtaCj) remains active, allowing for arbitrary… |
| **Governance / Economics** | 9/10 | Low | Holder concentration is extremely high, with the top 10 token accounts controlling 99.73% of the total supply, creating significant centralization risk. The token's DEX pair is very new, established… |
| **Upgrades** | 7/10 | Low | The token's core authorities, including Mint Authority and Freeze Authority, are not revoked, allowing for future changes to supply and account status. The Permanent Delegate authority is also… |

## Token-2022 Extensions

| Extension | Value |
|-----------|-------|
| **Permanent Delegate** | ⚠️ Set (any holder can be force-burned) |

## Security Findings

_🟡 1 Medium · ⚪ 12 Informational_

### `M-01` — Very New Pair  *(Severity: Medium · Status: Unresolved)*

DEX pair was created 4 days ago. Insufficient track record to assess team or holder behaviour.

**Recommendation:** Exercise caution due to the limited operational history of the DEX pair.


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

Top 10 token accounts hold 99.73% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Be aware of the significant market manipulation risk due to extreme holder concentration.


### `I-05` — Balance Mutability Authority  *(Severity: Informational · Status: Unresolved)*

A balance-mutating authority can adjust user balances.

**Recommendation:** Understand who controls the balance-mutating authority and its intended use before holding the token.


### `I-06` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 99.2% of supply. What remains: 99.2% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Vida Global xStock (VIDAX), rank #4547. Its mint authority (7pt9tk…taCj) controls 109 issuer-backed coins CoinGecko lists on solana, $923M together, among them Strategy PP Variable xStock, MicroStrategy xStock, Circle xStock: one issuer's programme, read on-chain. Verified by: issuer programme.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $111K (DexScreener, all pools). 24h trading volume $68K (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Tokenized real-world asset  *(Severity: Informational · Status: Acknowledged)*

A token backed by an off-chain asset (a stock, gold, treasury bills, a fund share) held by a named issuer or custodian. Issuance, redemption and transfer restrictions are the issuer's by design. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized Stocks. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $111K of DEX liquidity across 10 pools. Launch: 4 days of market history.

**Recommendation:** Treat the issuer or custodian as the counterparty: check its custody reports and who may hold or redeem the token.


### `QA-RECENT` — Recently launched — 4 days of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is 4 days old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`XsfCC9...zmTk`](https://solscan.io/account/XsfCC9VL4DamVGNgdJpfLXB3sBVa158Gbx8sh7NzmTk) |
| **Network** | Solana |
| **Price** | $1.8800 |
| **24h Volume** | $67.9K |
| **Liquidity** | $49.5K |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 4d |
| **Top-10 Holders** | 99.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2090 buys / 1943 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/edbmuqjwzwp8dxe7gwdtfsbsecr2hetyws8hxv2no95t)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vida-global-xstock-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-05*

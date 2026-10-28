---
token: EURC
ticker: EURC
network: solana
risk_score: 12
status: low
date: 2026-10-28
---

# EURC (EURC) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/eurc-sol)

---

## Audit Summary

The EURC token mint retains active mint and freeze authorities, posing significant centralization risks to holders. Holder concentration exceeds 70%, indicating potential for high price volatility. Third-party registry data indicates no adverse flags, though liquidity lock status remains unverified.

> **Final Recommendation:** Holders should monitor the mint and freeze authority addresses for potential revocation transactions. Given the high holder concentration, users should be prepared for significant price volatility during large sell-offs.

Verify the liquidity lock status via on-chain explorers to ensure the pool creator cannot withdraw the $393k liquidity. Do not treat this token as a fixed-supply asset until the mint authority is set to null.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for SPL mints. 7.3 Access Control is currently centralized, as both the mint authority (Hy9168...) and freeze… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis shows a holder concentration of 72.28% among the top 10 wallets, triggering a high-risk concentration warning. 7.5 Governance is centralized due to the active authorities. 7.6… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints in the EVM sense, but 7.8 Operations are affected by the metadata mutability flag. The token metadata is currently mutable, allowing for potential… |

## Security Findings

_⚪ 9 Informational_

### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is Hy9168u7b2Toujh8SJKtKK8DWbyaBbXPzxm337R4o4XY. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Freeze Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The freeze authority is 6FF2CPcL6fat16QVJH6W27DeBcX7TSqbwY3a5wtyVJLC. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `I-03` — Holder Concentration > 70%  *(Severity: Informational · Status: Unresolved)*

The ten largest holders that can sell hold 72.28% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top wallet activity for signs of coordinated liquidation.


### `I-04` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 72.3% of supply. What remains: 72.3% in wallets, 0.0% in other contracts. 57,468 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as EURC (EURC), market cap $486M, rank #112. On GoPlus's list of trusted tokens. 57,468 holders. Verified by: CoinGecko, GoPlus.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $545K (DexScreener, all pools). 24h trading volume $32.9M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; freeze or blacklist individual addresses; change the token's name, symbol and image. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Stablecoin  *(Severity: Informational · Status: Acknowledged)*

A token designed to hold a fixed value (usually $1). Its safety rests on what backs it and on who can mint, freeze or pause it. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: EUR Stablecoin. Tokenomics — Supply: issued and redeemed by the issuer against its backing. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $545K of DEX liquidity across 30 pools. Launch: 1045 days of market history.

**Recommendation:** Check what backs the peg and who controls supply: reserve attestations for an issuer-backed coin, collateral and governance for a protocol coin.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`HzwqbK...DKtr`](https://solscan.io/account/HzwqbKZw8HxMN6bF2yFZNrht3c2iXXzpKcFu7uBEDKtr) |
| **Network** | Solana |
| **Price** | $1.1100 |
| **24h Volume** | $1.20M |
| **Liquidity** | $393.3K |
| **Volume / Liquidity** | 3.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 72.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 2424 buys / 2662 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/arisqncbjxpjd7rgprvysatx3xcfhptbctkfd8kdoz9i)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/eurc-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-28*

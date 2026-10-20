---
token: Doodles
ticker: DOOD
network: solana
risk_score: 35
status: medium
date: 2026-09-29
---

# Doodles (DOOD) — Smart Contract Security Analysis | Solana

> **Risk Score: 35/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/doodles-sol)

---

## Audit Summary

The Doodles (DOOD) SPL token mint exhibits a high concentration of supply among its top holders, with 70.86% held by the top 10 wallets and program accounts that can sell. Additionally, the token's metadata is mutable, allowing for changes to its name, symbol, or image post-launch. Third-party risk registry data was available and flagged these specific concerns.

> **Final Recommendation:** Prospective holders should monitor the distribution of the token closely, as the current high concentration among top holders poses a significant risk of market volatility. Before relying on the token's branding, verify its current metadata (name, symbol, image) on-chain, as it can be changed. While core minting and freezing authorities are revoked, the mutable metadata introduces an element of uncertainty regarding the token's long-term identity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Doodles (DOOD) token is an SPL token operating under the `spl-token` program. Both the Mint Authority and Freeze Authority have been revoked, indicating that no new tokens can be minted and no… |
| **Governance / Economics** | 1/10 | High | A significant economic risk is the high concentration of token supply, with the top 10 holders that can sell controlling 70.86% of the total supply. This level of concentration makes the token… |
| **Upgrades** | 8/10 | Low | The token's core authorities, Mint Authority and Freeze Authority, have been permanently revoked, preventing any future changes to the token's supply or the ability to freeze holder accounts. The… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 100.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_🟠 1 High · 🟢 1 Low · ⚪ 6 Informational_

### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 70.86% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Exercise caution due to the high concentration of tokens. Monitor the activity of large holders and consider the potential impact of significant sell-offs on market price.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding. Be aware that the token's visual identity or descriptive information could change.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 70.9% of supply. What remains: 41.9% in wallets, 29.0% in other contracts. 110,314 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Doodles (DOOD), market cap $14M, rank #1098. 110,314 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity protection could not be verified  *(Severity: Informational · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. Solana LP holders are anonymous in the data we read, so who can withdraw the remaining liquidity cannot be verified. This assessment covers the main pool, which holds 75% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $695K (DexScreener, all pools). 24h trading volume $10.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $166K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.0175 on 2025-10-06; the price is now 90.0111% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $695K of DEX liquidity across 14 pools. Launch: 507 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DvjbEs...XvgV`](https://solscan.io/account/DvjbEsdca43oQcw2h3HW1CT7N3x5vRcr3QrvTUHnXvgV) |
| **Network** | Solana |
| **Price** | $0.001797 |
| **24h Volume** | $130.0K |
| **Liquidity** | $524.1K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 70.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1108 buys / 882 sells |

## Security Flags (3/4 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/solana/5kxe8rmf7iw9ptn665ahfzsmfjyb4lv2ta8ezetstwwc)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/doodles-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-29*

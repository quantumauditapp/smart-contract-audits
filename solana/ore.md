---
token: ORE
ticker: ORE
network: solana
risk_score: 36
status: medium
date: 2026-10-01
---

# ORE (ORE) — Smart Contract Security Analysis | Solana

> **Risk Score: 36/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/ore-sol)

---

## Audit Summary

The ORE token mint presents critical risks due to an unrevoked mint authority, allowing for unlimited new token creation. Additionally, over 50% of the sellable supply is concentrated among the top ten holders, and the token's metadata can be altered post-launch. Information regarding the locking status of the pool's liquidity was unavailable from the provided sources.

> **Final Recommendation:** Before engaging with this token, verify on-chain that the mint authority has been permanently revoked to ensure the supply is fixed. Monitor the top holder addresses for any significant movements that could indicate an impending sell-off. Additionally, confirm the token's metadata against official sources to ensure its branding remains consistent with expectations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ORE token is an SPL token operating on the Solana network, managed by the `spl-token` program. A significant technical risk is the active mint authority… |
| **Governance / Economics** | 7/10 | Low | The token exhibits a notable holder concentration, with the top 10 holders that can sell controlling 51.43% of the total supply. This concentration poses a risk of market manipulation or significant… |
| **Upgrades** | 5/10 | Medium | The mint authority for the ORE token remains active, allowing for potential changes to the token's supply dynamics. While the freeze authority has been revoked, the token's metadata, including its… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is BiN8KJqtGanTmHzgTyJA3ALwLaqygt5KzRydH7gX5rf4. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 51.43% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings. Monitor large holder wallets for unusual activity.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 51.4% of supply. What remains: 0.0% in wallets, 51.4% in other contracts. 33,978 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as ORE (ORE), market cap $62M, rank #413. 33,978 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.3M (DexScreener, all pools). 24h trading volume $2.8M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.6M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $1,451.62 on 2024-07-29; the price is now 91.4029% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.3M of DEX liquidity across 30 pools. Launch: 789 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`oreoU2...ybcp`](https://solscan.io/account/oreoU2P8bN6jkk3jbaiVxYnG1dCXcYxwhwyK9jSybcp) |
| **Network** | Solana |
| **Price** | $104.6900 |
| **24h Volume** | $597.8K |
| **Liquidity** | $531.7K |
| **Volume / Liquidity** | 1.1× |
| **Token Age** | 2y |
| **Top-10 Holders** | 51.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1111 buys / 1867 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/c7hf6mvqwerhsf1krfvnkzdarb9psoffiwzdipo9c7cz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/ore-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-01*

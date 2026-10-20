---
token: Render Token
ticker: RENDER
network: solana
risk_score: 49
status: medium
date: 2026-10-14
---

# Render Token (RENDER) — Smart Contract Security Analysis | Solana

> **Risk Score: 49/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/render-token-sol)

---

## Audit Summary

This audit of the Render Token (RENDER) SPL token mint reveals critical security risks due to the active Mint Authority and Freeze Authority, allowing the respective key holders to mint new tokens or freeze existing accounts. Additionally, over 50% of the sellable supply is concentrated among the top ten holders, posing a market manipulation risk. Third-party risk registry data and chain-native RPC data were successfully collected, but information regarding pool liquidity locking was unavailable.

> **Final Recommendation:** Before engaging with this token, verify on-chain that the Mint Authority has been revoked to ensure a fixed supply. Monitor the Freeze Authority's address for any activity and confirm its revocation if you require unrestricted transferability. Given the holder concentration, observe the wallets of the top holders for any large movements that could impact market stability.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The Render Token is an SPL token operating under the `spl-token` program. It has an active Mint Authority at `CFyeujXVymxgP2YR9kLbPsaCv2rKrtXMWtJ3EbAN2pdc`, enabling the creation of new tokens, and a… |
| **Governance / Economics** | 1/10 | High | Economic analysis indicates a medium risk due to holder concentration, with the top 10 holders that can sell controlling 52.46% of the total supply, which could lead to significant price volatility… |
| **Upgrades** | 2/10 | High | The token's metadata is mutable, meaning its name, symbol, or image can be altered post-launch, as indicated by `metadata_mutable: True`. Both the Mint Authority and Freeze Authority are active… |

## Security Findings

_🔴 2 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is CFyeujXVymxgP2YR9kLbPsaCv2rKrtXMWtJ3EbAN2pdc. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `C-02` — Freeze Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The freeze authority is 3LNxAhNnQpbCPcvgiamZhUbBugZTzxbjhcMwJ5jE65r5. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `M-01` — Holder Concentration > 50%  *(Severity: Medium · Status: Unresolved)*

The ten largest holders that can sell hold 52.46% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the potential impact of large holder movements on market stability.


### `QA-POWERS` — What the token's controller can do  *(Severity: Medium · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; freeze or blacklist individual addresses; change the token's name, symbol and image. Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `L-01` — Mutable Metadata  *(Severity: Low · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch, as indicated by `metadata_mutable: True`.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 52.5% of supply. What remains: 30.5% in wallets, 22.0% in other contracts. 126,539 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Render (RENDER), market cap $1.1B, rank #78. 126,539 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $908K (DexScreener, all pools). 24h trading volume $119.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $908K of DEX liquidity across 30 pools. Launch: 1072 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`rndriz...HBof`](https://solscan.io/account/rndrizKT3MK1iimdxRdWabcF7Zg7AR5T4nud4EkHBof) |
| **Network** | Solana |
| **Price** | $1.9800 |
| **24h Volume** | $1.18M |
| **Liquidity** | $455.8K |
| **Volume / Liquidity** | 2.6× |
| **Token Age** | 2y |
| **Top-10 Holders** | 52.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 4060 buys / 4826 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/fz8mjvdtpbp8juhtfcczb7lskunhexgzshgq59sujknl)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/render-token-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-14*

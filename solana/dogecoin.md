---
token: Dogecoin
ticker: DOGE
network: solana
risk_score: 98
status: critical
date: 2026-10-23
---

# Dogecoin (DOGE) — Smart Contract Security Analysis | Solana

> **Risk Score: 98/100 — 🔴 Critical Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/dogecoin-sol)

---

## Audit Summary

The token mint is currently controlled by an active mint authority, posing a significant risk of supply dilution. While the freeze authority is revoked, the metadata remains mutable and liquidity status is unverified, presenting potential operational risks. Third-party registry data indicates concerns regarding developer control and liquidity management.

> **Final Recommendation:** Investors should monitor the mint authority address for potential revocation. Verify the status of liquidity locks through on-chain explorers to ensure that the pool creator cannot withdraw the $232,930 in liquidity. 

Before interacting with this token, confirm that the current metadata matches your expectations, as the mutable metadata flag allows for branding changes. Do not treat the supply as fixed until the mint authority is set to null.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 4/10 | Medium | The token is initialized on the standard SPL Token program. The mint authority is currently held by address FCBW5Xs4grHRpDPtfEgtYrBc97QSwBvKUxwJkbt3ZdJZ, allowing for unlimited token creation. The… |
| **Governance / Economics** | 4/10 | Medium | The top 10 holders that can sell control 25.94% of the supply, indicating moderate concentration. Liquidity is $232,930 with a healthy volume/liquidity ratio of 0.79. The status of liquidity locks… |
| **Upgrades** | 4/10 | Medium | SPL token mints do not support upgrade patterns. Metadata is currently mutable, allowing the token name, symbol, or image to be changed by the owner. No other extensions are active. |

## Security Findings

_🔴 2 Critical · 🟡 2 Medium · 🟢 1 Low · ⚪ 4 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is FCBW5Xs4grHRpDPtfEgtYrBc97QSwBvKUxwJkbt3ZdJZ. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `QA-IDENTITY` — Imitation of Dogecoin (DOGE)  *(Severity: Critical · Status: Acknowledged)*

Presents itself as Dogecoin (DOGE), but CoinGecko lists no Dogecoin contract on solana at all (CoinGecko). Holders who think they own the real asset own this contract instead; it has none of the real asset's backing, liquidity or redemption.

**Recommendation:** Do not buy, hold or accept this token as the asset it names. Verify any token address against the issuer's official site.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `M-02` — Flagged High-Risk by Third-Party Registry  *(Severity: Medium · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `L-01` — Pool Liquidity Not Locked  *(Severity: Low · Status: Unresolved)*

The fact block indicates that liquidity status is unverified and third-party registries flag large amounts of unlocked LP.

**Recommendation:** Monitor the pool creator's wallet for liquidity removal.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 46.5% of supply. Of that, 28.5% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.1% in wallets, 5.9% in other contracts. 41,150 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $565K (DexScreener, all pools). 24h trading volume $6.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Imitation of Dogecoin (DOGE)  *(Severity: Informational · Status: Acknowledged)*

A token presenting itself under the name or ticker of an established asset without being that asset's contract. Its only reason to borrow that identity is to be mistaken for it. Scored as an imitation (see the identity finding). Basis: meme vocabulary in name/ticker (doge); launched on pump.fun (PumpSwap), a meme launchpad; behaves as: meme token. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $565K of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 46 days of market history.

**Recommendation:** Do not treat this token as the asset it names. Use only the official contract address published by that asset's issuer.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`DoGEV7...fm7R`](https://solscan.io/account/DoGEV7LASBkQbibMc5k5vKnTZoMg423GpJ5QtJEGfm7R) |
| **Network** | Solana |
| **Price** | $0.07997 |
| **24h Volume** | $184.2K |
| **Liquidity** | $232.4K |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1mo |
| **Top-10 Holders** | 46.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1278 buys / 1369 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/7s9gwyhhtmszppzytlaudfw3lyfus6xcnfwrgquk5x4n)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/dogecoin-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-23*

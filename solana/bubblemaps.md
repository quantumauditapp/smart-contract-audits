---
token: Bubblemaps
ticker: BMT
network: solana
risk_score: 72
status: high
date: 2026-10-24
---

# Bubblemaps (BMT) — Smart Contract Security Analysis | Solana

> **Risk Score: 72/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/bubblemaps-sol)

---

## Audit Summary

The Bubblemaps (BMT) token maintains an active mint authority, allowing for unlimited supply expansion. Holder concentration is high, with the top 10 holders controlling 73.23% of the circulating supply. Metadata remains mutable, and third-party registry data indicates potential risks regarding developer control.

> **Final Recommendation:** Investors should monitor the mint authority address for potential revocation. Given the high holder concentration, users should be aware of the risk of significant price volatility from large wallet movements.

Verify the current mint authority status using a block explorer to ensure no unexpected supply increases occur. Exercise caution regarding the mutable metadata, as the token's identity could be altered by the current owner.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard spl-token program. 7.1 Architecture is standard for SPL tokens. 7.3 Access Control is currently compromised by an active mint authority… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic analysis shows high concentration, with the top 10 holders controlling 73.23% of supply. 7.5 Governance is centralized due to the mint authority. Liquidity is $603,661 with a healthy… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints in the EVM sense, but metadata mutability allows for branding changes. The freeze authority is successfully revoked, preventing account freezing. Mint… |

## Security Findings

_🔴 1 Critical · 🟠 1 High · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is 9xNEePFZEiSW4V8UMpg2JHREw6pJBM1ZHc8qkWvQK8Ys. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `H-01` — Holder Concentration > 70%  *(Severity: High · Status: Unresolved)*

The ten largest holders that can sell hold 73.23% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Monitor top holder wallets for large outflows.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset.

**Recommendation:** Do not interact with this token if you are risk-averse.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.5% of supply. Of that, 1.3% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 53.4% in wallets, 19.8% in other contracts. 5,937 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Bubblemaps (BMT), market cap $21M, rank #806. 5,937 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.1M (DexScreener, all pools). 24h trading volume $57.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.2M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.317 on 2025-03-18; the price is now 91.1272% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.1M of DEX liquidity across 9 pools. Launch: 591 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`FQgtfu...ErhY`](https://solscan.io/account/FQgtfugBdpFN7PZ6NdPrZpVLDBrPGxXesi4gVu3vErhY) |
| **Network** | Solana |
| **Price** | $0.06759 |
| **24h Volume** | $1.46M |
| **Liquidity** | $608.7K |
| **Volume / Liquidity** | 2.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 74.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 865 buys / 1891 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ccxk5ixhdz4uxcyqrgkx6vbur4wacu6fw7kfkuvazdmy)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/bubblemaps-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

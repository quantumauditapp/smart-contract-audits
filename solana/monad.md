---
token: Monad
ticker: MON
network: solana
risk_score: 67
status: high
date: 2026-10-24
---

# Monad (MON) — Smart Contract Security Analysis | Solana

> **Risk Score: 67/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/monad-sol)

---

## Audit Summary

The Monad (MON) token mint retains an active mint authority, posing a significant risk of supply inflation. While the freeze authority is revoked, the metadata remains mutable, allowing for potential branding changes. Third-party registry data confirms these risks, though no honeypot behavior was detected.

> **Final Recommendation:** Holders should monitor the mint authority address for potential revocation. Verify the token metadata on-chain before performing large transactions to ensure the branding has not been altered.

Investors should treat the token as potentially inflationary until the mint authority is set to null. No further on-chain actions are required for the freeze authority, as it is already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for SPL mints. 7.3 Access Control is currently compromised by an active mint authority… |
| **Governance / Economics** | 6/10 | Medium | 7.4 Economic metrics show a healthy liquidity of $176,796 with a 4.33 volume/liquidity ratio. 7.5 Governance is decentralized with the top 10 holders controlling 25.11% of the supply. 7.6 External… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are not applicable to SPL mints, but 7.3 Access Control remains a concern due to the mutable metadata. The token name and symbol can be altered by the current authority. No other… |

## Security Findings

_🔴 1 Critical · 🟡 1 Medium · 🟢 1 Low · ⚪ 5 Informational_

### `C-01` — Mint Authority Not Revoked  *(Severity: Critical · Status: Unresolved)*

The mint authority is GJF9Xwoi9fdjM3dekeLWERsJAEmnWQPG7AZ3rxi19NX2. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `M-01` — Mutable Metadata  *(Severity: Medium · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset.

**Recommendation:** Do not interact with this token.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 33.8% of supply. Of that, 8.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 19.3% in wallets, 5.9% in other contracts. 8,726 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Listed, but not independently verified  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Wrapped MON (WMON), market cap $9M. 8,726 holders.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $163K (DexScreener, all pools). 24h trading volume $763K (CoinGecko, all markets, daily snapshot). 24h trading volume $867K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. Ownership is renounced, so nobody can use them now.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. The class itself adds no points; the contract and market facts decide the score. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $163K of DEX liquidity across 30 pools. Launch: 334 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`CrAr4R...reP2`](https://solscan.io/account/CrAr4RRJMBVwRsZtT62pEhfA9H5utymC2mVx8e7FreP2) |
| **Network** | Solana |
| **Price** | $0.02112 |
| **24h Volume** | $405.2K |
| **Liquidity** | $94.6K |
| **Volume / Liquidity** | 4.3× |
| **Token Age** | 11mo |
| **Top-10 Holders** | 33.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 3496 buys / 3138 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/14k3bm1fa6gn4f9x1h5e9urimzzy2xyz3fq72bl628un)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/monad-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-24*

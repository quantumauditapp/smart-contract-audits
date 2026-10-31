---
token: Phantom Staked SOL
ticker: PSOL
network: solana
risk_score: 12
status: low
date: 2026-10-31
---

# Phantom Staked SOL (PSOL) — Smart Contract Security Analysis | Solana

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/phantom-staked-sol-sol)

---

## Audit Summary

The token utilizes the standard SPL Token program with a revoked freeze authority, providing a stable foundation for holders. The primary risks identified are the active mint authority and mutable metadata. Third-party risk registry data was unavailable for this assessment.

> **Final Recommendation:** Users should monitor the mint authority address (2zeXA69dFoMLFLdzCfcff35aL7Y7uBZnjKBGWtESgVfS) for any unexpected minting activity. Verify the token metadata on-chain before performing large transactions to ensure the branding remains consistent with expectations.

Investors should treat the token as potentially inflationary until the mint authority is set to null. No further action is required regarding freeze authority as it is already revoked.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed on the standard SPL Token program (7.1 Architecture). The freeze authority is successfully revoked (7.3 Access Control), preventing account freezing. However, the mint authority… |
| **Governance / Economics** | 9/10 | Low | The token exhibits healthy market metrics with $1.36M in liquidity and a stable volume/liquidity ratio of 0.82 (7.4 Economic). Holder concentration is low, with the top 10 holders controlling only… |
| **Upgrades** | 10/10 | Low | The token metadata is currently mutable, allowing for potential changes to the name or symbol (7.7 Upgrades). There are no upgradeable proxy patterns or transfer hooks present (7.7 Upgrades). The… |

## Security Findings

_⚪ 7 Informational_

### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is 2zeXA69dFoMLFLdzCfcff35aL7Y7uBZnjKBGWtESgVfS. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 17.4% of supply. What remains: 13.9% in wallets, 3.5% in other contracts. 114,779 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Phantom Staked SOL (PSOL), market cap $155M. 114,779 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.4M (DexScreener, all pools). 24h trading volume $176K (CoinGecko, all markets, daily snapshot). 24h trading volume $1.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Liquid staking token  *(Severity: Informational · Status: Acknowledged)*

A receipt for staked native tokens that keeps earning staking rewards. Its value depends on the staking protocol and its validators. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Liquid Staking Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.4M of DEX liquidity across 30 pools. Launch: 541 days of market history.

**Recommendation:** Check the staking protocol's validator set, withdrawal queue and governance.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`pSo1f9...RQfL`](https://solscan.io/account/pSo1f9nQXWgXibFtKf7NWYxb5enAM4qfP6UJSiXRQfL) |
| **Network** | Solana |
| **Price** | $106.6900 |
| **24h Volume** | $1.10M |
| **Liquidity** | $1.37M |
| **Volume / Liquidity** | 0.8× |
| **Token Age** | 1y |
| **Top-10 Holders** | 17.4% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 16423 buys / 11719 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/3xlkrvg69agwkabnsjjpm3pb4qgvexfejixfw5shwmbt)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/phantom-staked-sol-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

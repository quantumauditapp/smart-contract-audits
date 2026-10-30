---
token: TRON
ticker: TRX
network: solana
risk_score: 9
status: low
date: 2026-10-30
---

# TRON (TRX) — Smart Contract Security Analysis | Solana

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tron-sol)

---

## Audit Summary

The token utilizes the standard SPL Token program. The primary security risks identified are the active mint authority, which allows for supply inflation, and mutable metadata. Third-party registry data indicates concerns regarding developer control and holder concentration.

> **Final Recommendation:** Monitor the mint authority address for potential revocation. Holders should verify the metadata on-chain before interacting to ensure the branding has not been altered.

Verify the current mint authority's activity on-chain. If the token is intended to be fixed-supply, the mint authority should be set to null to eliminate inflation risk.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token is deployed using the standard spl-token program. 7.1 Architecture follows the standard mint account structure. 7.3 Access Control is currently centralized as the mint authority is held by… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic analysis shows the top 10 holders that can sell control 30.41% of the supply. 7.6 External market data indicates a liquidity of $13,100,337 with a stable volume/liquidity ratio of 1.18.… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but 7.8 Operations are affected by the mutable metadata flag. The token name and symbol can be modified by the current authority. The freeze authority is… |

## Security Findings

_🟢 1 Low · ⚪ 7 Informational_

### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset (developer history, LP movements).

**Recommendation:** Do not interact with this token.


### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is 2qzoaECQaWkGariCaJdTuwZP7WaNUNdykqGVx6K8SZLV. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 98.3% of supply. Of that, 67.8% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 16.8% in wallets, 13.6% in other contracts. 10,293 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Solana Bridged TRX (Solana) (TRX), market cap $17M. 10,293 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $15.9M (DexScreener, all pools). 24h trading volume $765K (CoinGecko, all markets, daily snapshot). 24h trading volume $15.5M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — nobody (ownership renounced) — mint new supply; change the token's name, symbol and image. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Bridged-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: nobody (ownership renounced). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $15.9M of DEX liquidity across 30 pools. Launch: launched on pump.fun (PumpSwap), 588 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`GbbesP...LkKc`](https://solscan.io/account/GbbesPbaYh5uiAZSYNXTc7w9jty1rpg3P9L4JeN4LkKc) |
| **Network** | Solana |
| **Price** | $0.36 |
| **24h Volume** | $15.40M |
| **Liquidity** | $13.12M |
| **Volume / Liquidity** | 1.2× |
| **Token Age** | 1y |
| **Top-10 Holders** | 98.3% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 13374 buys / 13754 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/hpgv2jnzgrgfrzjezgkhgtnegrfahtzcvuk3brftfjwk)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tron-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

---
token: Wrapped XRP
ticker: WXRP
network: solana
risk_score: 8
status: low
date: 2026-10-27
---

# Wrapped XRP (WXRP) — Smart Contract Security Analysis | Solana

> **Risk Score: 8/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/wrapped-xrp-sol)

---

## Audit Summary

The token mint maintains active Mint and Freeze authorities, posing significant centralization risks to supply and holder access. Third-party registry data indicates concerns regarding metadata mutability and authority status. Holder concentration is moderate, and liquidity is sufficient, though the lock status of the pool liquidity remains unverified.

> **Final Recommendation:** Users should monitor the mint and freeze authorities for potential revocation. Verify the liquidity lock status on the specific DEX platform to ensure pool creator withdrawal risks are mitigated.

Before interacting, confirm that the metadata matches the expected branding, as the current configuration allows for post-launch modifications.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The token utilizes the standard SPL Token program (v3). 7.1 Architecture is standard for SPL mints, while 7.2 Code Security relies on the audited core program. 7.3 Access Control is currently… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic factors show a healthy volume/liquidity ratio of 3.43. 7.5 Governance is centralized, with the top 10 holders controlling 34.11% of the supply. 7.6 External market data confirms $527,818… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not applicable to SPL mints, but metadata mutability allows for branding changes. The mint and freeze authorities remain active, allowing for potential supply inflation or account… |

## Security Findings

_🟢 1 Low · ⚪ 8 Informational_

### `L-01` — Flagged High-Risk by Third-Party Registry  *(Severity: Low · Status: Unresolved)*

An independent third-party risk registry classifies this token as high-risk based on its own dataset.

**Recommendation:** Do not interact with this token.


### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is E5GXVzJbuN7iPJAfNB23SMXgQLXWGkqRWgvsq4Dg156o. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Freeze Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The freeze authority is E5GXVzJbuN7iPJAfNB23SMXgQLXWGkqRWgvsq4Dg156o. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `I-03` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 62.2% of supply. Of that, 28.1% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 28.2% in wallets, 5.9% in other contracts. 17,731 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Hex Trust Wrapped XRP (WXRP), market cap $65M. 17,731 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $666K (DexScreener, all pools). 24h trading volume $410K (CoinGecko, all markets, daily snapshot). 24h trading volume $2.1M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply; freeze or blacklist individual addresses; change the token's name, symbol and image. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $666K of DEX liquidity across 30 pools. Launch: 242 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`6UpQcM...5We2`](https://solscan.io/account/6UpQcMAb5xMzxc7ZfPaVMgx3KqsvKZdT5U718BzD5We2) |
| **Network** | Solana |
| **Price** | $1.3100 |
| **24h Volume** | $1.80M |
| **Liquidity** | $526.5K |
| **Volume / Liquidity** | 3.4× |
| **Token Age** | 8mo |
| **Top-10 Holders** | 62.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 15648 buys / 13785 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/jae55dx5trr1oxbes8ergxgcsp6mpudlqwwbf5dvevsz)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/wrapped-xrp-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-27*

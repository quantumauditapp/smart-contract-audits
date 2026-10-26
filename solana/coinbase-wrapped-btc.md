---
token: Coinbase Wrapped BTC
ticker: CBBTC
network: solana
risk_score: 10
status: low
date: 2026-09-01
---

# Coinbase Wrapped BTC (CBBTC) — Smart Contract Security Analysis | Solana

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-sol)

---

## Audit Summary

The Coinbase Wrapped BTC (cbBTC) SPL token mint presents critical security risks due to unrevoked Mint and Freeze authorities, which allow the respective key holders to mint unlimited tokens or freeze any holder's funds. Additionally, the top 10 holders control 64.98% of the supply, posing a concentration risk. While third-party registry data was available, specific holder distribution details beyond the top 10 were not.

> **Final Recommendation:** Before interacting with this token, verify on-chain that the Mint Authority has been set to null to prevent arbitrary supply inflation. Confirm that the Freeze Authority has also been revoked to ensure funds cannot be unilaterally frozen. Monitor the token's metadata for any unexpected changes to its branding or identity.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The cbBTC token operates on the standard `spl-token` program with a total supply of 335,920,214,592 units and 8 decimals. Both the Mint Authority (`CTQE6PMesbH4szKR9Nk5moj9WWUr9MVGP734wYX9wy3p`) and… |
| **Governance / Economics** | 9/10 | Low | The token exhibits a significant holder concentration (7.4 Economic), with the top 10 accounts holding 64.98% of the total supply, which could lead to price volatility from large sell-offs. Liquidity… |
| **Upgrades** | 10/10 | Low | The token's metadata is mutable (7.7 Upgrades), meaning its name, symbol, or image can be altered post-launch. Crucially, the Mint Authority and Freeze Authority are still enabled, allowing for… |

## Security Findings

_⚪ 9 Informational_

### `I-01` — Mint Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The mint authority is CTQE6PMesbH4szKR9Nk5moj9WWUr9MVGP734wYX9wy3p. The holder of this key can mint unlimited new tokens, diluting all current holders to zero value.

**Recommendation:** Verify on-chain that the mint authority is set to null before treating supply as fixed.


### `I-02` — Freeze Authority Not Revoked  *(Severity: Informational · Status: Unresolved)*

The freeze authority is DSFAkPhfrSR95J9oq9Sh8rUetbj5vgFmwiSuHw6rAVnz. The holder can freeze any holder's account, blocking transfers and effectively confiscating funds.

**Recommendation:** Avoid tokens whose freeze authority is not revoked unless the issuer is a regulated stablecoin operator.


### `I-03` — Holder Concentration > 50%  *(Severity: Informational · Status: Unresolved)*

Top 10 token accounts hold 64.98% of supply. Coordinated sell-off would crash price; single-whale dumps are common in this range.

**Recommendation:** Account for the risk of significant price volatility due to concentrated holdings.


### `I-04` — Mutable Metadata  *(Severity: Informational · Status: Unresolved)*

Token name, symbol, or image can be changed post-launch.

**Recommendation:** Verify metadata against off-chain expectations before trusting branding.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.5% of supply. What remains: 65.5% in wallets, 0.0% in other contracts. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coinbase Wrapped BTC (CBBTC), market cap $7.7B. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $17.4M (DexScreener, all pools). 24h trading volume $13.0M (DexScreener, main pool).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-POWERS` — What the token's controller can do  *(Severity: Informational · Status: Acknowledged)*

The contract lets its controller — the freeze authority — mint new supply. These are the issuer's controls by design; for a verified issuer they are counterparty risk — the issuer can act on any holder, including you.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: the freeze authority. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $17.4M of DEX liquidity across 30 pools. Launch: 662 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`cbbtcf...iMij`](https://solscan.io/account/cbbtcf3aa214zXHbiAZQwf4122FBYbraNdFqgw4iMij) |
| **Network** | Solana |
| **Price** | $85,878.5800 |
| **24h Volume** | $12.99M |
| **Liquidity** | $9.24M |
| **Volume / Liquidity** | 1.4× |
| **Token Age** | 1y |
| **Top-10 Holders** | 65.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1480 buys / 1433 sells |

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

- [View on DexScreener](https://dexscreener.com/solana/ceazcxbnlpjwtxzt58qqmfmbtjy8pqlvursxtjygqpbn)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-sol)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

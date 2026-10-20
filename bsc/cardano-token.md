---
token: Cardano Token
ticker: ADA
network: bsc
risk_score: 9
status: low
date: 2026-10-05
---

# Cardano Token (ADA) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/cardano-token-bsc)

---

## Audit Summary

The BEP20Cardano contract functions as a standard BEP20 token. The primary security concern identified is the owner's ability to mint new tokens, which introduces a risk of token supply dilution for existing holders. The contract is not upgradeable, ensuring immutability of its logic.

> **Final Recommendation:** It is crucial for token holders to understand the implications of the owner's ability to mint new tokens. If the minting functionality is not intended for continuous use, consider removing it or implementing robust controls. For example, transferring ownership to a multi-signature wallet or adding a time-lock mechanism to the `mint` function could enhance security and decentralization.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The BEP20Cardano contract correctly implements the BEP20 standard, providing essential token functionalities such as `transfer` and `balanceOf`. The core token transfer logic, including `transfer`… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model is heavily influenced by the owner's privileged access. The `mint(uint256)` function grants the owner the power to increase the total token supply at any time, which… |
| **Upgrades** | 10/10 | Low | The BEP20Cardano contract is not deployed as an upgradeable proxy (7.7 Upgrades). This design choice means the contract's logic is immutable once deployed, eliminating risks associated with upgrade… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 41.9% |
| **Top-3 Unlocked** | 76.2% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — A privileged address can mint new tokens  *(Severity: Informational · Status: Unresolved)*

A privileged function increases the total supply, diluting every holder. Functions: mint(uint256). Restricted to: owner.

**Recommendation:** Check who holds these functions and whether a timelock or multisig stands between them and holders.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 59.1% of supply. Of that, 3.1% locked — not holders that can sell, so excluded from the concentration score. What remains: 55.1% in wallets, 1.0% in other contracts. 616,987 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Binance-Peg Cardano (ADA), market cap $121M. On GoPlus's list of trusted tokens. Traded on Binance. 616,987 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $1.2M (DexScreener, all pools). 24h trading volume $853K (CoinGecko, all markets, daily snapshot). 24h trading volume $953K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.10 on 2021-09-01; the price is now 91.3414% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Binance-Peg Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $1.2M of DEX liquidity across 30 pools. Launch: 1990 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x3ee2...5d47`](https://bscscan.com/address/0x3ee2200efb3400fabb9aacf31297cbdd1d435d47) |
| **Network** | BNB Chain |
| **Price** | $0.2712 |
| **24h Volume** | $575.8K |
| **Liquidity** | $555.0K |
| **Volume / Liquidity** | 1.0× |
| **Token Age** | 5y |
| **Top-10 Holders** | 59.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1544 buys / 1492 sells |

## Security Flags (2/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x673516e510d702ab5f2bbf0c6b545111a85f7ea7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/cardano-token-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*

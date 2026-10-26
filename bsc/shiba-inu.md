---
token: SHIBA INU
ticker: SHIB
network: bsc
risk_score: 9
status: low
date: 2026-10-10
---

# SHIBA INU (SHIB) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/shiba-inu-bsc)

---

## Audit Summary

This audit covers a BEP20 token deployed via an upgradeable proxy. The primary finding is a medium-severity issue related to the owner's ability to mint new tokens, which introduces centralization and potential economic risks. The contract otherwise implements standard ERC-20 functionality.

> **Final Recommendation:** It is recommended to carefully manage the ownership of the token contract, especially regarding the minting capability. Consider transferring ownership to a multi-signature wallet or a time-locked contract to reduce the risk of a single point of failure or malicious action. Additionally, review the security practices for the proxy admin address to ensure the upgrade mechanism is robust and secure.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The contract implements standard ERC-20 functionality, including `transfer` and `transferFrom` methods, which appear to be correctly implemented (7.2 Code Security). A significant technical risk is… |
| **Governance / Economics** | 9/10 | Low | The economic model is primarily affected by the owner's ability to `mint(uint256)` new tokens. This function allows the owner to arbitrarily increase the total supply, which could lead to token… |
| **Upgrades** | 2/10 | High | The token is deployed using an EIP-1967 Transparent Proxy pattern, allowing for future upgrades of the contract logic (7.1 Architecture). This provides flexibility for bug fixes or feature… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 31.5% |
| **Top-3 Unlocked** | 65.3% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — The token's controller can create new tokens at any time.  *(Severity: Informational · Status: Unresolved)*

The `owner` of the token contract has the power to call the `mint(uint256)` function. This function creates new tokens and adds them to the total supply, which can be sent to any address. This means the controller can increase the total number of tokens in circulation without limit, potentially reducing the value of tokens held by others.

**Recommendation:** Token holders should be aware that the current `owner` (the controller) has the ability to create an unlimited number of new tokens. To mitigate this risk, the project team could consider transferring ownership to a multi-signature wallet or a decentralized autonomous organization (DAO) that requires multiple approvals for such actions, or even revoking the minting capability if it's not essential for the token's long-term design.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 32.7% of supply. What remains: 32.7% in wallets, 0.0% in other contracts. 1,395,888 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Binance-Peg SHIB (SHIB), market cap $45M. On GoPlus's list of trusted tokens. Traded on Binance. 1,395,888 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $737K (DexScreener, all pools). 24h trading volume $84K (CoinGecko, all markets, daily snapshot). 24h trading volume $509K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Binance-Peg Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $737K of DEX liquidity across 30 pools. Launch: 1968 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x2859...dd4d`](https://bscscan.com/address/0x2859e4544c4bb03966803b044a93563bd2d0dd4d) |
| **Network** | BNB Chain |
| **Price** | $0.00000547 |
| **24h Volume** | $97.9K |
| **Liquidity** | $409.4K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 32.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 504 buys / 538 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/bsc/0x98386f283e088ad53048376fc1c3bf2f726f775a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/shiba-inu-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-10*

---
token: LCX
ticker: LCX
network: ethereum
risk_score: 12
status: low
date: 2026-10-07
---

# LCX (LCX) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 12/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/lcx-eth)

---

## Audit Summary

The LCXToken contract is an upgradeable ERC-20 token with administrative controls for pausing transfers and blacklisting addresses. The contract is owned by a 3/5 multisig, enhancing security for critical operations. Two medium-severity issues were identified, relating to centralized control over token transfers, which could impact token holder autonomy.

> **Final Recommendation:** Review and clearly document the operational procedures for the owner multisig and the blacklister role, especially concerning the use of pause and blacklist functionalities. Consider implementing a timelock for critical administrative actions to provide users with advance notice and an opportunity to react. Evaluate whether the current level of centralization for pausing and blacklisting aligns with the project's long-term decentralization goals and community expectations.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The LCXToken contract implements standard ERC-20 functionality and includes additional administrative controls. The `transfer` and `transferFrom` functions correctly incorporate `whenNotPaused` and… |
| **Governance / Economics** | 9/10 | Low | The contract's economic model is based on a standard ERC-20 token with additional administrative powers. The owner, a 3/5 multisig, has significant control over token operations, including pausing… |
| **Upgrades** | 2/10 | High | The LCXToken is deployed as an upgradeable proxy using the EIP-1967 Transparent Proxy pattern (7.1 Architecture). This allows for future logic upgrades, ensuring flexibility and the ability to fix… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → EOA |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 57.7% |
| **Top-3 Unlocked** | ⚠️ 99.7% |

## Security Findings

_⚪ 6 Informational_

### `CP-04` — Owner can pause all token transfers  *(Severity: Informational · Status: Unresolved)*

The contract owner has the ability to completely stop all token transfers by calling the `pause()` function. This means that token holders would be unable to move or sell their tokens until the owner calls the `unpause()` function.

**Recommendation:** Token holders should be aware that a single entity (the owner) can unilaterally halt all token activity. Projects should clearly communicate the circumstances under which this power might be used and consider mechanisms to decentralize or time-lock such critical functions.


### `CP-06` — Privileged address can block individual token holders  *(Severity: Informational · Status: Unresolved)*

A designated blacklister, or the contract owner, can prevent specific token holders from transferring their tokens by calling the `blacklist()` function. This means that chosen addresses can be permanently or temporarily blocked from moving or selling their LCX tokens. The `deBlacklist()` function can reverse this.

**Recommendation:** Token holders should understand that their ability to transfer tokens can be individually restricted by a privileged address. The criteria and process for blacklisting should be transparently communicated to the community.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 74.5% of supply. What remains: 74.5% in wallets, 0.0% in other contracts. 5,029 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as LCX (LCX), market cap $56M, rank #448. Traded on Coinbase. 5,029 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $154K (DexScreener, all pools). 24h trading volume $5.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $356K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: bridge-mint functions in its code. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 3-of-5 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $154K of DEX liquidity across 2 pools. Launch: 239 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x8cd4...ae7e`](https://etherscan.io/address/0x8cd41041505885ef0ad3858181d66f17be8aae7e) |
| **Network** | Ethereum |
| **Price** | $0.0647 |
| **24h Volume** | $292.9K |
| **Liquidity** | $117.2K |
| **Volume / Liquidity** | 2.5× |
| **Token Age** | 7mo |
| **Top-10 Holders** | 74.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 227 buys / 333 sells |

## Security Flags (1/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ❌ Fail |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ❌ Fail |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ❌ | **Mint function present** — supply can be inflated by the owner. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ❌ | **Proxy contract** — the implementation can be swapped by the owner. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xcd16bd897f5c29bbc9e356f4a6bd682b20d97c19d962fbd0cb0ecdfc344c2068)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/lcx-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-07*

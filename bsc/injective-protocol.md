---
token: Injective Protocol
ticker: INJ
network: bsc
risk_score: 59
status: medium
date: 2026-10-11
---

# Injective Protocol (INJ) — Smart Contract Security Analysis | BNB Chain

> **Risk Score: 59/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/injective-protocol-bsc)

---

## Audit Summary

This audit covers a BEP20 token implemented via an upgradeable proxy. The contract provides standard ERC-20 functionalities. A key finding identifies that the contract owner has the ability to mint new tokens, which could dilute existing token holders.

> **Final Recommendation:** It is crucial for token holders to understand the implications of the owner's ability to mint new tokens. The project team should clearly communicate the policies and procedures governing the use of the `mint` function. Consider implementing a multi-signature wallet for the owner address to enhance security and decentralize control over critical functions like minting and ownership transfer. Additionally, ensure robust operational security for the proxy admin key.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 7/10 | Low | The contract implements a standard BEP20 token behind an EIP-1967 Transparent Proxy, ensuring upgradeability (7.1 Architecture). Core ERC-20 functions like `transfer` and `transferFrom` are correctly… |
| **Governance / Economics** | 1/10 | High | The economic model of the token is directly impacted by the owner's ability to `mint(uint256)` new tokens (7.4 Economic). This centralized control over supply can lead to token dilution if misused.… |
| **Upgrades** | 1/10 | High | The contract utilizes an EIP-1967 Transparent Proxy pattern, allowing for future upgrades of the token's logic (7.7 Upgrades). This design provides flexibility for bug fixes or feature additions… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 62.9% |
| **Top-3 Unlocked** | ⚠️ 85.7% |

## Security Findings

_🟡 2 Medium · ⚪ 4 Informational_

### `CP-01` — Owner can mint new tokens  *(Severity: Medium · Status: Unresolved)*

The contract includes a `mint(uint256)` function that allows the current owner of the token contract to create and add new tokens to the total supply. This means the owner can increase the number of tokens in circulation at any time, potentially diluting the value of existing tokens.

**Recommendation:** Token holders should be aware that the token supply is not fixed and can be increased by the contract owner. The project team should clearly define and communicate the circumstances under which new tokens will be minted, or consider revoking this capability if a fixed supply is desired.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.1% is held, unlocked, by 10 address(es) other than the owner/deployer. One of them — a contract, 0xb789…1f2d — holds 62.9% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 45% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 65.9% of supply. Of that, 15.5% locked — not holders that can sell, so excluded from the concentration score. What remains: 50.4% in wallets, 0.0% in other contracts. 58,838 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Injective (INJ), market cap $752M, rank #93. Traded on Binance. 58,838 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $497K (DexScreener, all pools). 24h trading volume $132.3M (CoinGecko, all markets, daily snapshot). 24h trading volume $85K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $497K of DEX liquidity across 30 pools. Launch: 1996 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xa2b7...d495`](https://bscscan.com/address/0xa2b726b1145a4773f68593cf171187d8ebe4d495) |
| **Network** | BNB Chain |
| **Price** | $7.6300 |
| **24h Volume** | $43.8K |
| **Liquidity** | $221.9K |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 5y |
| **Top-10 Holders** | 65.9% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 609 buys / 526 sells |

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

- [View on DexScreener](https://dexscreener.com/bsc/0x1bdcebca3b93af70b58c41272aea2231754b23ca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/injective-protocol-bsc)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-11*

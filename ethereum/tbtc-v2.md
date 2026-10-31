---
token: tBTC v2
ticker: TBTC
network: ethereum
risk_score: 9
status: low
date: 2026-10-31
---

# tBTC v2 (TBTC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/tbtc-v2-eth)

---

## Audit Summary

The TBTC contract is a standard ERC-20 implementation with additional recovery and minting capabilities. The architecture is straightforward, utilizing OpenZeppelin standards for core functionality. While the owner possesses significant power to mint tokens and recover assets, these functions are typical for administrative management in this token model.

> **Final Recommendation:** The protocol should consider transitioning the owner role to a multi-signature wallet or a decentralized governance contract to mitigate the risk of centralized control over token supply. Additionally, implementing a timelock on the mint function would provide transparency and protection for token holders against sudden supply changes.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract follows established ERC-20 standards and includes safe transfer patterns. 7.1 Architecture is modular, 7.2 Code Security is robust due to the use of audited libraries, and 7.3 Access… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance rely on a centralized owner address. The ability to mint tokens creates a potential for supply inflation, which is a significant economic risk for holders. Governance… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are handled through standard administrative functions. The lack of upgradeability ensures immutability of the current… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 99.5% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The mint(address,uint256) function allows the contract owner to create new tokens at will, which increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Restrict the minting capability to a multi-signature wallet or implement a timelock mechanism to ensure that any increase in supply is subject to community oversight or a mandatory waiting period.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 79.7% of supply. What remains: 7.0% in wallets, 72.7% in other contracts. 24,882 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as tBTC (TBTC), market cap $324M. 24,882 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $23.5M (DexScreener, all pools). 24h trading volume $6.2M (CoinGecko, all markets, daily snapshot). 24h trading volume $1.8M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized BTC. Tokenomics — Supply: mintable with no on-chain cap found. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $23.5M of DEX liquidity across 16 pools. Launch: 1367 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1808...3a88`](https://etherscan.io/address/0x18084fba666a33d37592fa2633fd49a74dd93a88) |
| **Network** | Ethereum |
| **Price** | $77,516.9700 |
| **24h Volume** | $1.07M |
| **Liquidity** | $4.18M |
| **Volume / Liquidity** | 0.3× |
| **Token Age** | 3y |
| **Top-10 Holders** | 79.7% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 45 buys / 80 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x73a38006d23517a1d383c88929b2014f8835b38b)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/tbtc-v2-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

---
token: (PoS) Wrapped BTC
ticker: WBTC
network: polygon
risk_score: 22
status: low
date: 2026-10-31
---

# (PoS) Wrapped BTC (WBTC) — Smart Contract Security Analysis | Polygon

> **Risk Score: 22/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pos-wrapped-btc-poly)

---

## Audit Summary

The UChildERC20 contract is a standard bridge-compatible token implementation on Polygon. It utilizes a proxy pattern for upgradeability and standard AccessControl for administrative tasks. The primary risks identified involve centralized minting capabilities and the accumulation of trapped ETH within the contract.

> **Final Recommendation:** The protocol should ensure that the address holding the DEPOSITOR_ROLE is a multi-signature wallet or a time-locked contract to mitigate the risk of unauthorized minting. Additionally, implement a sweep function to allow the recovery of accidentally sent ETH to the contract address.

Regular monitoring of the DEPOSITOR_ROLE and administrative role assignments is recommended to ensure that only authorized bridge infrastructure maintains control over the token supply.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The architecture follows standard OpenZeppelin-like patterns for ERC20 and AccessControl. 7.1 Architecture and 7.2 Code Security are robust, utilizing established libraries for core logic. 7.3 Access… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance risks are centered on the centralized minting authority. The DEPOSITOR_ROLE can arbitrarily increase the total supply, which is a necessary feature for bridge… |
| **Upgrades** | 5/10 | Medium | 7.7 Upgrades are handled via a proxy pattern, allowing for logic updates. The implementation is separated from the proxy, ensuring state persistence across upgrades. The upgrade mechanism is standard… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Etherscan Detected Custom |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 8.2% |
| **Top-3 Unlocked** | 22.8% |

## Security Findings

_🟡 1 Medium · ⚪ 5 Informational_

### `CD-01` — Trapped ETH in Contract  *(Severity: Medium · Status: Unresolved)*

The contract can receive ETH through meta-transactions or direct transfers but lacks a mechanism to withdraw or transfer these funds out. Any ETH sent to the contract is permanently locked.

**Recommendation:** Implement an administrative function to withdraw any ETH accidentally sent to the contract address.


### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The deposit function allows an address with the DEPOSITOR_ROLE to mint new tokens at will. This increases the total supply and dilutes the value of existing holdings, which could be abused if the role is compromised.

**Recommendation:** Restrict the DEPOSITOR_ROLE to a highly secure, multi-signature wallet or a time-locked governance contract to prevent unauthorized minting actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 54.0% of supply. What remains: 2.5% in wallets, 51.5% in other contracts. 370,198 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Polygon Bridged WBTC (Polygon POS) (WBTC), market cap $172M. On GoPlus's list of trusted tokens. Traded on Binance. 370,198 holders. Verified by: CoinGecko, GoPlus, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $5.2M (DexScreener, all pools). 24h trading volume $3.7M (CoinGecko, all markets, daily snapshot). 24h trading volume $936K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Bridged-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: an owner that could not be resolved. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $5.2M of DEX liquidity across 30 pools. Launch: 2196 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1bfd...bfd6`](https://polygonscan.com/address/0x1bfd67037b42cf73acf2047067bd4f2c47d9bfd6) |
| **Network** | Polygon |
| **Price** | $77,325.0320 |
| **24h Volume** | $276.1K |
| **Liquidity** | $1.29M |
| **Volume / Liquidity** | 0.2× |
| **Token Age** | 6y |
| **Top-10 Holders** | 54.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 347 buys / 340 sells |

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

- [View on DexScreener](https://dexscreener.com/polygon/0x50eaedb835021e4a108b7290636d62e9765cc6d7)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pos-wrapped-btc-poly)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-31*

---
token: PancakeSwap
ticker: CAKE
network: ethereum
risk_score: 10
status: low
date: 2026-08-20
---

# PancakeSwap (CAKE) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 10/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/pancakeswap-eth)

---

## Audit Summary

The CakeOFT contract implements an Omnichain Fungible Token (OFT) standard, allowing cross-chain transfers via LayerZero. The architecture relies on a centralized owner with extensive control over token supply, fee structures, and cross-chain caps. While the implementation follows standard LayerZero patterns, the high level of centralization and the ability to mint tokens pose significant risks to token holders.

> **Final Recommendation:** It is recommended to transition the ownership of the contract to a multi-signature wallet or a decentralized governance DAO to mitigate the risks associated with a single point of failure. Additionally, implementing a timelock on sensitive administrative functions like setOutboundCap and setFeeBp would provide users with sufficient notice before economic changes take effect.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The contract utilizes established LayerZero OFT libraries for cross-chain messaging. 7.1 Architecture is modular, separating core logic from cross-chain transport. 7.2 Code Security is robust… |
| **Governance / Economics** | 9/10 | Low | 7.4 Economic and 7.5 Governance are heavily centralized under the contract owner. The owner can modify fee structures via setFeeBp and setOutboundCap, directly impacting user costs and liquidity… |
| **Upgrades** | 10/10 | Low | 7.7 Upgrades are not implemented via proxy patterns in this contract. The contract is immutable in its logic, which prevents unauthorized code changes. 7.8 Operations are managed through… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 91.7% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Privileged Minting Capability  *(Severity: Informational · Status: Unresolved)*

The sendAndCall function allows a privileged address to mint new tokens. This action increases the total supply of the token, which directly dilutes the value of existing holdings for all token holders.

**Recommendation:** Restrict the minting capability to a specific, audited bridge contract or remove the minting functionality entirely if it is not required for the intended cross-chain operations.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 59.2% of supply. What remains: 59.2% in wallets, 0.0% in other contracts. 21,312 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as PancakeSwap (CAKE), market cap $668M, rank #92. Traded on Binance, Coinbase. 21,312 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $230K (DexScreener, all pools). 24h trading volume $51.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $24K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $43.96 on 2021-04-30; the price is now 95.2158% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Governance; a copy of the coin from its home chain (binance-smart-chain), minted here by LayerZero (lzReceive). Tokenomics — Supply: minted here by LayerZero (lzReceive) against tokens locked or burned on other chains. Control: a ProxyAdmin contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $230K of DEX liquidity across 10 pools. Launch: 1304 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x1526...c898`](https://etherscan.io/address/0x152649ea73beab28c5b49b26eb48f7ead6d4c898) |
| **Network** | Ethereum |
| **Price** | $2.1100 |
| **24h Volume** | $15.8K |
| **Liquidity** | $149.5K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 59.2% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 76 buys / 94 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x517f451b0a9e1b87dc0ae98a05ee033c3310f046)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/pancakeswap-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-08-20*

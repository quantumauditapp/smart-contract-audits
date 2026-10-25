---
token: Base tBTC v2
ticker: TBTC
network: base
risk_score: 47
status: medium
date: 2026-10-25
---

# Base tBTC v2 (TBTC) — Smart Contract Security Analysis | Base

> **Risk Score: 47/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/base-tbtc-v2-base)

---

## Audit Summary

The L2TBTC contract is a standard ERC-20 token implementation utilizing the Transparent Proxy pattern. The protocol is managed by a 6-of-9 multisig, providing a high degree of operational security. The primary risk identified is the centralized minting authority, which allows privileged addresses to increase the total supply.

> **Final Recommendation:** The protocol demonstrates strong security practices, particularly through the use of a multisig and a timelock for administrative actions. We recommend maintaining the current multisig threshold and ensuring that the list of minters is audited regularly to prevent unauthorized supply expansion.

For future iterations, consider implementing a decentralized governance mechanism or a hard cap on the total supply to further mitigate the risks associated with centralized minting authority.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows industry-standard OpenZeppelin upgradeable patterns, ensuring robust code structure. 7.1 Architecture is sound, utilizing a proxy-implementation separation. 7.2 Code Security… |
| **Governance / Economics** | 8/10 | Low | 7.4 Economic risk is centered on the minting capability, which allows for supply dilution. 7.5 Governance is handled by a 6-of-9 multisig, which is a strong security measure against… |
| **Upgrades** | 6/10 | Medium | 7.7 Upgrades are managed through a Transparent Proxy pattern controlled by a Timelock, providing a 24-hour delay for administrative changes. 7.8 Operations are well-defined with clear roles for… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Eip1967 Transparent |
| **Admin** | OZ ProxyAdmin → Timelock |
| **Implementation** | ✅ Verified source |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 87.0% |
| **Top-3 Unlocked** | ⚠️ 100.0% |

## Security Findings

_⚪ 5 Informational_

### `CP-01` — Centralized Minting Authority  *(Severity: Informational · Status: Unresolved)*

The mint(address,uint256) function allows addresses with the 'minter' role to create new tokens, which increases the total supply and dilutes the value of existing holdings.

**Recommendation:** Implement a hard cap on the total supply or transition the minting authority to a decentralized governance contract to prevent arbitrary supply increases.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 77.6% of supply. What remains: 3.6% in wallets, 74.0% in other contracts. 84,980 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as tBTC (TBTC), market cap $333M. 84,980 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.3M (DexScreener, all pools). 24h trading volume $3.1M (CoinGecko, all markets, daily snapshot). 24h trading volume $273K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Tokenized BTC. Tokenomics — Supply: mintable with no on-chain cap found. Control: a 6-of-9 multisig. Code: upgradeable proxy. Fees: no buy or sell tax. Market: $2.3M of DEX liquidity across 25 pools. Launch: 1153 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x236a...794b`](https://basescan.org/address/0x236aa50979d5f3de3bd1eeb40e81137f22ab794b) |
| **Network** | Base |
| **Price** | $80,654.7100 |
| **24h Volume** | $85.0K |
| **Liquidity** | $953.9K |
| **Volume / Liquidity** | 0.1× |
| **Token Age** | 3y |
| **Top-10 Holders** | 77.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 184 buys / 188 sells |

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

- [View on DexScreener](https://dexscreener.com/base/0xb24f7fcd75c3a001b74be4c60f181c024154c4d7c33097777e3950979042b073)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/base-tbtc-v2-base)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-25*

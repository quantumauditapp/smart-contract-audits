---
token: Coinbase Wrapped BTC
ticker: CBBTC
network: ethereum
risk_score: 9
status: low
date: 2026-10-17
---

# Coinbase Wrapped BTC (CBBTC) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 9/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-eth)

---

## Audit Summary

This report details the security posture of the FiatTokenV2_1 contract, an ERC-20 token implementation. The contract exhibits a high degree of centralized control, allowing specific privileged roles to mint new tokens, pause all transfers, and blacklist individual addresses. These capabilities introduce significant governance and economic risks for token holders.

> **Final Recommendation:** It is crucial for token holders to understand the extensive centralized control inherent in the FiatTokenV2_1 contract. The project team should implement robust multi-signature wallets for all privileged roles (owner, masterminter, pauser, blacklister, rescuer) to mitigate single points of failure. Additionally, transparent communication regarding any planned minting, pausing, blacklisting, or upgrade actions is essential to maintain trust and inform the community.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 9/10 | Low | The FiatTokenV2_1 contract is an ERC-20 token with additional features inherited from various FiatToken versions. It includes standard token functionalities and robust mechanisms for emergency… |
| **Governance / Economics** | 9/10 | Low | The economic stability and governance of the FiatTokenV2_1 are heavily reliant on the integrity of its privileged roles (7.5 Governance, 7.4 Economic). The `minters` role can `mint` new tokens… |
| **Upgrades** | 2/10 | High | The contract is deployed behind a Zeppelin OS Legacy proxy, making it upgradeable (7.7 Upgrades). This allows the owner to deploy new implementation logic, which can introduce new features or fix… |

## Proxy Upgrade Controls

| Control | Value |
|---------|-------|
| **Proxy Type** | Zeppelin Os Legacy |
| **Admin** | ⚠️ EOA (single key controls upgrades) |
| **Implementation** | ✅ Verified source |
| **Upgrades (30d)** | 0 (stable) |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 68.0% |
| **Top-3 Unlocked** | ⚠️ 92.4% |

## Security Findings

_⚪ 7 Informational_

### `CP-01` — Centralized Token Minting Capability  *(Severity: Informational · Status: Unresolved)*

The `mint` function allows an authorized `minter` to create new tokens and add them to any address. This increases the total supply of tokens, which can dilute the value of existing tokens held by users.

**Recommendation:** Token holders should be aware that the supply of this token is not fixed and can be increased by the designated `minters`. Transparency around minting policies and a clear communication strategy for any supply changes are crucial.


### `CP-04` — Centralized Transfer Pause Functionality  *(Severity: Informational · Status: Unresolved)*

The `pause` function, callable by the `pauser`, can halt all token transfers. This means that at any time, the `pauser` can prevent token holders from moving or selling their tokens, effectively freezing all activity on the token. The `unpause` function can resume transfers.

**Recommendation:** Token holders should understand that their ability to transfer tokens can be unilaterally suspended by the `pauser`. The project should clearly define the circumstances under which pausing would occur and ensure the `pauser` role is secured with strong access controls.


### `CP-06` — Centralized Blacklisting Capability  *(Severity: Informational · Status: Unresolved)*

The `blacklist` function allows the `blacklister` to prevent specific addresses from sending or receiving tokens. This means that chosen token holders can be blocked from moving or selling their tokens, effectively freezing their assets. The `unBlacklist` function can remove an address from the blacklist.

**Recommendation:** Token holders should be aware that their tokens can be frozen by the `blacklister`. The project should establish clear, publicly available policies for blacklisting and ensure the `blacklister` role is managed with the highest security standards.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 81.1% of supply. What remains: 11.8% in wallets, 69.3% in other contracts. 89,403 holders in total. For a verified reference asset the largest holders are custodians, exchanges and bridges; concentration is reported, not scored.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Coinbase Wrapped BTC (CBBTC), market cap $7.7B. 89,403 holders. Verified by: CoinGecko.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $143.1M (DexScreener, all pools). 24h trading volume $297.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $9.3M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Wrapped or bridged asset  *(Severity: Informational · Status: Acknowledged)*

A token representing another asset's units 1:1, backed by a wrapping contract, a custodian or a bridge. Scored as an established reference asset: its identity is verified, so the issuer's or protocol's controls (listed as findings) are real and are priced once as counterparty risk, and LP locks and holder concentration are not scored — its pools belong to market makers and its largest holders are exchanges, bridges and custody. Basis: CoinGecko category: Wrapped-Tokens. Tokenomics — Supply: mintable with no on-chain cap found. Control: a single wallet (EOA). Code: upgradeable proxy. Fees: no buy or sell tax. Market: $143.1M of DEX liquidity across 30 pools. Launch: 771 days of market history.

**Recommendation:** The backing is the risk: check who holds the underlying asset and how redemption works.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xcbb7...33bf`](https://etherscan.io/address/0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf) |
| **Network** | Ethereum |
| **Price** | $81,786.2200 |
| **24h Volume** | $2.08M |
| **Liquidity** | $61.81M |
| **Volume / Liquidity** | 0.0× |
| **Token Age** | 2y |
| **Top-10 Holders** | 81.1% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 79 buys / 48 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x862cb4e988fb66e72f128d1183829f8c05b6c6a0)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/coinbase-wrapped-btc-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-17*

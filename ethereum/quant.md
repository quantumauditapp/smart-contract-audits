---
token: Quant
ticker: QNT
network: ethereum
risk_score: 43
status: medium
date: 2026-09-01
---

# Quant (QNT) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 43/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/quant-eth)

---

## Audit Summary

The protocol implements a standard ERC-20 token with an additional minting capability restricted to a crowdsale contract. While the core transfer logic follows standard patterns, the minting function introduces significant centralization risk. The contract lacks modern security features like reentrancy guards or pause functionality, which is consistent with its 2018 deployment era.

> **Final Recommendation:** The protocol should implement a multi-signature wallet or a time-locked governance contract to control the crowdsale address. This would mitigate the risk of a single compromised key performing unauthorized minting operations.

Additionally, consider adding a 'pause' mechanism to halt transfers in the event of a detected exploit. Future iterations should migrate to modern OpenZeppelin standards, including AccessControl for granular permission management and ReentrancyGuard for all state-changing functions.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The contract utilizes standard OpenZeppelin-style ERC-20 logic, ensuring 7.1 Architecture and 7.2 Code Security are consistent with established patterns. 7.3 Access Control is implemented via a… |
| **Governance / Economics** | 3/10 | High | 7.4 Economic and 7.5 Governance risks are concentrated in the crowdsale contract's ability to mint tokens. This creates a single point of failure where the crowdsale controller can arbitrarily… |
| **Upgrades** | 3/10 | High | 7.7 Upgrades are not supported as the contract is not a proxy. 7.8 Operations are static, meaning the contract logic cannot be altered post-deployment. This provides immutability but prevents… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 19.8% |
| **Top-3 Unlocked** | 50.0% |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 4 Informational_

### `CP-02` — Centralized Minting Authority  *(Severity: High · Status: Unresolved)*

The mint(address,uint256) function allows the crowdsale controller to create new tokens and assign them to any address. This grants the controller total control over the token supply and the ability to dilute existing holders or manipulate balances.

**Recommendation:** Restrict the minting capability by requiring multi-signature approval or a time-locked governance process. Ensure the crowdsale contract is audited and its ownership is transferred to a secure multi-sig wallet.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 78.1% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 49% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 28.8% of supply. What remains: 7.8% in wallets, 21.0% in other contracts. 187,006 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Quant (QNT), market cap $3.2B, rank #34. Traded on Binance, Coinbase. 187,006 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $2.3M (DexScreener, all pools). 24h trading volume $151.0M (CoinGecko, all markets, daily snapshot). 24h trading volume $2.4M (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: mintable with no on-chain cap found. Control: crowdsale — a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $2.3M of DEX liquidity across 22 pools. Launch: 2314 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4a22...4675`](https://etherscan.io/address/0x4a220e6096b25eadb88358cb44068a3248254675) |
| **Network** | Ethereum |
| **Price** | $201.2600 |
| **24h Volume** | $1.46M |
| **Liquidity** | $1.11M |
| **Volume / Liquidity** | 1.3× |
| **Token Age** | 6y |
| **Top-10 Holders** | 28.8% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 110 buys / 115 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x24ee2c6b9597f035088cda8575e9d5e15a84b9df)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/quant-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-09-01*

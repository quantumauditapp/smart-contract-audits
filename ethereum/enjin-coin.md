---
token: Enjin Coin
ticker: ENJ
network: ethereum
risk_score: 56
status: medium
date: 2026-10-03
---

# Enjin Coin (ENJ) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/enjin-coin-eth)

---

## Audit Summary

The ENJToken contract is an ERC-20 token with significant centralized control. The owner has the ability to halt all public token transfers and manage large token allocations for team, advisors, and unsold tokens. Two findings were identified: a medium-severity issue where the owner can control the transfer switch, and a high-severity issue related to shadowing state variables.

> **Final Recommendation:** Token holders should be aware of the significant centralized control held by the contract owner, particularly the ability to halt transfers and manage large token allocations. It is crucial for the owner to implement robust security practices for their private keys to prevent unauthorized access and malicious actions. Future iterations of such contracts should consider decentralizing critical control functions or implementing multi-signature wallets for sensitive operations to reduce single points of failure and enhance trust.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The ENJToken contract implements standard ERC-20 functionality, allowing for token transfers and approvals. Key security features include `ownerOnly` modifiers restricting critical functions to the… |
| **Governance / Economics** | 1/10 | High | The contract exhibits a high degree of centralized control, posing significant governance and economic risks (7.4 Economic, 7.5 Governance). The owner can execute functions like… |
| **Upgrades** | 6/10 | Medium | This contract is not designed to be upgradeable, as indicated by `is_proxy: false` (7.7 Upgrades). This eliminates risks associated with upgrade mechanisms, such as proxy implementation… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 22.0% |
| **Top-3 Unlocked** | 49.2% |

## Security Findings

_🟠 1 High · 🟡 3 Medium · ⚪ 3 Informational_

### `CD-01` — Potential for hidden or conflicting state variables  *(Severity: High · Status: Unresolved)*

The static analysis identified a 'shadowing state' issue. This means that a variable in the `ENJToken` contract might have the same name as a variable in one of its inherited contracts, potentially leading to unexpected behavior or vulnerabilities where the contract uses one variable when it intends to use another. This could affect critical operations or calculations within the token contract.

**Recommendation:** This is a technical issue that could lead to unpredictable behavior. Token holders should be aware that such a low-level coding issue could have unforeseen consequences on the token's functionality or security. The contract developer should review the inheritance hierarchy and variable declarations to ensure no critical state variables are being unintentionally shadowed.


### `CP-05` — Owner can stop all token transfers  *(Severity: Medium · Status: Unresolved)*

The `allowTransfers()` function, which can only be called by the contract owner, controls a switch (`isReleasedToPublic`) that determines whether token transfers are permitted for regular users. If this switch is off, most token transfers will fail. This means the owner has the power to unilaterally halt all public trading or movement of tokens at any time.

**Recommendation:** Token holders should understand that the owner has the ability to freeze token transfers. For future contracts, consider removing such a centralized kill switch or implementing a decentralized governance mechanism (e.g., a DAO) to control it, or a timelock to provide notice.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 83.0% is held, unlocked, by 10 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 88% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $82K (DexScreener, all pools). 24h trading volume $143.4M (CoinGecko, all markets, daily snapshot). 24h trading volume $53K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $4.82 on 2021-11-25; the price is now 99.2365% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 78.6% of supply. Of that, 43.4% burned — not holders that can sell, so excluded from the concentration score. What remains: 28.9% in wallets, 6.4% in other contracts. 151,343 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as Enjin Coin (ENJ), market cap $74M, rank #362. Traded on Binance, Coinbase. 151,343 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a single wallet (EOA). Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $82K of DEX liquidity across 9 pools. Launch: 2328 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xf629...3b9c`](https://etherscan.io/address/0xf629cbd94d3791c9250152bd8dfbdf380e2a3b9c) |
| **Network** | Ethereum |
| **Price** | $0.03556 |
| **24h Volume** | $52.0K |
| **Liquidity** | $72.3K |
| **Volume / Liquidity** | 0.7× |
| **Token Age** | 6y |
| **Top-10 Holders** | 78.6% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 262 buys / 237 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ❌ Fail |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ❌ | Ownership **not renounced** — the deployer retains control over parameters. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xe56c60b5f9f7b5fc70de0eb79c6ee7d00efa2625)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/enjin-coin-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-03*

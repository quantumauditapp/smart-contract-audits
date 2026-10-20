---
token: VAIOT Token
ticker: VAI
network: ethereum
risk_score: 30
status: low
date: 2026-10-05
---

# VAIOT Token (VAI) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 30/100 — 🟢 Low Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/vaiot-token-eth)

---

## Audit Summary

The VAIToken contract is a standard ERC-20 token implementation. It lacks privileged functions for central control over token transfers or supply. A key finding identifies a medium-severity issue where Ether sent to the contract can become permanently inaccessible due to the absence of a withdrawal mechanism.

> **Final Recommendation:** It is crucial to address the medium-severity finding regarding inaccessible Ether. Implement a secure withdrawal mechanism for ETH, restricted to an authorized administrator, to prevent permanent loss of funds. If a withdrawal function is not added, ensure clear communication to users that ETH should never be sent directly to the token contract address. Additionally, consider a comprehensive review of external dependencies and potential attack vectors if the token interacts with other protocols.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 10/10 | Low | The VAIToken contract implements the standard ERC-20 token functionality, allowing for transfers, approvals, and balance queries. It does not have any privileged functions that can alter the token's… |
| **Governance / Economics** | 2/10 | High | The contract exhibits a decentralized access control model for its core ERC-20 functions, as there are no privileged roles that can control transfers or modify token balances (7.3 Access Control).… |
| **Upgrades** | 8/10 | Low | The VAIToken contract is not designed as an upgradeable proxy, meaning its logic cannot be modified or updated after deployment (7.7 Upgrades). This provides immutability but also means any… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | ⚠️ 56.8% |
| **Top-3 Unlocked** | ⚠️ 98.6% |

## Security Findings

_🟡 3 Medium · ⚪ 3 Informational_

### `CD-01` — Ether (ETH) sent to the contract can be permanently lost  *(Severity: Medium · Status: Unresolved)*

The VAIToken contract has a function, `executeMetaTransaction`, that allows it to receive Ether (ETH). However, the contract lacks any function to send this received ETH back out. This means if any ETH is accidentally or intentionally sent to the VAIToken contract, it will be permanently locked and inaccessible to anyone, including the contract deployer or token holders.

**Recommendation:** To prevent loss of funds, a function should be added to the VAIToken contract that allows an authorized party (e.g., an administrator) to withdraw any ETH received. Alternatively, users should be explicitly warned not to send ETH directly to this token contract.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 99.6% is held, unlocked, by 9 address(es) other than the owner/deployer. One of them — a contract, 0x454c…169e — holds 56.8% and can remove that share at once; who controls it is not visible on-chain, so it is not treated as an independent provider. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Medium · Status: Acknowledged)*

Liquidity $107K (DexScreener, all pools). 24h trading volume $762K (CoinGecko, all markets, daily snapshot). 24h trading volume $209K (DexScreener, all pools). CoinGecko's record for this coin: all-time high $3.60 on 2021-04-01; the price is now 99.7835% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 47.0% of supply. Of that, 2.7% in DEX pools — not holders that can sell, so excluded from the concentration score. What remains: 12.7% in wallets, 31.6% in other contracts. 15,352 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as VAIOT (VAI), market cap $3M, rank #2066. Traded on Binance. 15,352 holders. Verified by: exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $107K of DEX liquidity across 1 pools. Launch: 1643 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0xd13c...395c`](https://etherscan.io/address/0xd13cfd3133239a3c73a9e535a5c4dadee36b395c) |
| **Network** | Ethereum |
| **Price** | $0.004793 |
| **24h Volume** | $208.7K |
| **Liquidity** | $107.4K |
| **Volume / Liquidity** | 1.9× |
| **Token Age** | 4y |
| **Top-10 Holders** | 47.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 380 buys / 316 sells |

## Security Flags (3/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ❌ Fail |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ❌ | Liquidity is **not locked** — this is a rug-pull vector. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0xaf95d3a7a25f831dc2b9a6704554435957b51ec2)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/vaiot-token-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-05*

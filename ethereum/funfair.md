---
token: FunFair
ticker: FUN
network: ethereum
risk_score: 56
status: medium
date: 2026-10-30
---

# FunFair (FUN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 56/100 — 🟡 Medium Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/funfair-eth)

---

## Audit Summary

The protocol utilizes a modular architecture separating the Token interface, Controller logic, and Ledger state. While the separation of concerns is clear, the reliance on outdated Solidity versions and manual 'throw' statements poses significant risks. The system is highly centralized, granting the owner extensive control over token state and minting capabilities.

> **Final Recommendation:** Migrate the codebase to a modern Solidity version (0.8.x) to leverage built-in overflow protection and standard error handling. Implement a multi-signature wallet or a decentralized governance contract to manage administrative functions, removing the single point of failure associated with the 'owner' address.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 8/10 | Low | The architecture follows a clean separation of concerns (7.1 Architecture). However, the use of 'throw' instead of 'revert' or 'require' is deprecated and can lead to gas exhaustion (7.2 Code… |
| **Governance / Economics** | 1/10 | High | The protocol exhibits extreme centralization (7.5 Governance). The owner can stop minting, change controllers, and lock multisig transfers (7.4 Economic). There are no time-locks or multi-signature… |
| **Upgrades** | 7/10 | Low | The system is modular, allowing for controller and ledger updates (7.7 Upgrades). However, these upgrades are controlled by a single owner address without a governance process. Operations (7.8… |

## LP Distribution

| Metric | Value |
|--------|-------|
| **Top-1 Unlocked Holder** | 46.4% |
| **Top-3 Unlocked** | ⚠️ 82.2% |

## Security Findings

_🟠 1 High · 🟡 7 Medium · ⚪ 4 Informational_

### `QA-POWERS` — What the token's controller can do  *(Severity: High · Status: Acknowledged)*

The contract lets its controller — a contract — change any holder's balance (seize or credit tokens). Nothing independent vouches for whoever holds them, so each is a live risk to holders.

**Recommendation:** Check who holds these powers and whether a timelock or multisig stands between them and holders.


### `M-01` — Missing Input Validation  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). Several functions do not validate that addresses are non-zero, which could lead to tokens being sent to the null address.

**Recommendation:** Add 'require(_to != address(0))' checks.


### `M-02` — Insecure Ownership Transfer  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The ownership transfer process is a two-step process but lacks a 'cancel' function if the wrong address is set.

**Recommendation:** Add a function to reset the 'newOwner' variable.


### `M-03` — Use of Deprecated 'throw' Keyword  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The contract uses the 'throw' keyword, which is deprecated and consumes all remaining gas in a transaction, making it inefficient and potentially problematic for gas estimation.

**Recommendation:** Replace all instances of 'throw' with 'revert()' or 'require()'.


### `M-04` — Centralized Administrative Control  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The 'owner' has absolute power to change the controller, stop minting, and lock transfers, creating a significant trust risk for token holders.

**Recommendation:** Implement a DAO or multi-sig governance structure for all administrative functions.


### `M-05` — Lack of Reentrancy Protection  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The transfer functions do not implement reentrancy guards, which could be exploited if the controller logic interacts with external contracts.

**Recommendation:** Implement OpenZeppelin's ReentrancyGuard on all state-changing functions.


### `M-06` — Unsafe Arithmetic in Ledger  *(Severity: Medium · Status: Unresolved)*

Not confirmed by static analysis (the model's own reading of the source). The 'mint' function uses standard addition instead of the custom 'safeAdd' function, potentially leading to integer overflows.

**Recommendation:** Use 'safeAdd' for all balance and supply updates.


### `QA-LIQUIDITY` — Liquidity not locked  *(Severity: Medium · Status: Acknowledged)*

0.0% of the pool's LP is burned or time-locked. 100.0% is held, unlocked, by 9 address(es) other than the owner/deployer. No single one holds a majority: their exits thin the market rather than hand anyone the pool. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them. This assessment covers the main pool, which holds 56% of the token's DEX liquidity; the other pools were not assessed.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 82.5% of supply. What remains: 82.5% in wallets, 0.0% in other contracts. 73,228 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Identity verified by independent sources  *(Severity: Informational · Status: Acknowledged)*

Listed on CoinGecko as FUNToken (FUN), market cap $47M, rank #450. Traded on Binance. 73,228 holders. Verified by: CoinGecko, exchange listings.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $268K (DexScreener, all pools). 24h trading volume $1.5M (CoinGecko, all markets, daily snapshot). 24h trading volume $3.1M (DexScreener, all pools). CoinGecko's record for this coin: all-time high $0.191 on 2018-01-07; the price is now 97.794% below it.

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: a contract. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $268K of DEX liquidity across 14 pools. Launch: 2354 days of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x419d...711b`](https://etherscan.io/address/0x419d0d8bdd9af5e606ae2232ed285aff190e711b) |
| **Network** | Ethereum |
| **Price** | $0.00234 |
| **24h Volume** | $1.16M |
| **Liquidity** | $151.1K |
| **Volume / Liquidity** | 7.7× |
| **Token Age** | 6y |
| **Top-10 Holders** | 82.5% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 1011 buys / 760 sells |

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

- [View on DexScreener](https://dexscreener.com/ethereum/0x747ba49077e00554e47f76dd716006ec3aa6786db984141eac9c8f6c843b624a)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/funfair-eth)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-10-30*

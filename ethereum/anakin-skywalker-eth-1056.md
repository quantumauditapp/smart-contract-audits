---
token: Anakin Skywalker
ticker: ANAKIN
network: ethereum
risk_score: 70
status: high
date: 2026-11-01
---

# Anakin Skywalker (ANAKIN) — Smart Contract Security Analysis | Ethereum

> **Risk Score: 70/100 — 🟠 High Risk**

[→ Full interactive AI analysis on Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-eth-1056)

---

## Audit Summary

The Anakin token is a standard ERC-20 implementation. The audit identified critical issues regarding return value consistency and insecure authorization patterns. Coverage: 7.1 Architecture (Standard), 7.2 Code Security (Issues found), 7.3 Access Control (Weak), 7.4 Economic (Neutral), 7.5 Governance (N/A), 7.6 External (N/A), 7.7 Upgrades (N/A), 7.8 Operations (Standard).

> **Final Recommendation:** The development team should immediately address the return value inconsistency in the transfer functions to ensure compatibility with standard DeFi aggregators and wallets. Furthermore, replace all instances of tx.origin with msg.sender to prevent potential cross-contract authorization attacks.

## Category Ratings

| Category | Rating | Risk Level | Notes |
|----------|--------|-----------|-------|
| **Technical** | 6/10 | Medium | The contract utilizes standard OpenZeppelin-like ERC-20 logic for core transfers. The code is clean and follows modern Solidity 0.8.x conventions. However, the implementation of transfer logic fails… |
| **Governance / Economics** | 4/10 | Medium | The token does not implement complex economic mechanisms or governance modules. There are no privileged roles identified in the current codebase. The economic risk is limited to the token's inherent… |
| **Upgrades** | 6/10 | Medium | The contract is not upgradeable. It does not utilize proxy patterns or delegatecall mechanisms. Consequently, there is no risk associated with contract upgrades or administrative logic changes. |

## LP Distribution

| Metric | Value |
|--------|-------|
| **LP Burned** | ✅ 100.0% (≈ permanent lock) |
| **LP Locked** | 100.0% — Dead Address |

## Security Findings

_🟠 1 High · 🟡 1 Medium · ⚪ 6 Informational_

### `CD-01` — Non-Compliant Return Values  *(Severity: High · Status: Unresolved)*

The _transfer, maxWalletLimits, transfer, and transferFrom functions do not correctly handle or return the expected boolean values required by the ERC-20 standard. This can cause external smart contracts that expect a return value to fail or revert when interacting with the token.

**Recommendation:** Ensure all transfer functions explicitly return a boolean 'true' upon successful execution and handle internal logic to conform to the ERC-20 interface specification.


### `CD-02` — Insecure Authorization via tx.origin  *(Severity: Medium · Status: Unresolved)*

The returnTx function uses tx.origin to determine authorization or apply rules. Because tx.origin refers to the original sender of the transaction rather than the immediate caller, it is susceptible to phishing attacks where a malicious contract can trick a user into executing a transaction on their behalf.

**Recommendation:** Refactor the authorization logic to use msg.sender instead of tx.origin to ensure that only the immediate caller is authorized to perform sensitive actions.


### `QA-HOLDERS` — Who holds the supply  *(Severity: Informational · Status: Acknowledged)*

The ten largest holders own 100.0% of supply. What remains: 100.0% in wallets, 0.0% in other contracts. 1 holders in total.

**Recommendation:** Watch the largest wallets that are not exchanges, pools or locks — those are the ones that can move the price.


### `QA-IDENTITY` — Not listed by any independent source  *(Severity: Informational · Status: Acknowledged)*

1 holders. Not listed by CoinGecko or any exchange GoPlus tracks. Nothing independent confirms who is behind this token, so every power its contract grants is scored at face value.

**Recommendation:** Match the contract address against the project's official channels before trading.


### `QA-LIQUIDITY` — Liquidity burned — cannot be withdrawn  *(Severity: Informational · Status: Acknowledged)*

100.0% of the pool's LP is burned or time-locked. 100.0% of the LP tokens were sent to a burn address — that liquidity can never be withdrawn by anyone. Some pools are concentrated-liquidity (V3/V4) positions; shares above are by position as GoPlus reports them.

**Recommendation:** Check the lock's end date and beneficiary on the locker's own page before relying on it.


### `QA-MARKET` — The market for this token  *(Severity: Informational · Status: Acknowledged)*

Liquidity $12K (DexScreener, all pools). 24h trading volume $39K (DexScreener, all pools).

**Recommendation:** Size any position to the liquidity and daily volume shown — they set how much you can sell and at what price.


### `QA-PROFILE` — Asset class: Project token  *(Severity: Informational · Status: Acknowledged)*

A token issued by a project for use, governance or fundraising. Scored on its contract and market facts. The class itself adds no points; the contract and market facts decide the score. Basis: no class-specific evidence. Tokenomics — Supply: fixed — the contract has no mint function. Control: an owner that could not be resolved. Code: not upgradeable (no proxy). Fees: no buy or sell tax. Market: $12K of DEX liquidity across 1 pools. Launch: under a day of market history.

**Recommendation:** Check the project's own documentation for what the token is used for; this report covers what the contract allows.


### `QA-RECENT` — Recently launched — less than a day of market history  *(Severity: Informational · Status: Acknowledged)*

The token's oldest DEX pool is less than a day old. Age is not part of the risk score — a new token is not a risky one by default — but a short history means fewer trades and holder changes behind the facts in this report.

**Recommendation:** Re-check ownership, liquidity and holder distribution as the token matures; those are the facts that move early.

## Token Metrics

| Metric | Value |
|--------|-------|
| **Contract** | [`0x4419...7044`](https://etherscan.io/address/0x4419fd1cf099405b2f33609e5a05c0b28c697044) |
| **Network** | Ethereum |
| **Price** | $0.00002404 |
| **24h Volume** | $39.0K |
| **Liquidity** | $12.5K |
| **Volume / Liquidity** | 3.1× |
| **Token Age** | 1h |
| **Top-10 Holders** | 100.0% of supply |
| **Buy / Sell Tax** | 0.0% / 0.0% |
| **24h Transactions** | 138 buys / 132 sells |

## Security Flags (4/5 passed)

| Check | Status |
|-------|--------|
| Contract Verified | ✅ Pass |
| Ownership Renounced | ⚠️ Unknown |
| No Mint Function | ✅ Pass |
| Liquidity Locked | ✅ Pass |
| Not a Proxy | ✅ Pass |

## Security Flags Detail

| Check | | What it means |
|-------|---|---------------|
| Contract Verified | ✅ | Source code is publicly verified on-chain — logic is auditable. |
| Ownership Renounced | ⚠️ | Could not be determined from the explorer or on-chain reads — treat as unverified rather than safe. |
| No Mint Function | ✅ | No mint function — total supply cannot be inflated. |
| Liquidity Locked | ✅ | Liquidity is locked — reduces the rug-pull risk. |
| Not a Proxy | ✅ | Not a proxy — the implementation cannot be silently swapped. |

## Sources

- [View on DexScreener](https://dexscreener.com/ethereum/0x636577cf3852210864a02b44526bcf1628bc86a564cad8fddcf68257b3993cca)
- [Full AI Report — Quantum Audit](https://quantumaudit.app/token/anakin-skywalker-eth-1056)
- Security data: public on-chain security registries

---
*Generated by [Quantum Audit](https://quantumaudit.app) · AI-powered smart contract security · 2026-11-01*
